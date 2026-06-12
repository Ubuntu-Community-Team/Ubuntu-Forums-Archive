---
title: "Cannot boot from usb, please help!"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by Deer Hunter on 2012-10-16
Hello all,

I downloaded Ubuntu 12.04.1 64-bit and used unetbootin to try to make a bootable usb.

So, I plug it in, turn my computer on, select to boot from usb, and then I get a black screen with the following white text on it:

> 
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) and then a blinking cursor. 

I've tried this on three laptops, all with no success. CPU on the first is an Athlon 64, a Core 2 Duo on the second, and an Ivy Bridge i7 on the third, all three of which are supposed to be 64-bit compatible according to [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit).

Can someone help me figure out what's going on here? Thanks in advance for the help.

---

### Post by oharebp on 2012-10-16
At the prompt I think all you need to do is type:
startx
 
Then you should get the full X windows graphic environment, least thats
all I needed to do when last in this situation.:p

---

### Post by Deer Hunter on 2012-10-16
Thanks for the reply. Unfortunately, that didn't work, though; it just said
/bin/sh: startx: not found.

Anyone else?

---

### Post by martialartist81 on 2012-10-16
You could always try a different USB Loader tool.  Personally, I used Pen Drive's USB installer (Windows version [HERE]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button"))

I've never used unetbootin before.

Also... you could try to use 11.10 to the USB and attempt to boot it; I've had issues on my PC where I couldn't load 12.04.1 to USB, CD or DVD and get it to boot properly (some type of issue with my hardware that I never quite spent much time trying to figure out).

If you can get 11.10 to load, install it, then upgrade to 12.04.1 and see if that fixes the issue.

---

### Post by Deer Hunter on 2012-10-19
Thanks for the reply. Martialartist, I did as you suggested and used the Universal USB Installer PenDriveLinux to make the live usb drive. I don't know why, but that seems to have made the difference; exact same iso and everything. 

Two of my laptops (the one with the Athlon and the one with the i7) now boot up into a live session. The other one gives the boot-splash screen, and then tells me that it is unable to find a medium containing a live filesystem, which I find rather odd, but oh well.

Thanks for the help!

---

