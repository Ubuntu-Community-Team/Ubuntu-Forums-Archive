---
title: "How to achieve persistant mdadm device names on installation (or otherwise)?"
date: 2022-01-24
forum: Installation &amp; Upgrades
---

### Post by lorewap3 on 2022-01-24
Greetings!

I have a Ubuntu 16.0 server I've kept going for about 13 years now. It's time for an upgrade, so I'm building a new server and installing Ubuntu server 20.04 on it. Its primary purpose is a large samba server with RAID'ed drives and LVM groups for easy swapping. The installation goes off without issue. I setup the mdadm raid and lvm group within the installer under the custom storage layout option. I was hoping to name the mdadm devices this time to be more descriptive than md0, md1, etc. I have a raid for the boot partition I named 'mdboot' and others I named 'mdstore1', 'mdstore2' etc. Those are the ones combined into an logical volume in lvm. 

All I really want to know is how to achieve persistant mdadm names (and to see those same names everywhere). Even though I gave the mdadm devices names during installation, apparently that doesn't carry over to /proc/mdstat, which looks like this:
(I expected to see mdboot, mdstore1, etc here)
```

md123 : active raid1 sdb3[0] sda4[1]
      2147351552 blocks super 1.2 [2/2] [UU]
        resync=DELAYED
      bitmap: 16/16 pages [64KB], 65536KB chunk


md124 : active raid1 sdb4[0] sda5[1]
      1371440128 blocks super 1.2 [2/2] [UU]
        resync=DELAYED
      bitmap: 11/11 pages [44KB], 65536KB chunk


md125 : active raid1 sdb2[0] sda3[1]
      2147351552 blocks super 1.2 [2/2] [UU]
        resync=DELAYED
      bitmap: 16/16 pages [64KB], 65536KB chunk


md126 : active raid1 sda2[1] sdb1[0]
      2147351552 blocks super 1.2 [2/2] [UU]
      [===============>.....]  resync = 78.1% (1677831168/2147351552) finish=38.7min speed=201924K/sec
      bitmap: 4/16 pages [16KB], 65536KB chunk


md127 : active raid1 nvme1n1p1[1] nvme0n1p1[0]
      499907584 blocks super 1.2 [2/2] [UU]
      [===================>.]  resync = 97.5% (487413760/499907584) finish=3.1min speed=65932K/sec
      bitmap: 3/4 pages [12KB], 65536KB chunk

```


df -h:
```

/dev/md127p2                98G  9.8G   84G  11% /
tmpfs                       16G     0   16G   0% /dev/shm
tmpfs                      5.0M     0  5.0M   0% /run/lock
tmpfs                       16G     0   16G   0% /sys/fs/cgroup
/dev/md127p1               9.8G  142M  9.2G   2% /boot
/dev/md127p3               360G  498M  342G   1% /var

```

/etc/mdadm.conf looks like this:
```

ARRAY /dev/md/mdstore1 metadata=1.2 name=ubuntu-server:mdstore1 UUID=fd878a8e:d9d861f1:29a55a57:e01f2d60
ARRAY /dev/md/mdstore2 metadata=1.2 name=ubuntu-server:mdstore2 UUID=c51288c9:b1a1150f:c147ded1:88dfbf82
ARRAY /dev/md/mdstore3 metadata=1.2 name=ubuntu-server:mdstore3 UUID=6b07f823:f02f07b0:a7547089:51be900b
ARRAY /dev/md/mdstoreA metadata=1.2 name=ubuntu-server:mdstoreA UUID=ff2d6fad:83168d23:4fcef297:2c9219a4
ARRAY /dev/md/mdboot metadata=1.2 name=ubuntu-server:mdboot UUID=03130baa:65c64309:c4d5c575:8d68cac4

```


/etc/fstab looks like this:
```

# / was on /dev/md123p2 during curtin installation
/dev/disk/by-id/md-uuid-03130baa:65c64309:c4d5c575:8d68cac4-part2 / ext4 defaults 0 1
# /var was on /dev/md123p3 during curtin installation
/dev/disk/by-id/md-uuid-03130baa:65c64309:c4d5c575:8d68cac4-part3 /var ext4 defaults 0 1
# /home was on /dev/vgsol/lvearth during curtin installation
/dev/disk/by-id/dm-uuid-LVM-Y9P8RFyUGULifaGEkClnwI2cQ91mMeGETJM5mohy5D37wUlCBHeFMp6IXZPGsdB1 /home ext4 defaults 0 1
# /boot was on /dev/md123p1 during curtin installation
/dev/disk/by-id/md-uuid-03130baa:65c64309:c4d5c575:8d68cac4-part1 /boot ext4 defaults 0 1

```


I've honestly wrestled with this problem for probably all 13 years in my old server. I didn't get it figured out fast enough and when it got to the point where there was so much data on there I wasn't going to chance screwing with the RAIDs for something trivial like the names. But I vowed to figure this out when I built my next server. So it surprised me that even on a clean installation, setting up mdadm and lvm exactly as needed during the installation process, and the mdadm names don't stick. At least with my old server they were md0,md1...and not counting down from md127... not to mention they're not even consistent on reboot. So md127 could be a different raid every boot. 

