---
title: "Partition help"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by Chris Cromer on 2005-11-04
Alright I am getting a new computer and decided I would like to install a few OS's on it rather than just 2.

From what I have heard your basic IDE/ATA hard drive can only have 3 primary partitions? Does this mean I am restriced to 3 OS's? Or for example could I have 1st primary partition be windows xp media center, then the 2nd primary be "/boot" which would use grub. Then would I be able to use extended partitions to house multiple linux OS's? For instance I want to install Breezy, Dapper, Gentoo, and a few other OS's. Then would I be able to setup grub from the 2nd primary to be able to boot all of these OS's? If not it's fine, but at least I want to have windows xp, ubuntu, and gentoo installed those would be my OS's of choice.

---

### Post by aysiu on 2005-11-04
I quadruple-boot right now--three Linuxes, one Windows--all from one hard drive.

---

### Post by Chris Cromer on 2005-11-04
Does this mean that what I am talking about in my post would work?

Or is there some other way to do it? As example how did you do it?

---

### Post by aysiu on 2005-11-04
You could *set up* Grub from your second primary partition, but in order for Grub to work properly, it should be *installed* on the Master Boot Record (MBR). How did I get it to work? Well, considering I've installed and reinstalled many Linux distros over my existing partitions, it depends.

The easiest way to do it is this:

If you have Windows, install that first.
Install all the Linux distros that you **don't** want to be your primary distros (i.e., not the one in charge of the Grub setup).
Then, install the last Linux distro and put that distro's Grub on the MBR.

Linux distros tend to recognize other OSes (other distros and Windows) and automatically add them as Grub entries--Ubuntu in particular is good at doing this.

---

### Post by Chris Cromer on 2005-11-04
Ubuntu breezy badger is going to be my primary linux os. So it would properly detect all the other OS's when I install grub from Ubuntu? Gentoo, SUSE, and Ubuntu dapper drake are the ones I plan to install from the start, I might add others later.

---

### Post by aysiu on 2005-11-04
My general experience with Ubuntu is that it's good at detecting other OSes and adding them to the Grub menu. If they don't get added automatically, you can also add them manually, but let's deal with that if/when it comes up.

---

### Post by Chris Cromer on 2005-11-04
Well, now just to get the new system. I can't wait to try out the 64 bit version of Ubuntu since my new system will have the AMD 64 bit processor.

And don't worry I know how to manually add entries to the grub menu already. I have customized my grub in a few different ways. I just wanted to be sure they would all work and not conflict.

---

### Post by SilentCacophony on 2005-11-04
Hi. Technically, you can have as many primary partitions as you like, providing your firm/hardware can handle it, and you use the right partition manager (Ranish PM can do that.)

The catch is that you may only reference a total of four partitions from the partition table at the end of the MBR, so under normal circumstances you are limited to four. Most people would have no need for more, anyway. ;)

More on-topic: I'll give you an idea of one way to set such a partition scheme up, I'll show you my setup:

```
brian@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         722     3293325   83  Linux
/dev/hda3             723        1338     4948020   83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)

```

On the first HD, I have enough partitions for four linux distros and one windows (on the first partition.) AFAIK, there should be no problem with installing linux into an extended partition. I use one swap partition between distros.

Note that hda4 (the fourth and last 'primary' partion) is labeled 'extended', because it contains all of the extended partitions (hda5-7.) Extended partitions are always counted as hdx5 and above in linux, even if you only have one primary partition.

As *aysiu* pointed out, when installing multiple distros, you may have to get creative with grub. One thing to consider: the last one that you installed grub to the MBR with will be the one that has the menu.lst that matters.

---

