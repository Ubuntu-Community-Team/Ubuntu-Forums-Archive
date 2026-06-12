---
title: "cannot install grub 2"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by thisfreaks on 2009-11-21
Hi guys, 

I'm new to Linux and I'm having a bit of trouble getting things to work. I downloaded and installed Ubuntu 9.10 32-bit without trouble. However, I can't seem to get GRUB2 to work so that I can boot into my new OS. I already have Windows 7 installed and my computer boots into that every time. I have a "fake raid" set up, but I don't know if that's what's giving me trouble because the array shows up during the installation process and in Gparted. When I try to install dmraid, I am told it's already installed and up-to-date. 

I've been referencing this: 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

I've been trying to run the commands from a LiveUSB of Ubuntu. I've tried the three methods for installing listed in that guide, but each returns errors. I don't know if I'm doing something wrong, or there is genuinely a problem going on. 

A friend who has been using Linux for a few months told me that I should download an older version of Ubuntu with which to install an older version of Grub... Is that really the solution? 

Please help!

---

### Post by jaden93 on 2009-11-21
when you were installing ubuntu 9.10, at the end of the installation did you press skip? if so you most reinstall ubuntu 9.10 and do NOT press skip.

---

### Post by darkod on 2009-11-21
There are issues with fake raid. Just to let you know, sorry I don't have more experience with that to help.

PS. For LVM and RAID installation the Alternate CD needs to be used. I think that can work for you.

---

### Post by thisfreaks on 2009-11-21
I'll try the Alternate CD. Downloading it now. Thanks!

---

### Post by thisfreaks on 2009-11-21
The Alternate CD does not work either. When I get to the step that installs the boot loader, the install bar gets to 16% and then goes back to the menu for the installation. It gives me the option to install the LILO boot loader, but from what I understand, you shouldn't use that one for newer versions of Linux. 

I'm back to square one.

---

