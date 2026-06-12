---
title: "Error 17 after installing XP, /boot/grub/menu.lst empty"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Bishop Hill on 2007-12-19
I need some serious help right now. I have searched everything and no post can help me.

To make a long story short:

1. I have run Ubuntu for a while now, and everything has worked great.
2. I have an HP Laptop with 1.2 gb RAM, 128 mb ati 200x graphics card, 2 ghz cpu and 60 gb hdd.
3. I installed Windows yesterday, and after that I used the live cd to restore grub (using the help of [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)).
4. Windows is not among the OS listed in GRUB.
5. **When I try to boot linux, it gives me error 17, cant mount partition.**
6. **On top of that, when I try to check  /boot/grub/menu.lst, it is empty.**

**sudo fdisk -l gives me**

omitting empty partition (5)

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xecddecdd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5755    46227006   83  Linux
/dev/hda2   *        5756        6787     8289540    7  HPFS/NTFS
/dev/hda3            6788        7296     4088542+   5  Extended
/dev/hda4            6993        7296     2441848+  82  Linux swap / Solaris
/dev/hda5            6788        6992     1646599+  82  Linux swap / Solaris
[B]
 /etc/fstab says permission denied, and /boot/grub/menu.lst is just empty.[/B]

What have I done wrong? Can somebody help me, words cannot express how grateful I would be for help.

---

### Post by Pumalite on 2007-12-19
Windows has to be installed first. Ubuntu last.

---

### Post by Bishop Hill on 2007-12-19
> **Pumalite said:**
> Windows has to be installed first. Ubuntu last.

I honestly does not understand what you are talking about. I know that the best thing is to install Windows first and Ubuntu last, but I also know that you can restore grub and Ubuntu after installing Windows. That is what I need help with.

---

### Post by Pumalite on 2007-12-19
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Bishop Hill on 2007-12-19
Great link, hopefully this will do the trick. Will reboot now and look what happends,

---

### Post by Bishop Hill on 2007-12-19
Nope, still same error....

edit I have now edited the menu.lst, I think. Will reboot and try again.

Meanwhile, does anyone else have any idea?

---

### Post by Bishop Hill on 2007-12-19
Nope, did not work.

Will I have to reinstall Ubuntu?

---

### Post by randomnote1 on 2007-12-19
Looking at your partitioning scheme, it concerns me that you don't have 512 or so MB of FAT space at the beginning of your drive.  Normally that is the safest place to put GRUB due to the fact that Windows will take over your boot sector.  Since you're already tried restoring grub and that didn't work, I would suggest using gparted to create a FAT partition at the beginning of your drive and install grub to that.  Good Luck!

---

### Post by Bishop Hill on 2007-12-19
> **randomnote1 said:**
> Looking at your partitioning scheme, it concerns me that you don't have 512 or so MB of FAT space at the beginning of your drive.  Normally that is the safest place to put GRUB due to the fact that Windows will take over your boot sector.  Since you're already tried restoring grub and that didn't work, I would suggest using gparted to create a FAT partition at the beginning of your drive and install grub to that.  Good Luck!

Gparted says that I have 55.89 GiBs unallocated space. Fun.

---

### Post by Pumalite on 2007-12-19
Boot Live CD and post from Terminal (without omissions):
sudo fdisk -lu (copy and paste)
I'll help you mount your partition and find menu.lst. (if there is one)

---

