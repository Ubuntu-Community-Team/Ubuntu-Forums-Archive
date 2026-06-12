---
title: "Ubuntu 8.04, &quot;Hardy Heron,&quot; Install hung"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2008-04-27
I’ve read a lot of positive things about Ubuntu so I decide to try it out.
I use a spare desktop PC, bought in 1997, as a test machine.

I had previously installed XP and Fedora 8 on my desktop PC and tested dual boat XP and Fedora 8 successfully on that desktop. 

On 25 April I reformatted the hard drive on my desktop PC to ext3 using Partition Magic. 
I downloaded ubuntu-8.04-desktop-i386.iso, burnt the image to a CD and then attempted to install Ubuntu.
A message:
8139cp …  this (id 10ec:8139rev10) is not a 8139cr compatible chip
8139cp   trying the “8139t00” driver instead
some 20 or so seconds later a message stating “starting Gnome” a message “… deferred execution …” appeared very briefly. The monitor screen went blank and the install hung.

What information about my desktop PC does the team need to determine what may be wrong with Ubuntu please?

Regards, Mike
P.S. I’ve since installed Fedora 8 on my desktop PC where it is running successfully.
A listing of the hardware obtained from lshw is [***[COLOR="RoyalBlue"]txt here[/COLOR]***]("http://www.eacott.org.uk/hardware.txt") or [***[COLOR="royalblue"]html here[/COLOR]***]("http://www.eacott.org.uk/hardware.html")

---

### Post by ssican on 2008-04-27
When Partitioning, not make use of Partition Magic.
Make use of GParted (Gnome Partition Editor):
In the LIVE CD: System > Administration > Partition Editor,
or, in the INSTALL PROCESS > PREPARE DISK SPACE > HOW DO YOU WANT TO PARTITION THE DISK > MANUAL
Manual Install of Ubuntu, use the GParted:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

EDIT: Burn the .iso image on Speed of 4X or Less (3X).

---

