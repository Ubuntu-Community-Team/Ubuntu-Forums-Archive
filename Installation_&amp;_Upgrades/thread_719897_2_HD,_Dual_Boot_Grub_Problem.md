---
title: "2 HD, Dual Boot Grub Problem"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by jseiser on 2008-03-09
Linux is installed on sda, windows is on sdb, i can boot linux from grub fine, when i try to boot windows, i get error 15, file not found, if i use the bios, and just boot to that drive, windows works fine.  here is my disk result, and my grub file, i tried to put these together from this website, and google.

[root@beast justin]# fdisk -l

Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39473947

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40162   83  Linux
/dev/sda2               6          38      265072+  82  Linux swap / Solaris
/dev/sda3              39         995     7687102+  83  Linux
/dev/sda4             996       30401   236203695   83  Linux

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x562c2a8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS
--------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26-fallback.img

# (1) Windows
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
----
do i need to make windows the master, reinstall on the slave drive, and install grub to the windwos drive?  Is there any options, any help would be awesome.

---

### Post by Pumalite on 2008-03-09
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by jseiser on 2008-03-19
that tutorial is for dual booting on one drive, as you can see that isnt the issue, i can handle dual booting on the same drive.  The issu is getting windows to boot properly as the slave

---

### Post by Herman on 2008-03-19
I can't see any mistake in your arch linux's /boot/grub/menu.lst file.

GRUB's chainloader command should boot Windows by it's boot sector.
Try a couple of experiments to see if it's some problem with Windows's boot sector or a problem with GRUB.

One experiment would be to boot the second hard disk by that hard disk's MBR instead of the partition's boot sector, like this,
```
root               (hd1)
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
``` I'm not sure how that will work, it would work if you were booting another Linux and GRUB or LiLo, or GAG Boot Manager was installed in the second hard disk's MBR, but I'm not sure if Windows will boot that way, but it's worth a try to see what happens. 

Try using [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") for experimenting with, that's what GRUB's Command Line Interface is for. GRUB is the only boot loader that has a CLI, and it's one of the great advantages of using GRUB. GRUB's CLI might give some feedback that will be helpful in diagnosing the problem.
You should be able to type in exactly the same commands as you have in your /boot/grub/menu.lst file with the addition of the command : boot (at the end), and your operating system should boot.
You can omit the title and savedefault commands.
```
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
boot
```Try with 'rootnoverify' and see if that helps maybe.
```
rootnoverify  (hd1,0)
 makeactive
 map                (hd0) (hd1)
 map                (hd1) (hd0)
 chainloader        +1
boot
```If nothing here works, try booting up with [Super Grub Disk]("http://sgd.benjamin-butschko.de/") or some other GRUB to see if a different GRUB can do it. 

Regards, Herman :)

---