Can anyone give me a clue as to how to get this solved? I'm on a fresh install. I can do whatever is necessary. I'll reinstall 50 times if I have to get these stupid raid device names stable once and for all. 

Thank you!
Will

---

### Post by TheFu on 2022-01-24
I'd just put a LABEL on the file system, then in the fstab mount using the LABEL=XYZ rather than the /dev/...... junk.

Why did you use mdadm AND LVM?  LVM can do all the RAID stuff in a single tool, with many more capabilities. No need for both. Actually, these days, the kewl kids are moving all their storage to ZFS, so RAID and volume management is handled in 1 tool - along with hundreds of other great things.

That fstab is an abomination.  Too bad the installer does that to us.  When I use LVM, for mounting in the fstab, I use /dev/{vgname}/{lvname}. That's much clearer to me and provides useful information.
```
/dev/vgubuntu/home
/dev/vgubuntu/root
/dev/vgubuntu/swap_1
```
Isn't that easier?

In my system with a few mdadm arrays, I'm still using UUID= for mounts. I should switch that over to LABEL= instead.  Give me a second to try it out.
Yep, LABEL= works fine.

Back to your original question - did changing the device name in the /etc/mdadm/mdadm.conf file not work? Looks fairly straight forward.  The manpage for mdadm.conf has a section about this. The *name=* value must match the name stored in the superblock, so that would be important to know. I best there are other caveats.

On one of my really old arrays, I see the name= setting also shows up as the LABEL in other tools (lsblk). I don't know if that's related or coincidental.  I did add a new, different LABEL to 2 arrays using 
```
sudo e2label /dev/md1 "RAID1-Array"
sudo e2label /dev/md2 "R2-Array"
```
then modified the fstab to use those LABELs for the mount device, then rebooted the box.
```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/md2       ext4  1.3T  1.2T   13G  99% /Data/r2
/dev/md1       ext4  1.8T  1.7T  8.7G 100% /raid
```
Worked fine.  This entire system (from 2010) will be retired soon. I'll probably migrate all the data in the system to new storage in another box with a cleaner storage layout.

---

### Post by MAFoElffen on 2022-01-25
MDADM device names change intermittently in /proc/mdstat.In that what is named when you first create, when it actual runs, the it randomly reassigns those names to something else. That has been a problem and mystery for years.

Your fstab correctly sets by UUID, which never changes and is constant. Although not very descriptive.

I just spun up a VM and set to two RAID5 arrays named root and home, from within the Server Install. On running it, in my /etc/mdadm/mdadm.conf file it says /dev/md/root with a name of ubuntu-server:root and /dev/md/home with a name of ubuntu-server:home. Though in /proc/mdsta, they still show up as md126 and md127...

I was going to say that there is way to rename arrays, for when you have to more an array to another server, so there are no name conflicts between the two,  but it is risky. What you do is shut the array down, then assemble it with a different md device name. Anytime you do that, you a slight risk of it failing and not coming back up. Mine worked. 

