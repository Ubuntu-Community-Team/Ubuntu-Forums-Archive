---
title: "Triple Boot (initramfs) error"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by sheit on 2008-11-06
Current system was running Windows XP dual booted with Mandriva, using Grub for the dual boot system. Then went ahead and disconnected that hardrive and installed ubuntu onto another drive.  My goal wasnt to triple boot but now those plans have changed as my girlfriend likes ubuntu over mandriva.

anyway... 

I coppied from the menu.lst file on the ubuntu drive and placed that into the mandriva menu.lst file with a few changes, (hd1,0).  I can get windows and mandriva to work but not ubuntu.. I can however get the "memtest" from ubuntu to run.

I get an error on the "root-UUID" line.. If I remove that line i get it to start to boot and stop at the initramfs error.

Menu.lst

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=4e368210-f67c-4b95-8e1a-5de60e7280e0 resume=UUID=8174fcef-ff83-448b-a88d-dd0616d04d7a splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=4e368210-f67c-4b95-8e1a-5de60e7280e0 resume=UUID=8174fcef-ff83-448b-a88d-dd0616d04d7a
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=4e368210-f67c-4b95-8e1a-5de60e7280e0 failsafe
initrd (hd0,4)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd1,0)
uuid		a1323b48-c169-4d3b-8448-a238221f4648
kernel		(hd1,0)/boot/vmlinuz-2.6.27-7-generic 
root=UUID=a1323b48-c169-4d3b-8448-a238221f4648 ro xforcevesa quiet 
splash 
initrd		(hd1,0)/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd1,0)
uuid		a1323b48-c169-4d3b-8448-a238221f4648
kernel		(hd1,0)boot/vmlinuz-2.6.27-7-generic 
root=UUID=a1323b48-c169-4d3b-8448-a238221f4648 ro xforcevesa  single
initrd		(hd1,0)/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a1323b48-c169-4d3b-8448-a238221f4648
kernel		(hd1,0)/boot/memtest86+.bin
quiet

---

### Post by sheit on 2008-11-06
Also here is the device.map

(hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by sheit on 2008-11-06
[root@localhost /]# fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aa2fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            5100        7476    19093252+   5  Extended
/dev/sda5            5100        6118     8185086   83  Linux
/dev/sda6            6119        6460     2747083+  82  Linux swap / Solaris
/dev/sda7            6461        7476     8160988+  83  Linux

Disk /dev/sdb: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ffacf26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2132    17125258+  83  Linux
/dev/sdb2            2133        2231      795217+   5  Extended
/dev/sdb5            2133        2231      795186   82  Linux swap / Solaris
[root@localhost /]#

---

