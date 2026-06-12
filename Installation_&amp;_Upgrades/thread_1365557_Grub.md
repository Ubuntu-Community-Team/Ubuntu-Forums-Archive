---
title: "Grub"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by SBS Jackboy2 on 2009-12-27
My Dell Lat Lap has been taken over by GRUB. I used the entire disk to install 9.04, but realized later I wanted xp so I could run VBox etc.. So the problem is Windows should have been installed first, and even worse my laptop will not recognize any of my xp boot disks when it boots or when I try to open them in Ubuntu. Also My wine apps that I really need do not work well at all. The audio exe's I use should be much smoother.
                How can I stop GRUB without the use of an Xp fxmbr or fdisk way. Then I can Put Xp back and run its superior Ubuntu.  I wonder why if one software is so great and another is not then why neither of them cannot understand and speak the others language. A New Distro Is COMING!

---

### Post by oldfred on 2009-12-27
While it is easier to install windows first it is not absolutely required. You need to create the NTFS partition first with gparted and put the boot flag on it. Windows will not see your ext3 partitions. You will still have to reinstall grub as there is no way to install windows without it overwriting the MBR.

You may have to adjust you BIOS to boot CD first if you cannot select boot device as part of startup.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

---

