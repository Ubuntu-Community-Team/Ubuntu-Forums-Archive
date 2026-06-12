---
title: "Windows 7 ALERT! /dev/disk/by-uuid/e9... does not exist."
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by edarnell on 2010-03-05
Fun and games trying to install ubuntu (64bit) on a new Windows 7 (64bit) laptop (ASUS X5DIJ series).
 
As shipped the laptop comes with three partitions. The first is small and I think is just for recovery (GPART says it is Vista). The second has Windows 7. The third is a large (200GB) NTFS data partition.
 
I shrank the NTFS partition to 100G within Windows to free up 100G for Ubuntu.
 
Install all goes fine but grub can't then boot linux (it can boot windows 7 fine).
 
Grub menu is as follows:
 
GNU Grub version 1.97~beta4
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
 
When I try to boot ubuntu I get the following:
 
Begin: Waiting for root file system... ...
Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/e9263e1f-9f86-4209-b25c-0ee3a8b49c45 does not exist.
 
 
Grub looks to be having trouble mounting the new ext4 partition (which is a bit odd given that I think it runs it's config from it).
 
I'll send some more detail from the box itself when I reboot linux from a usb.

---

### Post by edarnell on 2010-03-05
RESULTS attached from running boot_info_script055.sh

RESULTS had /dev/sda6 mounted (sudo mount -t ext4 /dev/sda6 /mnt)
RESULTS1 does not (so I guess shows the problem grub has).

I have also attached a screenshot from GParted, and the grub.cfg file.

The problem looks to be /dev/disk/by-uuid

$ ls /dev/disk/by-uuid
1A57-3E1C  548CE6D58CE6B0A2  d198f8da-1340-4420-be4c-05f9f4cd155d
3C98-AC5D  80EA01CA7CF62578

The uuid grub is looking for doesn't exist even though /dev/sda6 looks to be fine.

Is there a way to create it - or to change the grub.cfg to not need it and use sda6 instead?

---

### Post by stlsaint on 2010-03-05
Are you able to set the mount point (flag) via the livecd in gparted?

---

### Post by edarnell on 2010-03-05
Which is the mount point flag?

Flags I look to be able to set in Gparted are:

boot,hidden,lba,lvm,palo,prep,raid

None are currently set for this partition (or the swap partition ubuntu created). The wap partition does look to have a uuid entry though. See output from ls -l below:

ubuntu$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2010-03-05 18:42 1A57-3E1C -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-03-05 18:42 3C98-AC5D -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-03-05 18:42 548CE6D58CE6B0A2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-03-05 18:42 80EA01CA7CF62578 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-03-05 18:42 d198f8da-1340-4420-be4c-05f9f4cd155d -> ../../sda7

---

### Post by krapp on 2010-03-05
I also have a new Asus laptop (N61 series) with Windows 7 (with the same 3 partitions) on which I will attempt later tonight to install Ubuntu as my second OS. I'm following this discussion with interest, and will post later if I encounter similar difficulties.

---

### Post by wilee-nilee on 2010-03-05
The last supergrub 1.3 now includes grub2.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by edarnell on 2010-03-05
... so a few other things to be aware of (not sure it will be true of your model of ASUS too).

Booting off the ubuntu CD was a challenge as the laptop just wanted to always dive straight into the windows 7 boot manager - whatever I did to try to get to the BIOS.

I found in the end that ESC during boot let me select which device to boot from.

You can also get to the BIOS (I think F2 but may be F1).

Once you have it installed be careful of the Vista (recovery boot). I did that rather than Windows 7 once and it trashed Grub. Removing the partitions and reinstalling ubuntu generally got grub working again though.

[http://ubuntuforums.org/showthread.php?t=813090](http://ubuntuforums.org/showthread.php?t=813090) looks relevant with respect to the problems I am now seeing. I'll take a look at fstab.

---

### Post by stlsaint on 2010-03-05
Sorry i cant be of further use but here is what i suggest: (all this should be doable from the livecd) just select your hdd from the Places menu to mount them onto desktop.
1) BACKUP YOUR FSTAB
```
cp /etc/fstab /etc/fstab.bak
```
2)  Enter fstab config:
```
nano /etc/fstab 
```
Find the entry /dev/disk (the one from the error) and replace /dev/disk/by-uuid with your linux partition (i think its /dev/sda6 for you...double check gparted to make sure.
3) Save then update and reboot system. 
PS...fstab is where all automatic mounting is configured.

Here a few links with people who had the same issue and solved it:

[http://ubuntuforums.org/archive/index.php/t-1319976.html](http://ubuntuforums.org/archive/index.php/t-1319976.html)
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090)

---

### Post by Choragos on 2010-03-05
Are you required to partition the hard drive first or will the installer walk you through it and do it for you?

---

### Post by edarnell on 2010-03-05
Interesting.

I can get ubuntu to boot by manually editing the boot command (e while in grub) if I edit the root=UUID=e926... line to read:

linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda6 ro quiet plash

I also edited fstab but I'm not sure if that was needed. Once everything boots the expected UUID value then exists. I'll try putting the UUID version of fstab back to see.

I suspect there is a bug in whatever grub2 is using to mount disks. The UUID entry doesn't exist when it is trying to use it but it does exist later. I saw a developer to developer thread which looked related but can't find it again to post here.

... yes all works fine if I put fstab back to using the UUID. .... so it is just grub2 which has a problem.

I'll do a little more testing tomorrow to see if I can pinpoint the bug. In the meantime everything is working (so this post is from ubuntu booted from the hard disk - albeit with a manual edit of the grub boot parameters).

---

### Post by edarnell on 2010-03-05
Forcing grub2 to boot via the normal device (/dev/sda6) looks to have solved the problem.

It now boots fine even via the UUID device name. Presumably booting once fixed some problem (or initialised something) with the fresh ext4 file system.

Not sure if any ubuntu developers lurk here. I suspect this is all reproducible if I delete everything and re-install (but I'd need to do soon before I start using the fresh install for real).

---

### Post by stlsaint on 2010-03-05
This is not something that happens ALL the time on every install. Just a slight adjustment happened somewhere during install. But im glad i could be of help. Please mark thread as solved.

---

### Post by meierfra. on 2010-03-07
> Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/e9263e1f-9f86-4209-b25c-0ee3a8b49c45 does not exist.

> /dev/sda6: ambivalent result (probably more filesystems on the device)
> Presumably booting once fixed some problem (or initialised something) with the fresh ext4 file system.


Sounds like you have been hit by this bug:
[http://bugs.launchpad.net/ubuntu/+bug/518582](http://bugs.launchpad.net/ubuntu/+bug/518582)

---

