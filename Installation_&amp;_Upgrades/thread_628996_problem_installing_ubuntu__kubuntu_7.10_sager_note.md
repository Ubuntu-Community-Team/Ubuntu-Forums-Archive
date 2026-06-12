---
title: "problem installing ubuntu / kubuntu 7.10 sager notebook np7260"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by egoldtech on 2007-12-01
We have two identical laptops, sagernotebooks np7260, they have dualcore, 2gb ram, sis672 video card, and hdd sata 7200 rpm/200gb. (really good laptops) bought with no OS.
when installing  ubuntu and kubuntu 7.10 we have a hanged installation so we tryed the vga safe with debbugin :
=casper xforcevesa inittrd=/casper/inittrd.gz -- debug


the installtion stops randomly between:
[ 3.508000] ohci_hcd 0000:00:03.0 irq 17, io mem 0xd41040000
...
...
...
[ 3.640000] SCSI subsystem initialized


they both have already a partition with windows xp sp2 already installed.

any clue ?
thks in advance

---

### Post by egoldtech on 2007-12-03
Also we have tried to install
Ubuntu/Kubuntu/  6.10 
at firts we have some video  problems  but using this commmand on boot
fb=false video=vga16:off  
systems boots up with LIVE cd with no problem .
but  there is no way to "see" the SATA drive 200gb ,  we tried gnome partition, disk mang,
and also after run
> sudo fdisk -l
we get zero(0)  lines . no disks.  so live cd works good on 6.10, surf internet wireless, etc perfect, but i cannot install .
---------------------------------------------------
with Ubuntu Gutsy, we get the system frozen 
we have several options on boot options:
ram=512 BOOT_DEBUG=2   debian-installer/probe/usb=false  
and nothing still frezzen  in the same time .
---------------
in the BIOS there are no many options, on the SATA Port area, w ehave tried everything .

but we dont have a this time idea hot to continue the debuging to find the problem .

---

