---
title: "Grub fails when install server 7.10 from usb"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by sunhan on 2007-12-11
I have placed the hdd installer placed on a 1gig usb stick. Made it bootable with syslinux 3.11
Placed the *.iso of server edition of ubuntu 7.10 als on the stick. During install it cannot find the *.iso
Found a sollution for that on the forums. But after the partitions are made and all files are copied it gets an fatal error during the install of grub or lilo.

The pc iam trying to install it on has no floppy drive or cdrom drive. So al has to be done with usb.

I tried installing grub using damn small linux and this also gave no succes.

I hope someone can help me around here because iam realy stuck..

---

### Post by jasmuz on 2007-12-11
Greets.

Have you checked this out: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sunhan on 2007-12-11
yes i have tried that but i ran into the error that is discribed at the bottem of the thread. I cannot mount the sda1 as cdrom. So i tried the option to use the hdd install files. that did work only it gives a error finding the iso but there is a solution to that also. Then the next error is that grub fails to instal to hda1 or hda. So it fails to write MBR.

---

### Post by jasmuz on 2007-12-11
Well, you have a "hitch".

If you dont mind using another distro, please try the father of our distribution, DEBIAN, wich has all the weird and funny ways of installing on hard to get hardware.

Read here: [http://www.debian.org/distrib/netinst#verysmall](http://www.debian.org/distrib/netinst#verysmall)

---

