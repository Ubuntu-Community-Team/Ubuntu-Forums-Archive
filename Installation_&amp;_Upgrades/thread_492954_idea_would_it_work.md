---
title: "idea would it work"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by zach12 on 2007-07-05
hi i'm trying to install ubuntu on one of my laptops (i have installed ubuntu on my 1th laptop and i love it !!!)any way the laptop does not have a cd drive so i tryed installing ubuntu with wubi but it wasn't working so i'm thinking trying this. i have a usb hard drive that you can put any hard drive in to it so i'm thinking of puting the laptop hdrive in the usb drive and
 booting from cd then installing to the usb harddrive then put the harddrive back in the laptop
will it work
thanks

---

### Post by lisati on 2007-07-05
I read somewhere that there are possibilities with this idea....anyone else out there know where to find the instructions?

---

### Post by bigken on 2007-07-05
cant you attach a cdrom to your usb device and boot from that ?

---

### Post by zach12 on 2007-07-05
i don't have one

---

### Post by zach12 on 2007-07-05
what i'm trying to do is install ubuntu on a usb hard drive and then put the harddrive on a computer

---

### Post by bigken on 2007-07-05
so try it it only takes 40mins to install ubuntu

---

### Post by logos34 on 2007-07-05
try this:

[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29)

---

### Post by fishbite on 2007-07-05
Your laptop hard drive is a different size cable connection than the usb or regular hard drive. I don't know if your lap top will boot from a usb device or not most don't! Most lap top hard drives are really hard to remove and reinstall.:confused:

---

### Post by kerry_s on 2007-07-06
> **zach12 said:**
> hi i'm trying to install ubuntu on one of my laptops (i have installed ubuntu on my 1th laptop and i love it !!!)any way the laptop does not have a cd drive so i tryed installing ubuntu with wubi but it wasn't working so i'm thinking trying this. i have a usb hard drive that you can put any hard drive in to it so i'm thinking of puting the laptop hdrive in the usb drive and
 booting from cd then installing to the usb harddrive then put the harddrive back in the laptop
will it work
thanks

Yes, but you need to install grub to the usb drive, so your going to have to use the alternate cd, then after you install grub you need to change it to point to hda. so when it says install grub to mbr select no, then type in /dev/sda1
example: when your installing you will be installing to usb(most likely /dev/sda1) so when grub tries to boot it will look for the boot on sda1 but if the drive is no longer a usb boot in the system you'll need to change the grub root=/dev/hda so it looks in the right place. 
also i'm not sure if you need to make changes to fstab.

---

### Post by zach12 on 2007-07-06
i'm going to borrow a usb cd drive from freegeek

---

### Post by bigken on 2007-07-06
> **zach12 said:**
> i'm going to borrow a usb cd drive from freegeek

got to be the easiest way and probablys the most efficient good luck ;)

---

### Post by logos34 on 2007-07-06
kerry_S is right, if you start playing musical drives you will have to edit your grub config files and fstab once you put the hard drive back in the lappy.  (sda-->hda, etc). Although grub won't be a problem--it  will automatically go to the MBR of the drive in the USB caddy (there won't be anywhere else it can go).  

Just make sure this laptop has a BIOS that supports booting from USB device, otherwise you will have to do an install from Windows hard disk as in the link I provided above (frankly I don't know why you don't try that--i've tested it and it works fine, easier than it looks.  Basically you just copy kernel and initrd images + ubuntu iso to your c:\ base directory and boot from it to start a netboot install.)

---

### Post by zach12 on 2007-07-06
hmm i'll try useing a usb cd drive (if they have one on at freegeek) if not all use the netboot thing or maybe wubi
thanks a ton!:p;)

---

