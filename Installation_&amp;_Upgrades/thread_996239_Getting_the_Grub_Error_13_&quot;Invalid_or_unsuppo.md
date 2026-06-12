---
title: "Getting the Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by xterminal01 on 2008-11-28
I have two hard drives. On one is vista and other one is ubuntu 8.10. First of all the vista installation has overwritten my MBR.
Because now i don't have the grub screen when booting up. 
Secondly, when i use the supergrub cd and manage to get the grub boot loader to show up. And try to boot inside ubuntu i get 
Grub Error 13: "Invalid or unsupported executable format."
Does anyone have any suggestions on this?

---

### Post by sadiqdude on 2008-11-28
hi since u areusing two hard drives and two diffrent os in them creates a lot of problem u have to install both the os on only one hard disk then only ur grub boot loader will work u can use ur onother hard disk for storage pupose i mean use it as a secondry drive and remember the drive which u are installing both the os has to be the master hard disk not the slave one this is very importanat..........k:):):):)

---

### Post by caljohnsmith on 2008-11-28
Can you set your BIOS to boot the Ubuntu drive on start up? If so, you can install Grub to the MBR of the Ubuntu drive and make it bootable by first booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you can't change your BIOS to boot your Ubuntu drive, you can install Grub to the MBR of your Windows drive by doing everything above except the last command "setup (hd0)". See if you can get the Ubuntu drive booting and let me know how it goes; we can work from there if you want.

---

### Post by xterminal01 on 2008-11-28
The Windows hard drive is sata, so i can't set it as master or slave. The Linux is IDE. If I turn off the sata the Linux shows me the grub. However, in the bios i can't set the boot up sequence to boot up specific hard drivers.
The problem is when i choose to boot up the linux i get the error
Error 13: "Invalid or unsupported executable format"

> **caljohnsmith said:**
> Can you set your BIOS to boot the Ubuntu drive on start up? If so, you can install Grub to the MBR of the Ubuntu drive and make it bootable by first booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you can't change your BIOS to boot your Ubuntu drive, you can install Grub to the MBR of your Windows drive by doing everything above except the last command "setup (hd0)". See if you can get the Ubuntu drive booting and let me know how it goes; we can work from there if you want.

---

### Post by caljohnsmith on 2008-11-28
> **xterminal01 said:**
> The Windows hard drive is sata, so i can't set it as master or slave. The Linux is IDE. If I turn off the sata the Linux shows me the grub. However, in the bios i can't set the boot up sequence to boot up specific hard drivers.
The problem is when i choose to boot up the linux i get the error
Error 13: "Invalid or unsupported executable format"
If you want, you could install Grub to the MBR (Master Boot Record) of your Windows drive so you can boot to Grub with both drives connected. Do you want to do that, or do you just want to get the Ubuntu drive booting OK when you turn off the Windows SATA drive? How about following my previous instructions for installing Grub to either the MBR of the Ubuntu drive, or to your Windows drive if you choose. Once you do that, you should be able to boot Ubuntu without SGD, or at least get the Grub menu on start up.

---

### Post by xterminal01 on 2008-11-28
IT WORKED !
All i needed to do is to unplug the windows driver boot into linux, and do your commands and plug in the windows hard drive and the grub showed up !
Thanks for the help ! 

> **caljohnsmith said:**
> If you want, you could install Grub to the MBR (Master Boot Record) of your Windows drive so you can boot to Grub with both drives connected. Do you want to do that, or do you just want to get the Ubuntu drive booting OK when you turn off the Windows SATA drive? How about following my previous instructions for installing Grub to either the MBR of the Ubuntu drive, or to your Windows drive if you choose. Once you do that, you should be able to boot Ubuntu without SGD, or at least get the Grub menu on start up.

---

### Post by caljohnsmith on 2008-11-28
That's great news you have it working, and I'm glad to help out. Cheers and have fun with your OSes. :)

---

