---
title: "XP Boot Problem"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by doughboy334 on 2008-01-21
Hi everyone I'm new to Ubuntu and tonight I decided to give it a go. It seems that I've run into a little problem however. Ubuntu works fine and I'm able to boot into it from the dual boot screen, but when I tried to boot into Windows XP, I got to the loading animation screen and then my computer restarted. I tried running XP in safe mode, but the same thing happened. My hard drive is partitioned into two drives, and I can mount the D drive in Unbuntu but I get an error when I tried to get into C. Any tips on how to fix booting into Windows without a reformat? Thanks!

---

### Post by banewman on 2008-01-21
Can you tell us the error pls ?

---

### Post by c0met on 2008-01-21
Did you install Ubuntu after having Windows installed?

---

### Post by doughboy334 on 2008-01-21
> **banewman said:**
> Can you tell us the error pls ?

The error is I'm able to go to XP through the startup menu, but it doesn't load and crashes at the XP animation screen.

> **c0met said:**
> Did you install Ubuntu after having Windows installed?

Yea I had XP first and then I installed Ubuntu.

---

### Post by c0met on 2008-01-22
My experience is that if Ubuntu is installed on top of a Windows installation, Ubuntu sorts out the booting. It's unusual that this didn't happen for you. Did you install Ubuntu on it's own partition?

---

### Post by doughboy334 on 2008-01-22
> **c0met said:**
> My experience is that if Ubuntu is installed on top of a Windows installation, Ubuntu sorts out the booting. It's unusual that this didn't happen for you. Did you install Ubuntu on it's own partition?

When I installed it, the option I chose at the Prepare Disk Menu was "Resize the main partition and use free space." I followed this guide to install.

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by sandysandy on 2008-01-22
> **doughboy334 said:**
> When I installed it, the option I chose at the Prepare Disk Menu was "Resize the main partition and use free space." I followed this guide to install.

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

Please post output of

[COLOR="Red"]sudo fdisk -lu[/COLOR]  from the terminal.

regards

---

### Post by c0met on 2008-01-22
I found that guide very useful when I installed Ubuntu, too. Can I ask, did you follow the "Configure GRUB" section? If you did, this could well be where you got into trouble.

You might want to surf to the following page, download the bootable version of a little program called "SuperGRUB" (ISO), burn it onto CD and then boot from it. After booting, you'll be presented with text-based menus that can be used to restore Linux and Windows. This program doesn't always work, but it's worth a try.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

[B][COLOR="Red"]IF SUPEGRUB DOESN'T WORK...
[/COLOR][/B]
Go to the complementary page of the one that you followed at...

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

About 1/3 of the way down the page, you'll find instructions on "Reinstalling GRUB to MBR". From what you say, it seems like this is what you need to do. SuperGRUB should do it, but it if doesn't, these instructions will allow you do it manually.

---

### Post by doughboy334 on 2008-01-26
> **sandysandy said:**
> Please post output of

[COLOR="Red"]sudo fdisk -lu[/COLOR]  from the terminal.

regards

sorry for the long wait. I was at the dorms and didn't get back till this weekend.

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06d306d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   251883134   125941536    7  HPFS/NTFS
/dev/sda2       369896625   586067264   108085320    f  W95 Ext'd (LBA)
/dev/sda3       251883135   369896624    59006745   83  Linux
/dev/sda5       375021423   586067264   105522921    7  HPFS/NTFS
/dev/sda6       369896751   375021359     2562304+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by doughboy334 on 2008-01-27
> **c0met said:**
> I found that guide very useful when I installed Ubuntu, too. Can I ask, did you follow the "Configure GRUB" section? If you did, this could well be where you got into trouble.

You might want to surf to the following page, download the bootable version of a little program called "SuperGRUB" (ISO), burn it onto CD and then boot from it. After booting, you'll be presented with text-based menus that can be used to restore Linux and Windows. This program doesn't always work, but it's worth a try.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

[B][COLOR="Red"]IF SUPEGRUB DOESN'T WORK...
[/COLOR][/B]
Go to the complementary page of the one that you followed at...

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

About 1/3 of the way down the page, you'll find instructions on "Reinstalling GRUB to MBR". From what you say, it seems like this is what you need to do. SuperGRUB should do it, but it if doesn't, these instructions will allow you do it manually.

Supergrub didn't work, and i'm not too experienced in terminal yet so i'll try the second method later. any other useful suggestions? :D

---

### Post by doughboy334 on 2008-01-29
bump:)

---

