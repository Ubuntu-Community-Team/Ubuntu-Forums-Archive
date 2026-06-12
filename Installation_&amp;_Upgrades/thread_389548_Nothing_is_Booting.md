---
title: "Nothing is Booting"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Pinka on 2007-03-20
I recently installed Ubuntu and restarted my computer.  As soon as I restarted, instead of getting the Grub menu as expected, I get some sort of Grub 0.97 Shell which only takes commands, but I can't get it to do much.

More Information:
I installed Grub to hd0 (the default option during installation)
I have a FAT32 physical drive which is just file storage at /media/hda1

I have another physical drive which already had Windows XP in it and to which I installed Ubuntu.  This drive is /media/sda1.  My windows partition is the first primary partition.  While partitioning during the installation, I put the swap on the second partition and the ext3 file system as partition 3.  Both of these other two partition  were set as Primary Partitions.

When I try the 'boot' command in the grub shell, I get Error 8, saying that the kernel must be loaded before booting.

How should this be resolved, any help would by wonderful.

---

### Post by KingCharles on 2007-03-21
well, the very first thing I would advise you to do, is load your Live Ubuntu CD and check the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). It can help you out tracking down what could be wrong.

If you installed from an alternative CD, or directly from an FTP, then I advise you to get another machine that is online, and download [SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), as it is a booting image that helps fix grub on your hard drive(s). Check out the page. There are both CD and floppy images.

---

