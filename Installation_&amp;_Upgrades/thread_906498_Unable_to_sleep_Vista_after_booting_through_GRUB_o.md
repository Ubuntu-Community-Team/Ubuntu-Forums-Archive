---
title: "Unable to sleep Vista after booting through GRUB on Linux HDD"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by VvWolverinevV on 2008-08-31
I have two HDDs - one with Windows Vista x86-64 and one with Linux. I recently setup GRUB on the Linux HDD's MBR. This allows me to choose the operating system I want to boot when the BIOS calls the Linux HDD MBR. However, when I boot to Windows in this way, sleep does not work properly (it simply locks my session - almost as if something like a USB device were waking the computer immediately after it tries to sleep).

When the BIOS calls the Windows HDD MBR, however, sleep works just fine.

Other possibly useful information: I used to have GRUB on the Windows HDD, and in that case, sleep also worked fine. So it seems to be a problem with actually booting through the secondary HDD MBR.  Could reinstallation of GRUB on the Linux HDD have messed up some hard drive numbering such that the BIOS would have trouble sleeping?

Does anyone know what's going on here? :confused:

---

### Post by cmat on 2008-08-31
I think you need Windows' boot loader to load sleep images.

---

### Post by VvWolverinevV on 2008-08-31
GRUB calls the Windows boot loader, does it not?

---

### Post by VvWolverinevV on 2008-09-01
*Bump*

---

### Post by manishtech on 2008-09-02
> **VvWolverinevV said:**
> GRUB calls the Windows boot loader, does it not?
Yeah! That's called chainloading..


> Could reinstallation of GRUB on the Linux HDD have messed up some hard drive numbering such that the BIOS would have trouble sleeping?
If you think so., then attach both the hard disks and post the output of the command

```
sudo fdisk -l
```

---

### Post by VvWolverinevV on 2008-09-02
> **manishtech said:**
> Yeah! That's called chainloading..



If you think so., then attach both the hard disks and post the output of the command

```
sudo fdisk -l
```

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x034cead4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       41345   312568168+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13d9c4e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096523

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59323   476511966   83  Linux
/dev/sdc2           59324       60801    11872035    5  Extended
/dev/sdc5           59324       60801    11872003+  82  Linux swap / Solaris
```
sda=storage, sdb=Windows, sdc=Ubuntu

... which is weird because I had to set up /boot/grub/menu.lst to call Ubuntu on hd0(=sda, according to /boot/grub/device.map) and Windows on hd1(=sdb)...

---

### Post by VvWolverinevV on 2008-09-03
*Bump*

---

