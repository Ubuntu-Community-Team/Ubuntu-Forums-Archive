---
title: "[SOLVED] unusual installation problem"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by nick2535 on 2008-08-08
i need help on a unusual installation
i resently bought a newer motherboard however their is a problem with dual booting unfortunately uninstalling windows is not an option because my schools software requires windows and does not work in wine 
anyway the bios does not support dual boot on the same hard drive or diffent hard drives for that matter it only allows dual boot with one of the operating systems on a removable device and for some reason the bios does not think a external hard drive is a removable device. i know you can mount devices as a folder so can i mount a usb device to hold just the files to get it to start the boot then boot the rest from a hard drive if so what filder do i have to mount it to and how much space does it take up 
or do i need to break down and buy a usb flash drive that is large enough to install everything to
i would preffer to use my ancient 128MB flash drive if possible or if the files are too large i have a newer 1GB one

if you want to avoid these problems avoid motherboards that have Intel bios
:confused:

---

### Post by spiderbatdad on 2008-08-08
I am not familiar with dual booting needing to be supported by the system BIOS. boot files are stored in linux in the root file system. initial ram disk initramfs handles access to the boot files. Have you tried to install Ubuntu and failed, or is this speculation?

---

### Post by nick2535 on 2008-08-09
yes for some strange reason the bios does not allow more than one operating system to be listed in GRUB it does not 
because of this i have trouble installing ubuntu
i have tried mounting a flash drive as /boot but it would not work i think it might be easier to buy a 4gb flash drive and just install on that 
it it had a message error can not edit GRUB this is a fatal error on both a separate partition and a completely separate hard drive it installed the files on a external hard drive and was successful the boot order in my bios is CD,USB,HDD the bios recognizes my USB external hard drive as a internal hard drive if it would recognize it as a USB storage device i would already be enjoying ububtu

---

### Post by sandysandy on 2008-08-09
kindly post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by zipperback on 2008-08-09
> **nick2535 said:**
> yes for some strange reason the bios does not allow more than one operating system to be listed in GRUB it does not 
because of this i have trouble installing ubuntu

You are incorrect in your view of what the bios can and cannot do with Grub.

The bios **does not** and **cannot** control what the grub loader sees in it's configuration file.

The bios controls the system as the lowest base hardware level and fully is independent of any grub configuration file and therefore has no ability to control what grub is allows have in its configuration.

- zipperback

---

### Post by nick2535 on 2008-08-11
i would like to add that in my BIOS i have to select the hard drive that is choses to boot from and their is no way to select 2 hard drives so my BIOS automatically loads the harddrive with windows on it i tryed installing ubuntu on a partition but it has an error "can not edit GRUB this is a fatal error and the installation quits

also it may take me awhile to relpy and test replys because i do not have much free time do work on this

---

### Post by nick2535 on 2008-08-11
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa64569a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    17575109     8787523+   b  W95 FAT32
/dev/sda2        17575110    19535039      979965   82  Linux swap / Solaris

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06a906a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     8080694     4040316    7  HPFS/NTFS
/dev/sdb2         8080695    16498754     4209030    c  W95 FAT32 (LBA)

Disk /dev/sde: 1030 MB, 1030225920 bytes
64 heads, 32 sectors/track, 982 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x701013b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          51     2012159     1006054+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 20)
Partition 1 has different physical/logical endings:
     phys=(982, 63, 32) logical=(982, 31, 32)

---

### Post by nick2535 on 2008-08-22
I was finally able to get ubuntu to install

---

