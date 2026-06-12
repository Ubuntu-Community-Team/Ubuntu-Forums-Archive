---
title: "Can't get installer working from USB"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Raiscan on 2011-02-24
Hi all,

I'm trying to install ubuntu 10.10 onto my desktop via usb. Depending on the tool I use to put the image on the USB drive, I get the following outcomes:

**Universal USB Installer**

whatever the default in results in no signal after the kernel has done it's work (i.e when the graphics kick in)

"Install Ubuntu to Hard Drive" results in a quick flash of graphical garbage, then an 'incomplete' gnome desktop; the wallpaper is there, a blank menubar with some of the top-right icons (like power etc.) but nothing else. Mouse moves but left, right click and keyboard does nothing. Can't move to the different terminals either.

[B]UNetbootin
[/B] One option is a blank screen, another results in graphical garbage which appears to be whatever was left in video ram? There was a cool collage effect of my windows logoff screen :D cursor is fully formed and moves, but that's all.


This isn't limited to Ubuntu 10.10; Fedora 14 has the same problem, but I can boot into basic video and get a desktop. Obviously, I don't want Fedora :)


I'm assuming my problems are the result of the nouveau video drivers, so my question is this; how do I get ubuntu to use an okay (preferably not basic vesa) graphics driver so I can install? And if I can do this, will enabling nouveau again (a newer version hopefully) cause my problems to continue?

Specs:
Asus P5Q Deluxe Motherboard
Intel Core 2 Quad Q6600
Nvidia Geforce GTX 295 (original revision)

Thanks!

---

### Post by MauserM98 on 2011-02-24
I've tried both Ubuntu and Fedora flawlessly. Do you use 32 or 64 bit versions?
I don't think that is the problem but maybe. I use 64 bit versions on everything that is capable of using it, 32 bit is for wimps and bad hardware.
I do use Fedora at the moment due to my needs and videodrivers is quite easy to fix after installing the system. In the meantime it uses the noveau driver witch is rock solid.
If it is possible to use noveau in Ubuntu is beyond my knowledge.

---

### Post by oldfred on 2011-02-24
With my 9600GT nVidia card, I had to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Not sure on your USB Flash installer, if you get the option on boot. Try hitting key as soon as it starts.  I install using grub2 and just add the nomodeset to the grub line, just like on first boot after install. You may be able to add it to syslinux's menu??

---

### Post by artofwar1 on 2011-04-13
look i had the same problem 
disabling the firewall  & the antivir didn't change the prob.
however you can extract the files (with rar or something)
cange the name on the directoey from "isolinux" to "syslinux"
in the directory from "isolinux.cfg" to "syslinux.cfg"
rebuild the iso with imgburner & than use the universal installer 

 i found that solution in the ubuntu geek site 
these guy know ****

i checked in works it installs ect.

---

