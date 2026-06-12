---
title: "full install on usb"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by madeki0663 on 2013-12-01
I'm running live cd (ubuntu-12.04.3-desktop-amd64) from USB stick (7 GB). Installed with Universal-USB-Installer-1.9.5.1. This works well.

Now is there a way to get this fully installed on this stick or should I use a bigger one (  64 GB ).

And how to do ? Can I use this live CD on ths stick and install from here ?

---

### Post by heir4c on 2013-12-01
A bigger one is better if you will keep files, documents, photo, etc... on that stick.
7GB is a little bit small, give Ubuntu a little bit space to work.
You need also a swap partition.
So, take a second usb and plug it in, choose from out the live-usb the other usb and install it on that one like you do up a HD.
I run for weeks with a 32GB usb.
It will be slower than on a HD.
I think it is better to use the 32bit version.

IMPORTANT!!!: See that the Grub is installed on the second usb so choose the right /dev/sdx (without a number) to install it. 
See the first screenshot in the following link (It's in Dutch but you see in the bottom of the window the chooses you can make. It's a button you can click on when you install):
[http://forum.ubuntu-nl.org/andere-distributies/installatie-elemetaryos-naast-ubuntu-12-04-en-windows7-koppelpunt/msg890099/#msg890099](http://forum.ubuntu-nl.org/andere-distributies/installatie-elemetaryos-naast-ubuntu-12-04-en-windows7-koppelpunt/msg890099/#msg890099)

---

### Post by madeki0663 on 2013-12-02
Do I have to make partitions?  And the grub do I have to install it before or after the installation ?
I think i'll buy a 64 GB stick to play with.
(is er meer info op de nederlandse site ?)

---

### Post by sudodus on 2013-12-02
You can install to a USB device exactly like you do to an internal drive (except that you point to the USB device instead, both the partition and the bootloader 'grub', as *heir4c* told you in post #2).

See this link for more information about USB devices

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

and the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") will do it for you in a convenient way. You need two USB devices, one for the installer (4 GB or more) and one where you want to install the system (8 GB or more). I have good experience of Sandisk Extreme 32 GB pendrives.

---

