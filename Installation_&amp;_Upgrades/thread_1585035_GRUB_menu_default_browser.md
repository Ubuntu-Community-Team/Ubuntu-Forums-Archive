---
title: "GRUB menu default browser"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by DogoDave on 2010-09-29
Hi,

I have just fixed my cousins netbook that had several bad viruses.  I installed Ubuntu Netbook on a 20 gig partition I made, and then I booted into Ubuntu and installed Avast anti-virus and scanned the windows partition, removed and restored some system files while in Ubuntu and then booted back to Windows XP and finished updating and fixing that installation.  

I would like to keep the Ubuntu Netbook installation on this netbook so that if I need it again I can just boot into it and make use of it.  I found running live off the USB stick and installing and updating the AV to be a bit of a pain in the azz.  

This is my cousin's and she wants to use XP, so the end goal here is to change the default OS in grub to the Windows XP installation and have it remain the default even it I update the Ubuntu kernel and it adds another line to the grub menu.  

How do I do this?  

Thanks

---

### Post by drs305 on 2010-09-29
If the computer boots to the Grub menu, the easiest way to configure the default OS and menu timeout is to install *startupmanager*. It's a GUI app that can still perform the basics even in Grub 2.

Here's a guide I wrote about SUM a while back. It will tell you how to install and run it:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

If you would prefer to manually edit the Grub2 configuration files, click on the G2-Tasks in my signature line.

---

### Post by DogoDave on 2010-09-30
Thanks,  best & easiest thing I have seen since switching to Ubuntu

---

