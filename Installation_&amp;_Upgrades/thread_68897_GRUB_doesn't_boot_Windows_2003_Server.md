---
title: "GRUB doesn't boot Windows 2003 Server"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by monosaccharide on 2005-09-24
[font=Tahoma]So here is my story: 
 I did a nice install of WinXP and 2003 Server. No problem dualbooting...I installed Ubuntu. No problem. Everything worked fine. One day, I realized I had 2 partitions of free space on 2 disks, so I decided to just create FAT32 partitions w/ Acronis Disk Director (I didn't know how to deal w/ partitioning stuff in Linux). 
Anyway, I created those partitions, and rebooted. GRUB didn't work. Error 27 or something. Tried reinstalling grub w/ stuff I found online (chrooting, etc..). No luck. I decided to get my 2003 Server CD and did a recovery console FIXBOOT and FIXMBR.
Everything worked...GRUB was gone. So I decided to just reinstall Ubuntu. Which I did...install went fine. No problems. However, unlike the first time I installed Ubuntu --this time the Server 2003 Installation was not detected. It only lists Windows XP as the other operating system, and boots it just fine. But I am unable to boot Windows 2003 Server. 
I tried editing the GRUB boot line for Windows XP (which read "root (hd0,0)"), so that it could boot up 2003 (changed to "root (hd1,0)") --but this did not work. Said something about device not being found...
   I'm sure it could be the case that the partition was wrong, who knows.

Any help would be GREATLY appreciated.
BTW: I got 2 HDs --an SATA and an IDE. WinXP is on the IDE drive (/dev/hda) and Ubuntu and Windows 2003 are both on the SATA Drive (/dev/sda)

Do I need to change my menu.lst or something? Plz tell me what I need to change it to. I really need to get my work done. 

Also ---how can I enable SSH tunneling?

Thanks. Here is my fdisk -l and menu.lst, respectively:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        9726    78116062+   f  W95 Ext'd (LBA)
/dev/sda5               2        5306    42612381    7  HPFS/NTFS
/dev/sda6            5307        6913    12908196    b  W95 FAT32
/dev/sda7            6914        7175     2104483+  83  Linux
/dev/sda8            7176        7437     2104483+  83  Linux
/dev/sda9            7438        7699     2104483+  83  Linux
/dev/sda10           7700        8026     2626596   83  Linux
/dev/sda11           8027        8811     6305481   83  Linux
/dev/sda12           8812        9595     6297448+  83  Linux
/dev/sda13           9596        9726     1052226   82  Linux swap / Solaris

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5483    44042166    7  HPFS/NTFS
/dev/hda2            5484        7476    16008772+   5  Extended
/dev/hda5            5484        7345    14956483+   7  HPFS/NTFS
/dev/hda6            7346        7476     1052226   82  Linux swap / Solaris

-------------------------------

title           Ubuntu, kernel 2.6.10-5-k7
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-k7
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.10-5-k7
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
savedefault
boot



Thanks in advance.


[/font]

---

