---
title: "Grub will not load after Ghost restore"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Jorin on 2008-05-20
Hi, I thought I was doing myself a favour by backing up my Ubuntu 8.04 partition with Ghost, but it looks like I might have just killed my installation when I restored the image.

Before the image started restoring I saw a message saying "creating Ext2 filesystem." The problem is my Ubuntu partition was Ext3, not Ext2. I think the version of Ghost I was using was too old. :(

When I tried to load Ubuntu I got a Grub error that just displayed "GRUB" at the top of the screen with a cursor.

I'm wondering if there's any way I can get Ubuntu to boot or whether I'm starting from scratch.

Many thanks for the help!

---

### Post by ThaDiggler on 2008-05-20
Not sure if this will work but you may want to try to restore your grub boot loader with a super grub cd.  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by VMC on 2008-05-20
How did you clone ubuntu using Ghost? All still may not be lost.
Maybe the ext2 was another partition and you did a disk clone.

In other words, you had a ext3 partition for ubuntu, a swap partition and another partition ext3. If you have Windows installed you can view the files with Ghost Explorer.

---

### Post by Jorin on 2008-05-22
Thanks for the replies! I checked out the grub boot disc but I haven't had time to play with it enough to see if I can fix the bootloader.

The good news is that the files are all still there. I can see them in XP after installing Ext2 drivers. If I can fix the bootloader that's perfect, but I figure I also have the option now to backup the files again in a more suitable way and copy some stuff over to a fresh Ubuntu installation to preserve the programs, drivers and settings -never tried that before though.

I'm still confused as to what happened with Grub. I'm using the Windows bootloader in my MBR, which points to an ubuntu.bin file on my windows partition, which then apparently points to Grub which I specified to be installed to the Ubuntu partition itself. Perhaps there was some information in the boot sector of my Ubuntu partition that wasn't included by ghost and got wiped out?

I backed up my partition with Ghost by using a bootable disc. It always worked fine with XP and Vista so I thought it would cover Ubuntu as well.

I really appreciate the help! This is at least an interesting learning experience. :D

---

