---
title: "zfs-fuse gone crazy, won't export, won't destroy pool"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by mrluohua on 2013-01-05
tl;dr zfs-fuse wont export nor destory my pool claiming 'busy', even when it's disks are used by mdadm raid!

So I had 4x3tb drives that I created a raidz pool on it for some temporary testing.  When done, I was unable to export or destroy my pool

# zpool export -f rstoreb1
cannot export 'rstoreb1': pool is busy
# zpool destroy -f rstoreb1
cannot destroy 'rstoreb1': pool is busy

I can find nothing using it with lsof -n nor with ps -ef nor with fuser.

At this point I'm annoyed, and stop it with /etc/init.d/zfs-fuse stop

I partition the 4x3tb drives with parted, and create my raid with mdadm, and then create filesystem with mkfs.ext4, and mounted,

At this point mdadm is creating the raid, the new raid is mounted and I can copy files to it just fine.

I do a final reboot to make sure everything boots well and mounts well ... and low and behold ... zfs-fuse starts with boot, and mounts rstoreb1 again !

/dev/md127      7.9T  1.7G  7.9T   1% /extra/mdstore2
rstoreb1        8.1T  8.0T   89G  99% /extra/rstoreb1

these two raids are using the same hard drives !!

zpool stays it's healthy (i copied a 1gb file to the md127 raid device that shares the same disks with zfs raidz)

 # zpool status
  pool: rstoreb1
 state: ONLINE
 scrub: resilver completed after 0h0m with 0 errors on Sat Jan  5 17:55:15 2013
config:

        NAME                                            STATE     READ WRITE CKSUM
        rstoreb1                                        ONLINE       0     0     0
          raidz1-0                                      ONLINE       0     0     0
            disk/by-id/wwn-0x5000c5004e5454fe           ONLINE       0     0     0
            disk/by-id/ata-ST3000DM001-1CH166_Z1F16Q3S  ONLINE       0     0     0  10K resilvered
            disk/by-id/ata-ST3000DM001-1CH166_Z1F16QB0  ONLINE       0     0     0
            disk/by-id/ata-ST3000DM001-1CH166_Z1F16QDX  ONLINE       0     0     0

errors: No known data errors

at this point I am confused.  I like fuse-zfs and I want to (need to) continue using it with my external e-sata drives but this internal set of disks I want mdadm, and zfs just won't let go.

How can I coax zfs to nicely let go of this volume?

# dpkg -l | grep zfs
ii  zfs-fuse                              0.6.9-1build1                         ZFS on FUSE

I'm running Ubuntu 12.04.1 LTS.

