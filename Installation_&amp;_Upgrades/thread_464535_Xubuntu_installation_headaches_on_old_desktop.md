---
title: "Xubuntu installation headaches on old desktop"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by 09amw on 2007-06-04
I'm having a devilishly difficult time installing Xubuntu on my rather old (1999) desktop that I'm trying to save from the dump.

It's an old Compaq Presario 7970 with 132 mb RAM.  I've been using the alternate install disc, because the computer is right around the border for not able to handle graphical install.  I have been messing around with the boot options, because the darn installer freezes seemingly at random.  The set of instructions that got me the farthest through the installation without problems were "noapic nolapic acpi=off pci=noacpi."  This may or may not be redundant; I'm still rather new to Linux and installing OSes in general.

Anyway, if anyone has any tips about how to get this install to not hang and perhaps, well, install, that would be great.  Also, if the graphical disc works better, I can download and burn that too.

Thanks for the help!

---

### Post by kerry_s on 2007-06-04
did you use the check disk option to verify the disk was okay? have you tried any other linux and does it do the same thing?

try debian, net installer-> [http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

try and installing in stages, you might be running out of memory.

example:
type> server
to install a base system

then reboot and log in

sudo su
to become root

nano /etc/apt/sources.list
turn on all your repos and comment out the cd
ctrl and x and y and enter to save

apt-get update

apt-get install xorg gdm xubuntu-desktop
(or you can do a custom install which would be faster)

reboot and login to the system

---

### Post by Frederick J. Harris on 2007-06-05
I managed to get Xubuntu installed on my old Compaq 1800T (Presario Laptop).  Its from around 2001.  It had 128 mb ram but before I installed Xubuntu on it I took it to a local shop to see if I could get more RAM put in it.  The fellow told me he put a 256 MB RAM chip in it and it only cost me $ 50.00  or so.  However, in Windows 2000 it only lists 192 MB.  However, Xubentu installs on it no problem.  I'm not sure how low you can go with RAM.  Hope this helps.

It has a 20 gigabyte harddrive.  I partitioned off about 6 gigs for Xubentu.  I eventually removed it.  I like Ubuntu better than Xubuntu.

---

### Post by kerry_s on 2007-06-05
well you have the alternate cd right, you can do the server install, then just install the minimum gnome.

apt-get install xorg gdm gnome-core

just don't be one of those that complains about speed. you want the big dog, you get the big dog speed. :p

anyways what ever you use you want to start from the ground up to get the most out of your system.

did you try the debian one i posted, debian has better backward compatiabilty for old hardware, ubuntu screws with the kernel to make it generic and drops a lot of older stuff that might have worked on your system.

what are all your specs? cpu

---

### Post by 09amw on 2007-06-05
I did try your Debian install, but, of course, the computer has a crappy unsupported Linksys wireless card and a busted LAN card, so no internet for me, so no net install either.

I will try the server install and see if I can at least get a base system installed.  I've only had trouble installing Ubuntu and its derivatives on this computer.  It had Fedora Core 5 installed before the Ubuntu installer reformatted the harddrive, so now I have a nice clean hard disk, but no system.

I'll let you guys know if I can get the base system installed -- I appreciate the help!

---

