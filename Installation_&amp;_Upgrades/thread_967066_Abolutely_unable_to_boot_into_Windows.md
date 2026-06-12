---
title: "Abolutely unable to boot into Windows"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by cedrickinnard on 2008-11-01
Hello All
pardon me in advance if I missed an easy solution to this but I can't find any.
I have Ubuntu 8.10 installed on /dev/sdb1, linux swap on /dev/sdb2, and after installing Ubuntu I installed Win XP 64 on /dev/sdb3
/dev/sda1 contains 2 NTFS partitions with files, so does /dev/sdc1

I tried many many solutions but I'm never able to load in windows.
Here is my fdisk and menu.lst

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23277c7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   143362047    71680000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       143362048   234436607    45537280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda4   *           0           0           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x660583b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   244139804   122069871   83  Linux
/dev/sdb2       244139805   248043599     1951897+  82  Linux swap / Solaris
/dev/sdb3   *   248043600   488375999   120166200    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4001fff4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   234437792   117218865    7  HPFS/NTFS


MENU.LST
title      Ubuntu 8.10 x64
uuid      485e3351-d510-4aa4-af0a-0547ed161f16
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=485e3351-d510-4aa4-af0a-0547ed161f16 ro quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic
quiet

title      Ubuntu 8.10 x64 (recovery mode)
uuid      485e3351-d510-4aa4-af0a-0547ed161f16
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=485e3351-d510-4aa4-af0a-0547ed161f16 ro  single
initrd      /boot/initrd.img-2.6.27-7-generic

title      Ubuntu 8.10, memtest86+
uuid      485e3351-d510-4aa4-af0a-0547ed161f16
kernel      /boot/memtest86+.bin
quiet

title      Microsoft Windows XP Professional x64
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify            (hd0,2)
makeactive
chainloader     +1
boot

Now I'm fully aware of the last entry probably not being correct, it is only my last try at something I had read... I tried the map (hd0)(hd1) and vice versa and it does not work. I tried all combinations of (hd#,#) and it never works, but anyway when I try all that in the boot process, I can see that hd0 is the correct one; it's the only which has 3 partitions.
So when I choose hd0,2, and choose windows in grub boot menu, nothing happens. When I try other combinations, I get error22 (partitions not existing)


Now to SuperGrubdisk for those who know it : when I choose windows / advanced / boot windows partition and I manually choose /dev/sdb3, I am able to load in windows! But I do not know now how to take advantage of that and modify my system to have a normal dual boot without supergrub...

Normal boot files are presend on sdb3 for windows (ntldr, boot.ini, ndetect)

I'm out of ideas, and I'm a noob at grub and LInux but I want to succeed in my transition to Linux.
Thanks in advance!

---

### Post by Pumalite on 2008-11-01
Looks like a Partition Table problem. Fix it with TestDisk:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by caljohnsmith on 2008-11-01
First we need to know which (hdX,Y) Ubuntu uses to boot, because we don't know which drive has Grub in the MBR (Master Boot Record). So how about when you get the Grub menu on start up, press "c" to get the command line, and then do:
```
grub> find /boot/grub/stage1
```
That will probably return (hd1,0) or maybe (hd2,0), but let me know exactly what it returns; we can use that information to know how to boot your Windows properly.

---

