---
title: "Is MKUSB the best way to do a full install to a USB?"
date: 2017-02-01
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2017-02-01
I want to do a full install of LUBUNTU onto a USB then boot from it to have a fully working (not persistent) environment. I tried MKUSB but when booting got so many errors I could track them all. Thinking of setting up a camera and video the boot process to capture all the errors. I have to go into the boot menu and select the UEFI boot file for the USB and then it looks like it is going to boot (lots of processes run, etc) but finally fails. Didn't write down the last error because I got so many. 

So my question is, if I want to install to a USB and make it a full system, is MKUSB the best (interpret easiest) way to do it?

Acer Inspire F 15 (F5-573G56CG)
Dual boot Win 10 and Mate 16.04 (working just fine)
UEFI mode
Secure boot turned off

Tried MKUSB-DUS version downloaded today with image suggested in the MKUSB tutorial

---

### Post by sudodus on 2017-02-01
Well, I am prejudiced ;-) but I think mkusb can do what you need (and easy enough). Please tell us more to make it possible to give more specific help.

1. Which image did you try? There are many alternatives. Please specify the name of the file.

2. Can we suspect problems with the drivers for the graphics chip and wifi chip? Please specify the brand name and model of the

- graphics chip
- wifi chip

3. It might help, if you manage to make a video clip of what is written to the screen.

---

### Post by sudodus on 2017-02-04
If you need not boot in both UEFI and BIOS but only one of these boot modes, it is straight-forward to install Lubuntu from one USB drive to another USB drive:

1. ***Remove the internal drive***. When the internal drive is disconnected, there is no risk, that the installer will write anything to it, and chances increase that you will write 'everything' to the USB drive, where you want it.

2. If you have other USB devices connected, there might be problems with the installation, so it is a good idea to disconnect all USB devices, that are not necessary during the installation.

3. Boot into the Lubuntu boot drive.

4. Use the standard installer to install Lubuntu into the other USB drive.

5. After you have finished and shut down the computer, you can plug in the internal drive into the computer again.

-o-

If you want an installed system that boots in both UEFI and BIOS mode (and in many computers), it is probably easiest to use mkusb to install from a compressed image file according to [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS). I suggest to install a text-only system,

**dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz** from

[http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios) or
[https://drive.google.com/open?id=0BzX-18u3W1sQUXI2YV95dHJxVlE](https://drive.google.com/open?id=0BzX-18u3W1sQUXI2YV95dHJxVlE)

and to install Lubuntu desktop into it afterwards.

```
sudo apt-get install lubuntu-desktop
```

---

