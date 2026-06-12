---
title: "Kubuntu killed my other *buntus"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by DFreeze on 2007-10-27
I installed Kubuntu 7.10 yesterday and now no other buntu wants to load! I have Ubuntu 7.10, UbuntuStudio 7.04 and WinXP installed. Now, only Windows and Kubuntu work, and UbuntuStudio gives some error. Ubuntu Gutsy just blanks out indefinately (I have the bug of no USplash, but Ubuntu never gets back from that black screen).

How do I fix this?

---

### Post by kellemes on 2007-10-27
Well, can you please explain where all those OS's are installed and how/where you have setup your bootloader?

sudo fdisk -l (gives your partitions)
And as far as you know.. give us more info what's on every partition.
And try to figure out from which *buntu you're managing Grub (probably Kubuntu), and post the relevant /boot/grub/menu.lst

---

### Post by louieb on 2007-10-27
Gutsy killed Feisty on my desktop. When Gutsy installed it changed the UUID of the swap and its install partition.Use **ls -l /dev/disk/by-uuid/** to list. Check /etc/fstab and fix as needed.

---

### Post by DFreeze on 2007-10-28
These are my fdisk listings (I put the OS or contents between brackets):

```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa87fa87

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10240000+   7  HPFS/NTFS (WindowsXP)
/dev/hda2            1276       12161    87441795    5  Extended
/dev/hda5            1276        2549    10233373+  83  Linux (PCLinuxOS)
/dev/hda6            2550        2731     1461883+  82  Linux swap / Solaris
/dev/hda7            7299       12161    39062016    b  W95 FAT32 (documents disk)
/dev/hda8            2732        3947     9767488+  83  Linux (Kubuntu 7.10)
/dev/hda9            3948        5163     9767488+  83  Linux (UbuntuStudio 7.04)
/dev/hda10           5164        6379     9767488+  83  Linux (Ubuntu 7.10)

```

And here's how my Grub menu.lst looks:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2e3f50c2-6043-4a96-9a2d-7781746afaea ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2e3f50c2-6043-4a96-9a2d-7781746afaea ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda10.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3dd1227-4497-4b01-b49e-1277cb3f3f1c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda10.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3dd1227-4497-4b01-b49e-1277cb3f3f1c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda10.
title		Ubuntu 7.10, memtest86+ (on /dev/hda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		linux (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda5 acpi=on resume=/dev/hda6 splash=silent vga=788 
initrd		(hd0,4)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		linux-nonfb (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hda5 acpi=on resume=/dev/hda6 
initrd		(hd0,4)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		failsafe (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hda5 failsafe acpi=on resume=/dev/hda6 
initrd		(hd0,4)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-16-lowlatency (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-16-lowlatency (recovery mode) (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro single 
initrd		/boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-16-generic (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-15-lowlatency (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-15-lowlatency (recovery mode) (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro single 
initrd		/boot/initrd.img-2.6.20-15-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-15-generic (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=05f887df-f004-454b-9cf7-7b9e18d7afc8 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		Ubuntu, memtest86+ (on /dev/hda9)
root		(hd0,8)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

