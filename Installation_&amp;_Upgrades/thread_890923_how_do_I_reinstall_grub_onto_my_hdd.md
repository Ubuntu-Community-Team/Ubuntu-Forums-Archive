---
title: "how do I reinstall grub onto my hdd?"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by cool2000m on 2008-08-15
Hey all.

I have the classic "system files on hdd, can't boot without hdd" grub problem. How do I restore the windows' version of grub and then put grub on my hdd, so I can use it on any computer? Thanks!

---

### Post by logos34 on 2008-08-15
not sure what you mean.  You have an external drive?

---

### Post by cool2000m on 2008-08-15
Yes. It's a 500 GB high-end, fanless hard drive (it doesn't need one!). Half of the partition is set for ubuntu, and the other half is set for windows. The Grub (or bios, I dunno which) is on my internal hard drive. How do I reset the windows MBR (I don't have a windows live disk) and put grub/bios on the hdd? and would this cause hardware detection problems? thanks!

Oh... by the way, can you use a hard disk (like, say, drive D://) for swap memory? That'd make my computer way fast.

---

### Post by logos34 on 2008-08-15
swap: yes, you can put it on another disk to speed things up.

You can restore windows bootloader from the Super Grub Disc (see link my signature).

Install grub to the MBR of the external disk from the ubuntu live cd (link in my sig).

You'll have to edit /boot/grub/menu.lst so the 'groot' and 'root' lines read (hd**0**,?) instead of (hd1,?)

---

### Post by Sef on 2008-08-15
> You'll have to edit /boot/grub/menu.lst so the 'groot' and 'root' lines read (hd0,?) instead of (hd1,?)

The full command is ```
gksudo gedit /boot/grub/menu.lst
```.

---

### Post by cool2000m on 2008-08-16
that's great... but how do I find out what (hd?,?) am I?

Besides that, I'm cool.

**EDIT**

and also, I want my SDA drive to be portable... as in I can boot my ubuntu from any computer.

---

### Post by logos34 on 2008-08-16
sudo fdisk -l

will list your partitions including root.  The external right now is being seen as (hd1) because it's listed second in the bios (windows internal disk is the boot disk).  But as soon as you change it to boot grub on the external, it will become (hd0)

Remember, grub starts counting from 0, so if fdisk says root is sdb1, then you want (hd0,0)

---