note: I had uninstalled nfs-kernel-server at one point, and reading that it might be necessary I just reinstalled it (didn't start it), but I still can't destroy or export pool rstoreb1.

Any ideas?  Thanks so much !!

mrluohua

edit: change zfs-kernel-server to nfs-kernel-server.  There is no zfs-kernel-server, I typo'd it.  I meant nfs.

---

### Post by tgalati4 on 2013-01-05
How much RAM do you have?

```
free
```

Bad things happen in zfs when you are low on RAM.

---

### Post by mrluohua on 2013-01-05
about 1gb free

[FONT=Courier New]# free -m
             total       used       free     shared    buffers     cached
Mem:          4026       3040        986          0        103       2522
-/+ buffers/cache:        413       3613
Swap:         1906          0       1906

[/FONT]edit: formatting

---

### Post by mrluohua on 2013-01-05
I should add that I've rebooted 2x and stopped/started zfs-fuse multiple times.

---

### Post by tgalati4 on 2013-01-05
I have zfs running on my freenas home server, and I recall reading that you need 1 GB per TB of disk space.  You have 12 TB running on a 4 GB machine.  Perhaps you should monitor the RAM to see what is going on.

Also, uninstalling and reinstalling a zfs-enabled kernel AND expecting your pools to continue to exist is expecting a lot.  ZFS was developed under BSD.  It has some neat features (like being 128-bit, which means HUGE file system sizes).  I don't know how stable zfs is under linux.  

It sounds like zfs has striped your internal drives, which might require a wipe to remove the striping to get zfs to release them.  It's also possible that a bad interaction with mdadm and zfs on the same devices caused a partition table problem.  The data is still there and the RAID is intact, but the pool architecture is messed up in a nontrivial way.

Running the system with and without the zfs kernel may have contributed to the problem.  I don't know what else to say.  Proceed carefully.

---

### Post by mrluohua on 2013-01-06
> **tgalati4 said:**
> Running the system with and without the zfs kernel may have contributed to the problem.  I don't know what else to say.  Proceed carefully.

Sorry, I had a horrible typo, which I just corrected in my main post.  I removed the "nfs-kernel-server" package... nfs, not zfs.  

I read in some post somewhere that the zfs-fuse made use of the nfs-kernel-server which is why I re-installed it.

As an aside, the 4 x 3tb raidz 'temp' setup worked great for about 2 weeks.  I was moving data around and I filled it all the way up, swapped hardware, and then moved my data back. Worked wonderfully.

It almost seems like a bug with the specific version of zfs that I have.  All I want to do is export/destroy it.  Why does it say 'busy'?  ps / lsof / fuser tell me that it's not busy.  Just confusing.

Anyway, thanks for your advice !!

---

### Post by tgalati4 on 2013-01-06
I think it says busy because it is trying the read and understand the zfs partitioning scheme and it is messed up in a nontrivial way.  nfs-kernel-server is a support package for the NFS (network file system) an older, unix-based network file sharing protocol--before SAMBA and Windows sharing.

According to:

tgalati4@Dell600m-mint14 ~ $ apt-cache depends zfs-fuse
zfs-fuse
  Depends: libaio1
  Depends: libc6
  Depends: libfuse2
  Depends: libssl1.0.0
  Depends: zlib1g
  Depends: fuse
  Depends: lsb-base
  Suggests: nfs-kernel-server
  Suggests: kpartx

It's not a required package, just a suggested one, probably to allow you to share a zfs pool over NFS. So removing that package should not effect the operation of zfs pools.

So to summarize:

1. You built and operated a 12 TB zfs pool and moved data around at it seemed to function OK for 2 weeks.  Hardware is probably OK.

2.  You were finished playing around with zfs so you decided to use the same drives for software RAID pool using mdadm.  You repartitioned them (wiped them) and created ext4 partitions and formatted them with mkfs.ext4.  You used parted, which I believe has no support for zfs (at least gparted doesn't have support in 12.10).  So there may be remnants of the zfs pool striping on the drives that zfs can read, but parted did not erase.

3.  ZFS detects the striping of the drives, or a configuration file and is trying to read them resulting in busy.  Mdadm shows the current RAID with ext4.

I'm not familiar with the zfs-fuse package, but from the name, I assume that this is a user-space zfs mount tool that allows users to make and mount zfs pools.  Because it is user-space and not kernel-space, there are probably configuration files stored somewhere, like ~/.zfs perhaps?  Try finding and deleting those configuration files.  There might be files in /etc/zfs.

Try removing the zfs-fuse package.  If you are not going to use zfs, then remove it.  This assumes that you have no other zfs pools that you need access to.

```
sudo apt-get remove zfs-fuse
sudo apt-get purge zfs-fuse
```

The second one removes configuration files as well as removes the package.

---

### Post by mrluohua on 2013-01-07
@[tgalati4]("http://ubuntuforums.org/member.php?u=241895") thanks so much for the ideas.

Indeed, repartitioning and doing a newfs did not overlap where zfs writes it's metadata.  The only real problem here is with ZFS and the inability to 'export' something, claiming it's busy, even when it is most certainly not busy.  (many reboots, restarts, etc, fuser/lsof/etc).  After reading, I think it's an issue/bug with the version of zfs I'm using.

[aside] Unfortunately I still use zfs with external esata.   Archiving media off to dvd-r became too slow and too small, so I started getting cheap 500gb HD and creating external (esata) raidz (raid5) using zfs.  1.5tb useable.  When it was filled, I'd catalog it, label the drives (raidset01, raidset02, etc) and put them on the shelf and get 4 new drives.  Zfs works amazing well for this. [/aside]

What I finally did was
* stop zfs daemon
* using dd, overwrite first 10mb and last 10mb of the disk (if=/dev/zero, etc)
* start zfs daemon; no metadata signature, no problem.
* re-partition, re-init mdadm raid, re-newfs, all good

So I learned some stuff in the process and I'm back in action.    

Thanks again everyone fot the help!!

MrLuoHua

---

### Post by tgalati4 on 2013-01-07
Excellent.  Since parted does not (yet) have zfs support, it has no way of knowing how to handle it.  Wiping the front and back of the drive is a brute force way to do it, but hey, if it works, then more power to you.  

Normally RAID is not used as a backup scheme, but you managed to find a way.  It would be helpful for you to document your experiences to those who maintain the parted source code.  A simple algorithm to read the ZFS striping and a warning to the user before overwriting would be helpful.  This would help others avoid a similar problem in the future.  Gparted has a nice table of file system support, but zfs is not included and needs to be.

---

