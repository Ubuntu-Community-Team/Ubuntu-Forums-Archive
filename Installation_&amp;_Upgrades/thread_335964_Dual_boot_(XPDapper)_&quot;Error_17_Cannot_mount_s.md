---
title: "Dual boot (XP/Dapper) &quot;Error 17: Cannot mount selected partition&quot;"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by flexible on 2007-01-11
Dear forum,

I recently installed Ubuntu Dapper Drake (Linux kernel 2.6.15-26-386) using Live CD as a Dual Boot with windows XP.

Hard Drives are:

hda1 (NTFS, Win XP boot)
hda5 (FAT)
hda6 (FAT)
hda7 (Linux Swap)
hda8(Linux Ext 3)


After installation, as i felt size of my new Ubuntu swap was very low (2GB), using 'norton partition magic' in win XP, i made some changes to the windows drive hda6. What i did was, made a new partition and formatting it in linux swap. I used partition magic, because i thought if i partition my windows (FAT) hard drives using GParted (GNU Partition Editor), all data will be lost.

Now,i tried to log into Ubuntu in GRUB. The following error message appears:




> booting 'ubuntu, kernel 2.6.15-26-386/root (hd0,7)

Filesystem type unknown, partition type 0x82

kernel /boot/umlinuz-2.6.15-26-386 root=/dev/hda8 ro quet splash

Error 17: cannot mount selected partition

press any key to continue...

when i press any key, it take me back to GRUB.
I also tried to log-in to the ubuntu recovery consol, but same error happens. I could login to XP,no problems.

Could anyone kind enough to advise me what to do? I am very new to linux.

Cheers

---

### Post by meng on 2007-01-11
2GB is not small for a swap partition. It's probably too much!
Try reinstalling grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

