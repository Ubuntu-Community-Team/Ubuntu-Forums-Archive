---
title: "Installing on a Netgear ND508/520"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2008-05-14
I don't think any one can help here. But maybe.

I love to get Ubuntu server working on a Netgear ND508 or ND520. Each came with a 8GB or 20GB hard drive. All it has is some LED's, Power, and Ethernet to it. No keyboard, mouse, or screen!

But I have got Trustix Secure Linux 3.0.5 installed and working on it. It booted with both GRUB LILO but that was Trustix. But Ubuntu it will not with ether GRUB or LILO boot. I install it and Trustix on a motherboard with a Ethernet card like the chip it has in the Netgear. So that way I can log in to it to use it.

I am thinking they my be a way save a Ubuntu server on it and then edit Trustix's GRUB boot to point to the Ubuntu boot. But I don't know how to do this and if it can be done. Any one know.

I got this working on a 320GB hard drive. I can't do nothing with the BIOS in the Netgear ND508. It's something it works with a big hard drive. When other older PC need a update BIOS. So the Netgear is good for this but is OS is very old and hard to make it work on a bigger hard drive.

Or any one know a good place to ask this? Because any post I have done here I get no help!

-Raymond Day

---

### Post by dbstraffin on 2008-05-14
Did you try the trustix forums?

I don't know much about the device.  But maybe a few ideas.
Since there is no display or serial, you can't really tell what grub has for an error right? 
You could compare /boot/grub/menu.lst from trustix and ubuntu.  
Do a fresh grub install and force it to point to (hd0,0)
You could also try using dd to backup the mbr (containing grub stage 1) from trustix and copying it to the ubuntu drive, making a backup of the ubuntu mbr first.  You only want to copy the first 446 bytes of the drive like:
dd if=/dev/hda bs=446 count=1 of=mbrbackup
and then
dd if=mbrbackup bs=446 count=1 of=/dev/hda

---

### Post by Raymond Day on 2008-10-01
NASLite HDD works on the Netgear ND508/520! Can use the install CD on about any system. Set it up some on that system then put the hard drive in the Netgear and it works. I and others posted about it here:

[http://www.serverelements.com/forums/viewtopic.php?f=10&t=2200&st=0&sk=t&sd=a&start=15]("http://www.serverelements.com/forums/viewtopic.php?f=10&t=2200&st=0&sk=t&sd=a&start=15")

I think this is better then a Ubuntu server as a NAS box.

It my be neat if they had a easy set up ubuntu NAS CD.

-Raymond Day

---

