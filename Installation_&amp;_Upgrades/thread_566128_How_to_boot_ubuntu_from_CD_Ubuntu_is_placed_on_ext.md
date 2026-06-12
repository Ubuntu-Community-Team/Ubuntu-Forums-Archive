---
title: "How to boot ubuntu from CD? Ubuntu is placed on extern USB HD boot from CD ...."
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by kubu_for on 2007-10-03
I've installed ubuntu (7.04) on my extern HD. I also managed somehow to create boot CD. I copied vmlinuz, and initrd.img together with grub and created boot CD. Menu.lst is also ok. Boot works fine and ubuntu as well, but there are two problems:
- after any kernel update I need to recreate boot CD with new kernel files
- CD drive is locked and cannot be used from ubuntu.

Could anyone help me to solve these problems? Is it possible to place boot once on CD and then to load ubuntu from extern HD? This would be the ideal problem solution... Or, is it possible to unlock CD after booting so that I can use CD drive for normal work?

Thanks in advance....

---

### Post by kubu_for on 2007-10-03
This is my drive list:

Disk /dev/sda:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS
/dev/sda2            4866        9729    39070080    f  W95 Ext'd (LBA)
/dev/sda5            4866        9729    39070048+   7  HPFS/NTFS

Disk /dev/sdb:


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         474     3807373+  83  Linux
/dev/sdb2             475       60047   478520122+  83  Linux
/dev/sdb3           60048       60801     6056505    f  W95 Ext'd (LBA)
/dev/sdb5           60048       60801     6056473+  82  Linux swap / Solaris

this is how I boot it from grub (in menu.lst)

title		Ubuntu, kernel 2.6.20-16-generic (from CD sdb1)
root		(cd)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sdb1 quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

I tried to change this sequence to 
root		(hd1,0)
kernel		/vmlinuz root=/dev/sdb1 quiet splash
initrd		/initrd.img

but I get an error "Cannot mount drive..."

I made all possible combinations but I canot load it..

I am not sure how device.map works and if that can help somehow.. 

I would appreciate any help. I do not want to install grub in first HD.

---

### Post by logos34 on 2007-10-03
Boot into ubuntu and install Grub to mbr of external drive using [this howto]("http://ubuntuforums.org/showthread.php?t=224351") (it's for the livecd but the commands are the same).  Except you want **setup (hd1)**.  But before you do that change the 'groot' and 'root' lines in /boot/grib/menu.lst to (hd0,0) -- as soon as you switch the bios boot order the drive designations will change.  

To go into ubuntu change the Bios drive sequence at startup to boot the external first.

---

### Post by kubu_for on 2007-10-05
Well the problem is that my BIOS doesn't support usb boot. If I load kernel from CD and put root to be my external HD it works. However, in this case, my CD ROM is locked and I cannot use it. Is it possible somehow to add USB support to grub? I have nothing against booting from CD, if I can use CD later.

---

### Post by logos34 on 2007-10-05
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

