---
title: "Installer automatically going to wrong hard drive"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by Darkslime on 2010-04-18
Hey all. I'm running into a weird problem when trying to install from the live CD I'm running. Basically, I have two hard drives: sda, a 160GB HDD which has Windows 7 on it, and is the one I would like to put kubuntu on; and sdb, which is a plain 500GB NTFS file system I keep all my personal stuff on.

When I get to 'disk setup' and choose 'install side-by-side', it defaults to sdb instead of sda and I can't change it. I've created a 20GB partition on sda, which is where I want to put kubuntu, but it still defaults to sdb. I also can't figure out how to install to where I want using the advanced partitioning menu.

Can anyone help me out? I've installed ubuntu before, but not with a second hard drive. :/

---

### Post by Bucky Ball on 2010-04-18
Are you selecting 'manual partitioning' during the install and pointing to the sda that way?

---

### Post by Darkslime on 2010-04-18
Yeah, I did go there. Under sda, it has the three partitions:

dev/sda1 (the Win7 partition)
dev/sda2 (the boot partition)
free space

So I click on free space and go to "add", and choose primary, ext4 file system, and leave the mount location blank(I'm not sure what that is). Once that's done, I click on the new sda3 partition and hit "next", but it gives me an error message saying that the root filesystem isn't defined.

---

### Post by tommcd on 2010-04-18
You should choose manual partitioning for this.
You will install Kubuntu to /dev/sdaX, where X represents the 20GB partition you have created on /dev/sda for Kubuntu. Choose "yes" to format this partition, choose ext4 as the file system, and choose the mount point as root /.
Ideally, you should have a separate home partition. You can leave home on the 20GB root partition though if you have no space for a separate home partition. Since you will share data between Windows and Ubuntu from you /dev/sdb NTFS drive, the home directory on /dev/sdaX will not take up much space.
Personally, I would convert /dev/sdb to ext3 or ext4 instead of NTFS, and forget about sharing the data with Windows. But it is your choice.
NOTE that formatting /dev/sdb would erase all data on it, so be sure all important data is backed up first.

---