Here is the UbuntuForums 'system-info' script for it, to show you the detials:
[https://paste.ubuntu.com/p/7jtdZk2mVb/](https://paste.ubuntu.com/p/7jtdZk2mVb/)

---

### Post by lorewap3 on 2022-01-25
> **TheFu said:**
> I'd just put a LABEL on the file system, then in the fstab mount using the LABEL=XYZ rather than the /dev/...... junk.

I'll investigate this. I don't think I've done this before. Is this using e2label? I tried to run it on the boot raid:
```

root@poillion:~# e2label /dev/md127 /dev/mdboot
e2label: Bad magic number in super-block while trying to open /dev/md127
Found a gpt partition table in /dev/md127

```


> **TheFu said:**
> 
Why did you use mdadm AND LVM?  LVM can do all the RAID stuff in a single tool, with many more capabilities. No need for both. Actually, these days, the kewl kids are moving all their storage to ZFS, so RAID and volume management is handled in 1 tool - along with hundreds of other great things.

I didn't know lvm had raid capability. At least I didn't know it did 13 years ago. But regardless I think it's different use cases. My boot raid is only 512gb which is plenty and an LV would be overkill. A mdadm RAID 1 setup works just fine for this. 

The larger storage I'm more flexible, although I'm familiar with mdadm and swapping out failed drives. Not sure it's worth the learning curve to use lvm's redundant system. 

I hadn't heard of ZFS much before, but I'm looking into it. It seems like it'd be great for the large storage. My only hesitation is with the licensing concerns and even Linus himself telling people not to use it. But it seems like it's more mainstream at this point and for a home NAS it should be fine. If you have any guides you'd recommend I'd appreciate it.

> **TheFu said:**
> 
That fstab is an abomination.  Too bad the installer does that to us.  When I use LVM, for mounting in the fstab, I use /dev/{vgname}/{lvname}. That's much clearer to me and provides useful information.
```
/dev/vgubuntu/home
/dev/vgubuntu/root
/dev/vgubuntu/swap_1
```
Isn't that easier?


I'll change out the fstab. You're right that is easier. I just wanted to show what the installer does. I haven't had a problem with auto-mounting the drives though. It's mainly just the inconsistency with the mdadm names and /proc/mdstat

> **TheFu said:**
> 
In my system with a few mdadm arrays, I'm still using UUID= for mounts. I should switch that over to LABEL= instead.  Give me a second to try it out.
Yep, LABEL= works fine.

Back to your original question - did changing the device name in the /etc/mdadm/mdadm.conf file not work? Looks fairly straight forward.  The manpage for mdadm.conf has a section about this. The *name=* value must match the name stored in the superblock, so that would be important to know. I best there are other caveats.


To be clear, all of the code I posted was what was auto-generated by the installer by doing the 'custom storage layout' option. I didn't change the mdadm.conf file at all. 

I'm having to rejog my memory on superblocks. Is there an article or post you can point me to that goes into details about superblocks? I know I've had to 'zero-superblock' before to fix inconsistencies but I don't think I really understood why. 

I think I will likely go with ZFS for my large storage, but still a simple mdadm RAID 1 for the boot drives. That being said, I'm still trying to figure out how to get /proc/mdstat (and lsblk for that matter) to show the mdadm names I gave during setup. Or just any way to rename them at all. I will figure out how to eliminate seeing md127,md126 if it kills me! 

Thanks again!
Will

---

### Post by TheFu on 2022-01-25
I stopped using the installer to setup storage a few years ago, unless it was encrypted.  It was just too sad for me otherwise. During an install, I'll install ssh from another tty and pull over my script, make a few changes to create the partitions of the correct type and size, then put everything else under LVM on the boot HDD/SSD.  I only work with 1 storage device during boot.  Next I'll create the LVs I want, sized smaller than I'll need in a year, but since adding storage to an LV from the VG pool is trivial (5 seconds) and removing storage from an LV is hard (boot into an other OS first), I want to add space to LVs only for 3-6 months of use. It is amazing how little is actually needed.

LVM RAID code was stolen from the mdadm base.  It just provides all the LVM tools like pvmove and lvconvert and vgextend to make management 100x easier.  We're all comfortable with what we know and kept good notes around. That's human nature, but sometimes it actually causes us to do things a harder way than necessary.

ZFS is only for data storage, in my book, at this time.  All the complaints about it are really old.
At least you aren't suggesting btrfs for any RAID use. Good job. BTRFS is good for single disk situations only - think laptop. There are a few not-great failure modes when used with RAID that mdadm or LVM-RAID or ZFS avoid completely.

> **lorewap3 said:**
>  
I'll change out the fstab. You're right that is easier. I just wanted to show what the installer does. I haven't had a problem with auto-mounting the drives though. It's mainly just the inconsistency with the mdadm names and /proc/mdstat
 
It won't kill you, but it can make for a very bad day.  The mapper service handles most of the stuff for aliases of storage under /dev/.  It does this using symbolic links, but the real device names are outside our control for a number of reasons.  Our needs aren't the only ones of concern here.  There are hundreds, if not thousands, of other software that has expectations around the names of devices.  We are free to use any of those symbolic links, but don't expect /dev/md{whatever} to really change and not use 'md' as the beginning of the name.  It may be required to have md{numbers} for some software to properly see the arrays, then look more closely.  IDK.

When you break your system over this, which I think is likely, please ensure you have backups of everything needed to put it back.  As usual, we don't know what we don't know. Even if the mdadm code works, think of all the other tools that won't.

---

### Post by MAFoElffen on 2022-01-26
Both TheFU and I have said... there is always the risk, that trying to rename (any time you reassemble), have good backups.

Here is how to rename a mdadm array. 

Assumption #1, is that the Array you want to rename does not have root on it. If it is, then get the info first, then shutdown the server, boot from a LiveCD, install mdadm into the LiveCD Environment... Then deal with that array while it is offline.

For this example, rename /dev/md1 to /dev/home
```

sudo mdadm --detail /dev/md1

```
Note the first line where it says 'Version', the UUID, and the devices members. The current version for Ubuntu 20.04.3 is v1.2.

If Version 0.90, then this is only valid for v0.90 metadata.That is the only version where the --super-minor flag is valid.
```

sudo mdadm --uuid=8c229b6a:c20a3bfa:2d164f4f:84bee133 --update=super-minor --assemble /dev/home

```
When it is through, backup and update your mdadm.conf file
```

sudo cp -v /etc/mdadm/mdadm.{conf,bak-jan-25-2022}
sudo mdadm -Es > /etc/mdadm/mdadm.conf

```
There is another way, but the above is safer(using UUID)...  
```

sudo mdadm --assemble /dev/md/home --name=home --update=name /dev/sdb2 /de/sdc2

```

---

