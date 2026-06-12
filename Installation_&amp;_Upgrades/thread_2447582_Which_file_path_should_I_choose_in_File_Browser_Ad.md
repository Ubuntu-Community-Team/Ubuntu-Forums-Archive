---
title: "Which file path should I choose in File Browser Add Boot Option (BIOS)?"
date: 2020-07-21
forum: Installation &amp; Upgrades
---

### Post by warbler2 on 2020-07-21
I have created a bootable USB stick for Ubuntu 20.04 LTS ([https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)).

Now I am trying to install Ubuntu desktop from it. 

With the live USB inserted, I restarted my computer. There was no Ubuntu welcome window. 

I entered the BIOS. Only Windows Boot Manager appears in Boot Option Priorities:


[ATTACH=CONFIG]286507[/ATTACH]




 
































In File Browser Add Boot Option, after selecting my USB stick, which file path should I choose?


[ATTACH=CONFIG]286509[/ATTACH]                                                                                                





































Thanks.

---

### Post by oldfred on 2020-07-21
Please attach screen shots or photos. Not everyone has high speed Internet.
Easy to attach with forum's go advanced editor and paperclip icon.

That looks more like internal UEFI boot options where you can set which is first in boot order.
To boot USB flash drive, you use UEFI one time boot key, often f12, but varies by every mfg. Check your manual.
You also may have settings in UEFI to enable USB boot or full USB support or both. Again varies by vendor.

You should see UEFI:flash and flash where flash is name or label on the flash drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by warbler2 on 2020-07-21
Here are the photos.

---

### Post by oldfred on 2020-07-21
Those look like your UEFI, not your UEFI boot.
What brand/model system?
What video card/chip?

Did you review the examples in the previous post's links?
And also many UEFI boot links in my signature below.

---

### Post by warbler2 on 2020-07-22
Before starting this thread, I had also tried to use the UEFI one time boot key (F12).
It brought me to the screen you can see in Photo 1 attached.
I then entered USB1 - UEFI OS (SanDisk).
It brought me to the screen you can see in Photo 2 attached.
From *Ubuntu, it then crashed and the following message was written: "[0.000000] [Firmware Bug]: Failed to parse event in TPM Final Events Log" as you can see in Photo 3 attached.

I have an Alienware Area 51-m R1.
Intel Core i9-9900K CPU @ 3.60GHz
(Intel UHD Graphics 630)
NVIDIA GeForce RTX 2080
Windows 10 Home (version 2004)

I am going to review the examples in the links that you mentioned and the UEFI Boot links in your signature.

---

### Post by oldfred on 2020-07-22
To boot installer, you boot USB1 in UEFI options.
After install, you also get an "ubuntu" boot option.

Because you have nVidia, you need the nomodeset boot parameter. They have added the safe graphics which I really do not know but bet it adds the nomodeset parameter for you.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Alienware is similar to Dell and needs UEFI update and SSD firmware update.

Some older threads:
[https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506](https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506)
Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)

---

### Post by warbler2 on 2020-07-25
It worked fine when entering Ubuntu (safe graphics).

Thanks.

---

