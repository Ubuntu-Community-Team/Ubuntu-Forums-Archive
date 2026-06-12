---
title: "Live CD booting from a USB Stick"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2008-10-03
I tried a few of the current ideas of getting a LiveCD system to boot from a USB stick, but I on each trial after making it and then trying to boot it on a different computer it wont load without getting error before the desktop apears.

My computer is now getting old and a mate has a new PC with the latest video card etc..

When I boot a live CD it goes all the way to desktop environment. But when i try make a live usb it seems to have only setup drivers for my computer and there is no drivers for video and possibly more things for this other computer when I boot from the usb stick.

What is the correct method or program to use to have an exact copy of a live cd on a usb stick. I don't need to add software to the ISO of a live cd, just want a straight copy of the live cd on the usb stick. I think a live CD boots on anything and reguardless of hardware can use generic drivers.

I tried looking at setting up a usb stick to boot and mount the iso and boot it, that option I prefered to try cause I can fit several ISOs on the 16gig usb stick then.

As I said I tried a few options and failed.

---

### Post by zakalwe_ukuk on 2008-10-03
Theres a program called unetbootin that will install the live cd onto a usb stick for you. Worked perfectly for me. Be warned though that if your installing Hardy via usb you will run into problems mounting external drives, though this can be fixed afterwards.  Don't know if the problem exists in Intrepid though.

---

### Post by skozzy on 2008-10-03
Ok, I will give that one a shot.

---

### Post by vijaym on 2008-10-03
see the site [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/) which should help

---

### Post by C.S.Cameron on 2008-10-03
8.10 has a new tool called usb-creator.
It works on 8.04 just fine.
You can download it here:
[https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7](https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7)
Setting up a Flash drive takes about 2 minutes
There is the choice to make the drive persistent or not.
It will install to USB directly from an iso on the desktop.
No CD's required.
I installed Xubuntu 8.10 onto a 2G flash and still have 1.2G free.
Much, much easier than trying to follow the instructions at pendrivelinux

---

### Post by skozzy on 2008-10-03
UnetBootin is ok and works, but it copys files from the iso to the usb stick and doesn't use the ISO, and it also locks the free space on the usb stick so I can't write to it.

I tried the pendrive site as well, that one also installs files and when I try to boot the stick on another computer I don't get gnome to load, there is errors about video drivers not installed.

And I have issues with 8.04, when I load that version non of my SATA drives appear, so I stick to only version 7.10 for now.

The 16gig usb stick can hold many ISOs, 32 and 64 bit versions of ubunut and kbunutu plus win2k winxp and vista ISOs.

---

