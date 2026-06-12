---
title: "Multiple Install Problems"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by taddy_porter on 2005-07-10
Ok, have Ubuntu on my office box and I liked it so I thought I'd give Ubuntu/Mythtv a try on my HTPC. It's not working out. My hardware is an Abit A8N-Deluxe with 3 SATA HD's and an Geforce 6600GT vidcard. I bought the 3rd HD specifically for linux so now pre-existing data on it. I went through the expert install. Created my partition table and installed the 64-bit AMD kernel on it. Changed the boot order in my bios to hit the linux HD first so grub would load. That worked fine. I loaded into Ubuntu. Unfortunately I'm conncted to a Mitsi TV via DVI so overscan is an issue. Since this isn't monitor it would only boot into 640x480. Some mods to the xorg file would fix this. Here's were the problems start. First, the tv has about 10% overscan so I can't see the menus. I can manage to get to them but I can't do anything with ROOT. If I try to use synaptic or load a root terminal they crash and won't load. If I try to SUDO it says my user isn't in the SUDOER list so I have no way to change the xorg file to correct. I created a root password during the setup. What am I doing wrong here?

Secondly, it won't load my Windows MCE from Grub. It just stops doing anything after the default partition type blah blah blah text. I can still run WINDOWS by changing the boot order in the bios but it won't load it. Does this have something to do with the installs being on different SATA drives?

Thanks.

---

### Post by taddy_porter on 2005-07-11
Anyone?

---

### Post by al7kz on 2005-07-11
Bonjour,

I'll take a stab at it:

Re your video problem, when you sudo, enter your user password, not root password.

Re booting windows:  I don't know why windows isn't loading. You could have installed grub on the first hard drive boot sector  - no need to change the boot sequence in bios. You can still do that using the grub program - type grub in a shell.

The windows entry in /boot/grub/menu.lst should be something like:

title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by taddy_porter on 2005-07-12
My root and user password are the same.  It's giving me an error that my user isn't in the SUDOER'S list. I can't log in as root either.

---

### Post by codejunkie on 2005-07-12
reboot at grub choose the recovery mode this will enable root temporarily and you can the enable the root account with this command ```
passwd root
``` then set the new root password, reboot like normal login as root in the terminal with ```
su
``` enter the password you just set and follow the guide here [http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers) to add your name to the sudoers file .

---

