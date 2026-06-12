---
title: "installing using a boot floppy and an external usb cd-rom drive"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by odysseus.lost on 2006-06-14
Hi,

I want to install ubuntu 6.06 server on a system that can only boot from a floppy and has an external usb cd-rom drive.... How is it possible to do that? Is there any way to create a boot floppy and then use the external usb cd-rom drive?

Thanks.

---

### Post by martypants on 2006-06-14
I have exactly the same problem...  My bios doesn't recognize the external usb cd-rom...  And I can't find an easy way to install the new Dapper Drake...

---

### Post by The Cosmic Hobo on 2006-06-14
You'd need a bootable floppy which provided both USB support and CD-ROM support... Someone more knowledgeable than I might know where you could find such a thing, or possibly point you in the direction of a suitable solution.
In theory, there are some very small distros out there, so with a little technical help you could have one on a floppy which simply mounts the USB device and allows you to run the installer from a command line. I stress the *in theory* part, because I have absolutely no idea how practical it would be to implement, but I'm sure someone else will be able to expand upon it shortly.

---

### Post by odysseus.lost on 2006-06-21
[QUOTE=martypants]I have exactly the same problem...  My bios doesn't recognize the external usb cd-rom...  And I can't find an easy way to install the new Dapper Drake...[/QUOTE]

Make sure you check your bios boot settings that you are not able to boot from an external usb device... In my case I was lucky that I am finally able to do so and hence saved me the trouble... However,  a few links that I had a look and seem that could be of use were: (bear in mind that I have not tested any of the procedures described....)
[http://btmgr.sourceforge.net/](http://btmgr.sourceforge.net/)
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

if you are flexinble in using another distro the following is for fedora:
[http://www.linuxquestions.org/questions/showthread.php?t=444013](http://www.linuxquestions.org/questions/showthread.php?t=444013)

---

