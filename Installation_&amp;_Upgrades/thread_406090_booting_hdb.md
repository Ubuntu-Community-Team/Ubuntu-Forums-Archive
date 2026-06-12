---
title: "booting hdb"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by mquinteiro on 2007-04-10
Hi!

I have and installation over hdb. I can't change from slave to master.

when I have hda (CD as master) connected (without disk) It book perfect, but if I disconnect (fisically) hda the sistem do not boot with message DISK BOOT FAILURE , INSERT DISK AND PRESS ENTER.

some help? I do not know what to do.

thanks!

---

### Post by john_spiral on 2007-04-10
does your BIOS see your hard discs?

---

### Post by mquinteiro on 2007-04-11
yes. 

when CD is plug

Primary Master: CD-ROM
Primary Slave: Trascend......

when cd is unplug

Primary Master: NONE
Primary Slave: Trascend......

---

### Post by bulldog on 2007-04-11
Why would you disconnect the CD-player?
Let it run as it is with both devices connected,and it will run fine as you stated.

---

### Post by mquinteiro on 2007-04-11
Cos I have no money for an CD unit... :)

The system is a black box with out units, no cd, no disk only one compact flash.

I have used de CD only to install, and now i want to remove it.

---

### Post by bulldog on 2007-04-11
I think you have to open the box and connect the hdd to the master IDE port.
Also take a look at the jumpers at the back of the hdd,to see if there are any jumpers which you have to re-order to make it a master hdd.

---

### Post by mquinteiro on 2007-04-11
No jumpers... ok it have some similar to jumper, in fact if you want to change master to slave you have to change 2 smd resistors, but it is not the way....

I sopouse that the problem is something in grub... but i don't know how to solve

---

### Post by mquinteiro on 2007-04-11
few more info..

Originaly I have

my old menu.lst is like this (with out commnets)
 
 default 0
 serial
 terminal --timeout=12 serial console
 hiddenmenu
 
 timeout 3
 title Ubuntu, kernel 2.6.15-23-386
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
 initrd /boot/initrd.img-2.6.15-23-386
 savedefault
 boot
 
 title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
 initrd /boot/initrd.img-2.6.15-23-386
 boot
 
 title Ubuntu, memtest86+
 root (hd0,0)
 kernel /boot/memtest86+.bin
 boot
 
 
I have tried with this other and the same... 

my old menu.lst is like this (with out commnets)
 
 default 0
 serial
 terminal --timeout=12 serial console
 hiddenmenu
 
 timeout 3
 title Ubuntu, kernel 2.6.15-23-386
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
 initrd /boot/initrd.img-2.6.15-23-386
 savedefault
 boot
 
 title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
 initrd /boot/initrd.img-2.6.15-23-386
 boot
 
 title Ubuntu, memtest86+
 root (hd0,0)
 kernel /boot/memtest86+.bin
 boot
 
 
 


with unplug CD unit it do not boot

---

### Post by bulldog on 2007-04-11
You van try to reinstall grub from the live cd,but I don't think it will do any good.
Ubuntu sees your cd-player as master boot device and your hdd as slave.

There must be something in BIOS to change this behavior and make the hdd master and cd-player the slave device.

---

