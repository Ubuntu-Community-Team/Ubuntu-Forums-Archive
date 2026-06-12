---
title: "Install Windows XP after Feisty . . ."
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by subzero_acj on 2007-07-05
[B]hi guys....

this is my sudo fdisk -l output >>
[/B]
[I]Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1367    10980396   83  Linux
/dev/hda2            1368        7301    47664855    5  Extended
/dev/hda5            1368        1460      746991   82  Linux swap / Solaris
/dev/hda6            1461        2920    11727418+   b  W95 FAT32
/dev/hda7            2921        4380    11727418+   b  W95 FAT32
/dev/hda8            4381        5840    11727418+   b  W95 FAT32
/dev/hda9            5841        7301    11735451    b  W95 FAT32[/I]

[B]
i wud like to install windows xp in my [SIZE="5"]hda6[/SIZE] drive. but that overwrites my grub rgt ?
pls explain me what to do...

pls explain in detail... i am a Ubuntu noob... Really !!:D[/B]

---

### Post by jimbren on 2007-07-05
Life is a lot easier when you have an installation of XP *first,* and you install Ubuntu second.  This is because your XP installation will overwrite grub, and then you'll have to get it back.  This is possible, but it is a pain in the *** that I've enver actually done before, so I can't speak to it.  

I would consider backing up whatever you need from /home, doing a fresh installation of XP that overwrites your Ubuntu installation, and then reinstall Ubuntu.  This is a pain in the *** too, but I think it is less of a pain than trying to install XP after Ubuntu and retain both installations.

Also, using this method you'll have the opportunity to put /home on it's own partition, which has great benefits.  Backups are easier to set up, upgrades\reinstallations of Ubuntu are easier to do.  I'm kind of surprised that a /home partition isn't part of the default installation scheme, or at least an option.  

Anyway, this probably isn't much help.  

You might also want to check out this link for more information.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

This page is a wealth of information that I refer back to pretty often.

Thanks,

jimbo

---

