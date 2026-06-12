---
title: "4 primary partitions limitation"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by albertkao on 2010-04-30
My hard disk has windows 7 and kubuntu 9.04 installed.
The disk still has 1 unallocated partition.
How do I install another linux (fedora 12)?
I cannot install to the unallocated partition because hard disk can only have 4 primary partitions. The extended also counts as primary, so it can only have 3 primary partitions.
If I cannot install on this hard disk, may I install another linux (fedora 12) on an 200GB external USB disk to make the computer triple boot?

The partition layout is as follows:
```
$ sudo fdisk -l
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7fbbb3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14336000   27  Unknown
/dev/sda2   *        1785        1798      102400    7  HPFS/NTFS
/dev/sda3            1798       40634   311950680    7  HPFS/NTFS
/dev/sda4           40635       53510   103426470    5  Extended
/dev/sda5           40635       41132     4000153+  82  Linux swap / Solaris
/dev/sda6           41133       51078    79891213+  83  Linux
/dev/sda7           51079       53510    19535008+  83  Linux

$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda7 on /home type ext3 (rw)
/dev/sda2 on /media/SYSTEM RESERVED type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

---

### Post by Chronon on 2010-04-30
/dev/sda4 is not unallocated if that's what you're talking about.  It is a physical (extended) partition containing a set of logical partitions.  If you look at the sectors you will see that /dev/sda4 encompasses /dev/sda5, /dev/sda6 and /dev/sda7.

In order to install Fedora you would need to add more logical partitions.

What is /dev/sda1?  Can you install Fedora to that?

---

### Post by slvr42 on 2010-04-30
Yeah you can only have 4 primary partitions and I think that has to do with the whole MBR standard thing.  If you want more than four use logical partitions.  This allows you to get around the 4 limit.

---

### Post by albertkao on 2010-05-01
Running GParted in kubuntu indicates that the disk has a 186GB unallocated "partition" after /dev/sda7.  However, selecting that unallocated space and clicking the "New" button results in a "4 primary partitions limit" error.
Selecting the /dev/sda4 extended partition and clicking the "Partition" menu result in a popup menu which has the "New" menu being active, the other menus such as "Resize/Move" are unactive, so I cannot use GParted to enlarge the extended partition.
Please help.
Thanks.

---

### Post by spandey on 2010-05-01
I was having similar problem. Then I went to my windows and installed free partition tool [http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm), which allowed me to extend my extended partition to unallocated space.

---

### Post by srs5694 on 2010-05-01
Your extended partition runs from cylinder 40635 to cylinder 53510, but the disk ends at cylinder 77825. Thus, the unallocated space after /dev/sda7 falls outside of the extended partition. You may allocate it in either of two ways:


[list=1]
[*]Create a new primary partition in this space. Exercising this option would, however, require deleting one of your three existing primary partitions (or absorbing at least one into the extended partition, which is a complicated process). Presumably you don't want to do this, so this really isn't a viable option. I mention it only for completeness.
[*]Expand the extended partition (/dev/sda4) so that it ends at cylinder 77825, then create one or more new logical partition(s) within the larger extended partition.
[/list]


To do #2 with GParted, you must click the extended partition and then select the resize option. This will only be possible if none of the current logical partitions are in use, though, so you'll need to boot an emergency disc to do the job -- or perhaps the Fedora installer can do this (I don't recall enough about the Fedora installer to know for sure what it can do in this respect).

---

### Post by albertkao on 2010-05-01
> **srs5694 said:**
> Your extended partition runs from cylinder 40635 to cylinder 53510, but the disk ends at cylinder 77825. Thus, the unallocated space after /dev/sda7 falls outside of the extended partition. You may allocate it in either of two ways:


[LIST=1]
[*]Create a new primary partition in this space. Exercising this option would, however, require deleting one of your three existing primary partitions (or absorbing at least one into the extended partition, which is a complicated process). Presumably you don't want to do this, so this really isn't a viable option. I mention it only for completeness.
[*]Expand the extended partition (/dev/sda4) so that it ends at cylinder 77825, then create one or more new logical partition(s) within the larger extended partition.
[/LIST]


To do #2 with GParted, you must click the extended partition and then select the resize option. This will only be possible if none of the current logical partitions are in use, though, so you'll need to boot an emergency disc to do the job -- or perhaps the Fedora installer can do this (I don't recall enough about the Fedora installer to know for sure what it can do in this respect).

Following your advice, I use gparted from sysrescuecd to maximize the size of the extended (sda4) primary partition which have room to add logical drives for other distributions.
The fedora 12 installation program keep the existing partitions and suggest these new partitions:
```
/dev/sda8           /boot       ext4                      199MB    
/dev/sda9                       physical volume (LVM)   67000MB 
```
Are they ok or should I do this:
- a single logical partition for / should be simplest. i.e. no need for LVM and /boot partition
- no need to install the Fedora boot loader and keep the existing linux boot loader

---

### Post by srs5694 on 2010-05-02
It's interesting that Fedora is recommending an LVM configuration. (Personally, I like LVM, although my memory was that Fedora's installer made using LVM more complex than it could have been.) LVM has advantages and disadvantages over using partitions directly. On the plus side, it makes adding, deleting, and resizing volumes much easier than is the case when you use partitions directly, which can help simplify future Linux installations. On the down side, it's an added layer of complexity, and Ubuntu makes installing to an LVM a real pain. (I just did such an install. After I set it up and loaded the lvm2 package in the installer, the installer loaded files into the LVM just fine, but then it was stupid enough to *not* install the lvm2 package in the main installation, so the system wouldn't boot! That's a real Homer Simpson "d'oh!" moment.)

Personally, I'd go for the LVM configuration and then plan on moving other partitions over to LVM form in the future (say, with the next Ubuntu upgrade). Note that your current /home partition is 19GB, if I'm reading your output correctly, but your free space is more like 200GB, and Fedora wants to allocate 67GB to an LVM. Thus, you *could* create a 67-200GB LVM partition, move /home into the LVM, add the /home to the LVM space (or re-allocate it for a non-Linux OS, if you prefer), and have lots of flexibility for resizing /home for both distributions. I'm comfortable with LVM, though. If you're not, using partitions directly may make more sense.

In either case, I personally would re-use /home (whether you leave it where it is or move it into an LVM). Note that Fedora, the last I checked, numbered UIDs starting with 500 by default, whereas Ubuntu starts with 1000. Between this and the fact that configuration files may differ, you're better off using different usernames in the two distributions, or at least changing the default home directory in one so they don't both try to use the same user home directory (e.g., /home/albertkao or whatever you use) in both distributions.

As for boot loaders, you should decide where you want to maintain it: Ubuntu or Fedora. It's possible to chain-load from one to another if you put one in a boot partition vs. in the MBR, so you might consider doing that rather than omitting it entirely from the Fedora installation. That might even come in handy down the road.

---

