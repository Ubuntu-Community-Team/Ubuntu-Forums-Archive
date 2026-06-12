---
title: "Grub/ vista bootload fixing"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Magic Spoon on 2008-04-27
I currently have, Vista installed on one hard drive and Ubuntu installed on an external drive. Also the external drive contains a common storage partition.

Vista was allready installed. I then installed ubuntu (7.10) from the live cd. This worked well but grub was installed to the mbr and on the external drive. Meaning I cannot boot without the external drive in place. This is no good so I booted back into windows and fixed the vista bootloader. I can now boot into vista but not ubuntu. I tried using easyBCD to add ubuntu to the vista bootloader menu. This semed to work but when i tried to boot into it it failed.

I need to set things up so that I can boot into vista when the external drive is not in place, and choose to boot into ubuntu when it is. Preferably using the vista bootloader but grub will do. Also please note that I cannot create any more partitions on my internal disk.

Help please.

---

### Post by Pumalite on 2008-04-27
Post:
sudo fdisk -l

---

### Post by Magic Spoon on 2008-04-27
as posted from ubuntu live cd:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd657135c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       19034    69493760    7  HPFS/NTFS
/dev/sda4           19034       19458     3398656   17  Hidden HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008db49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       57402   461081533+   7  HPFS/NTFS
/dev/sdb2           57403       60044    21221865   83  Linux
/dev/sdb3           60045       60801     6080602+   5  Extended
/dev/sdb5           60045       60801     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by Magic Spoon on 2008-04-27
I managed to sort this out.

Turns out easyBCD definitely was the way to do it, I just didn't know how to use it properly. The documentation on their site explains how to do it very simply. 

Basically i just had to use neogrub, copy the entries I wanted from /boot/grub/menu.lst into the neogrub menu.lst and it worked perfectly. There is also a better way to do it by fixing grub on the linux partition, but it is simpler just to get around that problem using neogrub.

---

### Post by Pumalite on 2008-04-27
Congrats.

---

