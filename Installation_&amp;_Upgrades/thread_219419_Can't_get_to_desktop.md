---
title: "Can't get to desktop"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by cmo220 on 2006-07-19
I'm trying to install ubuntu on an old HP Pavillion 4550z from a live Ubuntu desktop cd. I know the cd is good, it has worked on other computers. It has an integrated ATI video card.  It can't get to the desktop.  I have tried most options in dpkg-reconfigure xserver-xorg.  I have tried the F5 (vga) option.  I just can't get the desktop.  Any suggestions?

---

### Post by swamytk on 2006-07-20
> **cmo220 said:**
> I know the cd is good, it has worked on other computers. 
it is not necessary that still it should be good. better check with media check option in the main grub menu of live cd.

> **cmo220 said:**
> It has an integrated ATI video card.  It can't get to the desktop. 

anyway, you are getting shell, right? check the monitor vertical and horizontal frequency settings in /etc/X11/xorg.conf.

---

### Post by SuperMike on 2006-07-20
Were you doing dual monitors coming out of one card? If so, then consider this:

[http://ubuntuforums.org/showpost.php?p=1279482&postcount=138](http://ubuntuforums.org/showpost.php?p=1279482&postcount=138)

If not, if you were using a second video card and you have a motherboard video card as well, then perhaps it's as simple as fixing your system to boot from the proper video card by going into your system BIOS and changing the option for integrated devices from auto to "agp", "pci", or whatever.

---

### Post by az on 2006-07-20
> **cmo220 said:**
> I'm trying to install ubuntu on an old HP Pavillion 4550z from a live Ubuntu desktop cd. I know the cd is good, it has worked on other computers. It has an integrated ATI video card.  It can't get to the desktop.  I have tried most options in dpkg-reconfigure xserver-xorg.  I have tried the F5 (vga) option.  I just can't get the desktop.  Any suggestions?

What exaclt happens?  Does the screen go blank?  Does the booting stop?  What is displayed?

Are you out of memory?  You need at least 192 megs to use the live cd and 256 to use the installer on the live cd.

---

### Post by cmo220 on 2006-07-20
Thanks for the replies.  It was a problem with the monitor.  I can't find any info about the monitor online and I don't have a manual for it.  But I was able to use an old monitor from work, hooked it up, and it works.  I guess that one just doesn't work immediately with ubuntu.  It was a DiGiview HR-50, if anyone cares.  Thanks again.

---

