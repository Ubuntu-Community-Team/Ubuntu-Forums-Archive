---
title: "Problem booting in to  Ubuntu 8.0.4"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by hempar on 2008-05-01
I'm new to linux. i have installed ubuntu 8.0.4 on my computer using live cd. Now after booting to GRUB manu when i select Ubuntu i see Ubuntu logo and bar moving but nothing happens after that. after couple minute i get message  as follow:

ata6.00 exception Emask 0x0 SAct 0x0x Serr 0x0 action 0x2 frozen
ata6.00 Cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in Status:{DRDY}

My System configuration is as follow

Brand : Home Build
MOBO : Abit IP35 PRO
CPU : C2D E4500
Memory : HP 4gb
Video Card : ATI Radeon HD 2600 XT
CDROM : Samsung DVD-RW
Hard Drive : WD 400 GB 
             55 GB - NTFS ( Windows XP )
             18 GB - EXT3 ( Ubuntu 8.04)
             2  GB - Swap
             320 GB - NTFS ( Storage )

When i boot to Windows XP from GRUB it is working fine.

---

### Post by fbroce on 2008-05-01
You have to tweek the kernel to boot with 4gb of ram on most systems. The video system uses some of the memory in the area 3-4gb. Try this..

add mem=3328M as a grub boot option. If that works..When you finish your install,
add this to the grub menu in /boot/grub or install lilo and add it to lilo.conf as an append statement:

This option will allow you to see all 4gb memory if you add it to the grub menu (as below)
iommu=65534,noagp,soft (this option should let you see 4gb memory with a 64 bit systems. You also have to enable memory hole remapping in the bios).
------------------------------------------------------
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b-b22a-cdcee67f502f ro quiet splash iommu=65534,noagp,soft
initrd          /boot/initrd.img-2.6.24-16-generic
quiet
---------------------------------------------------------

or if your satisfied with 3gb memory use the mem=3328M option.


Hope this helps.

Fred B.

---

