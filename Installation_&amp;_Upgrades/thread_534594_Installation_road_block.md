---
title: "Installation road block"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by Kxpress on 2007-08-25
This is my first attempt to install Ubuntu 7.04 on my new Laptop. I have used the same Ubuntu CD on a desktop, it is OK. For the laptop, I selected to start with VGA, 1280x1024, 1280x800 or defaulted VGA. This is what I see on the screen:

----------------------------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in command.
/bin/sh: can't access tty; job control turn off
(initramfs)
---------------------------------------------

I am stucked here, how can I proceed further ?

Thanks,

My ThinkPad T61 configuration:

Intel Centrino Core2 Duo T7300 2.0 GHz
DDR2 PC5300 2.0 GB
SATA 120 GB
Nvidia Quadro NVS 140
15.4 WSXGA+ TFT Screen (1280x1050)
Intel PRO/WL3945abg Card.

---

### Post by Pumalite on 2007-08-25
Try Alternate CD

---

### Post by Kxpress on 2007-08-25
Any other suggestion ? I am downloading the Alternate CD...

---

### Post by Pumalite on 2007-08-25
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Kxpress on 2007-08-29
Used Alternate CD version or go to BIOS change SATA to Compatibility.
However, further along the installation to get over with the Xserver problem, I had to to change graphic display mode to "vesa".

In short, I have my machine configured as dual-boot (WinXP and Ubuntu 7.04 Linux) :
- Wireless Intel 3945 is not working consistent.
- Graphic/Display remains "vesa" with 800x600 resolution. I need "step-by-step" instruction to install Nvidia Quadro M140 NVS Card to utilize my full15.4" WXGA 1680x1050 resolution.
- Sound is not working yet.
- A little annoying thing is the loader shows there are so many choices to boot in the menu:
      Ubuntu, kernel 2.6.20-16-generic
      Ubuntu, kernel 2.6.20-16-generic (recovery mode)
      Ubuntu, kernel 2.6.20-15-generic
      Ubuntu, kernel 2.6.20-15-generic (recovery mode)
      Ubuntu, memtest86+
      Other Operating system:
      Microsoft Window XP Professional

This is just a cosmestic thing, but it will be great if it could be clean.

So far my machine is usable, I don't want to mess it up. I REALLY need to know how to back it up i.e. restore to the current configuration before installing new dirvers. I've read some posts mentioned problems after installing new drivers for graphic card, CD/DVD burner, Wireless, Sound etc..
Is it true ?

I am a very "fresh" newbie in Linux, considered a "illiterated" Linux guy... I am starting to learn Linux, please bear with me.

Thank for your help if any.

---

### Post by Pumalite on 2007-08-29
Be happy you have a working dual boot system. Keep the extra kernels for the moment. For wireless go to 'Networking'. For drivers for your card visit this site: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) Check 'page'.

---

