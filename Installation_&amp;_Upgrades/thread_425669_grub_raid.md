---
title: "grub raid"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by eier on 2007-04-27
i've recently innstalled ubuntu feisty on a computer with windows.
the machine has 3 hdd two of them are raid.
in ubuntu i cant find the raid disk's so i cant make grub load windows only ubuntu.
anyone know how to set up so i can dual boot?

---

### Post by psusi on 2007-04-27
If you have a sata fake hardware raid, you should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

Does fdisk -l show the two disks in the raid?

---

### Post by eier on 2007-04-28
here's my fdisk:

root@petter-desktop:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       29186   193478827+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/hda5               2       37608   302078196    7  HPFS/NTFS
/dev/hda6           37609       37735     1020096   82  Linux swap / Solaris
/dev/hda7           37736       38913     9462253+  83  Linux


sdb is probably the raid disk, but i dont know what it's called in grub:(

---

### Post by psusi on 2007-04-30
According to that, you have 4 hard drives, but you said you only have 3.  Which is it?  

I am guessing that the 320 gig drive with only one partition ( sda ) is where your windows is installed.  Because you have an ide drive as well that shows up as hda, grub treats that as hd0, and sda as hd1.  Which disk do you have the bios configured to boot from?

---

### Post by eier on 2007-05-01
i have 4 hdd's,forgot about the last one.
i've tried to boot windows with grub as (hd0,0) (hd1,0) ,hd2,0) and (hd3,0)
but with no luck.

---

### Post by psusi on 2007-05-02
Could you be more specific about what goes wrong, and what your menu.lst looks like?  To boot windows it should be chainload (hd2,0)

---

