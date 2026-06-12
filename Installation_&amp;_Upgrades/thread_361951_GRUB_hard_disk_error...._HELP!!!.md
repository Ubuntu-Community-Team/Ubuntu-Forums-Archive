---
title: "GRUB hard disk error.... HELP!!!"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by NeonShadow on 2007-02-15
I just tried to install Ubuntu 6.10 onto my freshly returned from toshiba laptop (it had mainboard replaced due to design flaws from toshiba, model Qosmio F15-AV201).

I'm still a noob in Linux, but this is my 4th install on 3rd laptop (previous were installed on older versions of Toshiba Satellite) and never had an issue....

Install went ok, no problems there. When I reboot get message "GRUB hard disk error" and computer is unresponsive to anything except rebooting. Current partition setup is this:
sda1 20Gb NTFS
sda2 2Gb swap
sda3 10Gb ext3
sda4 ~42Gb FAT32

This is for a regular live CD (32 bit), 1.8Ghz Centrino (Pentium M) 512 Mb RAM, 80 Gb hard drive....

No clue what went wrong, any ideas would be greatly appreciated. Also, I'm not too attached to the NTFS partition, since it has no data except for clean install of XP on it (from toshiba)... Help! :confused:

---

### Post by NeonShadow on 2007-02-15
Ok, just managed to but up using the live CD, and option boot from frist hard disk.... grub came up fine and ubuntu loaded!!! I'm even more confused, but think that I'm on the right path...

Can anyone help me figure out the correct settings for grub? Please!!!

---

### Post by NeonShadow on 2007-02-15
Found what the error means, but it really doesn't tell me anything:

"Hard Disk Error
    The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed. "

---

### Post by Kateikyoushi on 2007-02-15
Check whether in your bios hard drive is detected and set up correctly.

---

