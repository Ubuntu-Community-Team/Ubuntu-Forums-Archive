---
title: "I want to install ubuntu w/o CD-ROM, how to?"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by karinr on 2007-01-04
I have a 3 year old laptop with a new and empty hard disk in it, a floppy station but, no working CD-ROM.  It´s a HP laptop and  the CDROM has been changed/repaired twice, still not working. The laptop cannot boot from USB, either and there are no BIOS option to make it boot from USB. 

Is there an easy way - designed for newbies like me - to install Ubuntu by use of floppy boot up (ready made floppy images) and then be able to download/install the rest via the net?
I am totally new to anything but Windows and so need an easy explanation. 

If no such installation method exists, do any of you know if there are any other functional Linux distro(s) that can be installed without using a CD? 

Or, if it is possible to download first another linux variant and then download/install Ubuntu from there? 
(I do know from Debian´s pages that floppy images do exist - BUT, they are well hidden and out of reach, no download link anywhere). 

The reason why I want to install Ubuntu is to have a working, reasonably virus safe  computer. My windows installation was damaged by a virus. I am hoping I will not have to buy yet another new laptop with Microsoft-ware on it.

---

### Post by aysiu on 2007-01-04
Maybe this might work?
[HOWTO: Install Ubuntu Linux without burning a cd](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by karinr on 2007-01-04
Thanks, aysiu.  I have however read this page before and soon understood it excluded newbies like me...   I have no knowlegde if Linux commands at all. I wondered if there were ready made floppy image(s) that would lead me right to network install.

---

### Post by aysiu on 2007-01-04
I can't imagine any method *sans* a CD-ROM will be easy for new users.

You'd honestly have an easier time installing and using Debian.

---

### Post by Pobega on 2007-01-04
I know Debian has a floppy-disc NetInstaller, you should give that a shot.

[http://www.us.debian.org/distrib/netinst](http://www.us.debian.org/distrib/netinst)

---

### Post by karinr on 2007-01-04
Thanks you. Yes, I already knew about this page. But, the links lead to the installation manuals only, not to the floppies to start the net install process. There are no links to these floppy images from anywhere on Debian´s pages as far as I can see.

---

### Post by scaryant on 2007-01-04
It is possible to install Ubuntu with a floppy disk set, I've not done it myself with Ubuntu but with other distro's. I imagine that you'd be able to use the USB instructions...

If you have another network enabled Windows machine that you can use at home (or wherever you are) you might be able to install Ubuntu via your network.

With a laptop that is only 3 years old it is likely that your built-in network card has the ability to boot via the network. If it can you should be able to see an option to boot from the network in the BIOS boot options, it'll probably appear as LAN - set your laptop to boot from this option and then see if you can follow this howto [I wrote]("http://www.ubuntuforums.org/showthread.php?t=327597") after I did it myself.

---

### Post by karinr on 2007-01-04
Thank you, scaryant! Your how-to is the only walk-through I´ve seen usable for newbies like me.
Only one problem: Your how-to assumes there are a working windows installation ...and mine went bad (virus attack), windows will not boot at all. So, I took the hard disk out and replaced it with a new and empty, ready to install ubuntu.  

The laptop and network card can boot from network. The only thing lacking is a starter, a basic installation to further install into. 

My laptop cannot boot from usb. Network booting does work,  PXE is enabled. 



> **scaryant said:**
> It is possible to install Ubuntu with a floppy disk set, I've not done it myself with Ubuntu but with other distro's. I imagine that you'd be able to use the USB instructions...

If you have another network enabled Windows machine that you can use at home (or wherever you are) you might be able to install Ubuntu via your network.

With a laptop that is only 3 years old it is likely that your built-in network card has the ability to boot via the network. If it can you should be able to see an option to boot from the network in the BIOS boot options, it'll probably appear as LAN - set your laptop to boot from this option and then see if you can follow this howto [I wrote]("http://www.ubuntuforums.org/showthread.php?t=327597") after I did it myself.

---

### Post by scaryant on 2007-01-05
Hi. You've misunderstood slightly, you need two PC's - only one (for my walk-through) must have Windows XP/2000 running and working, this is the one that is used to host the Ubuntu boot image. The other (which you intend to install Ubuntu on to) doesn't need to have anything at all, the disk doesn't even need to be partitioned - but it must be plugged into the network and must be able to access the internet from the network (Ubuntu will take care of this for you, the PXE Booter on your LAN card will get the IP Address for you)

Hope that helps, cheers.

---

### Post by karinr on 2007-01-06
Aha, now that´s good news! Thanks again. 

Ok, so the computers here are directly connected to the internet (no house LAN). I have a wireless router with four outputs. Can I connect the laptop I want to install ubuntu on to the router and also this working laptop, and have it done that way?
Guess I´m asking stupid questions... pardon me, I´m not good with his.  

> **scaryant said:**
> Hi. You've misunderstood slightly, you need two PC's - only one (for my walk-through) must have Windows XP/2000 running and working, this is the one that is used to host the Ubuntu boot image. The other (which you intend to install Ubuntu on to) doesn't need to have anything at all, the disk doesn't even need to be partitioned - but it must be plugged into the network and must be able to access the internet from the network (Ubuntu will take care of this for you, the PXE Booter on your LAN card will get the IP Address for you)

Hope that helps, cheers.

---

### Post by scaryant on 2007-01-06
Hi, yes that's what you *have* to do both computers must be connected to the router. Most likely the PC that you want to install Ubuntu on will have to be connected to the router using a cable (not wireless) unless your wireless card supports PXE booting, but I highly doubt it.

> Remember children there's no stupid questions, just stupid people - Mr Garrison.

;)

---

### Post by confused57 on 2007-01-06
Here's a howto for installing DSL, without a CD:

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=5;t=14925;st=0](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=5;t=14925;st=0)

---

### Post by karinr on 2007-01-10
Thanks again, scaryant. I haven´t come around to do anything about it yet. I tried to boot up another way and that did not work at all.... 
Thanks a lot to you, too, confused57.  DSL may be an option to install first, to get some kind of starter, if I don´t get it to load and install ubuntu directly.

---

