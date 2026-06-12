---
title: "Install Ubuntu 8.10 to USB Hard Drive"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by funnyguyfunnyguy on 2008-11-02
I've been using Ubuntu 8.04 on an external usb hard drive for the past six months, and I want to start from scratch, installing Ubuntu 8.10 to the external hard drive; however, from the install program on the live CD, I can no longer select the external hard drive as an install location. (Ubuntu does, however, recognize my internal hard drive as a possible install location, and both the internal and external drives are visible from GParted.) I know the 8.10 has a special "USB Flash Drive" install utility, but I don't want to do this. I am simply trying to install Ubuntu to my hard drive, which happens to be an external USB hard drive. Any ideas?

Thanks in advance,
Steve

---

### Post by wlake on 2008-11-03
I have the exact same problem. I did find I could install Xubuntu RC1 to my external hard drive. Since this has worked fine, I haven't downloaded the official release of Xubuntu to try that. I am thinking about installing Xubuntu to another partition on my external HD and then installing the Gnome desktop on top of that, but haven't done it yet. 
Regards,
wlake

---

### Post by mehraan on 2008-11-23
I have the same problem. Any clues?

---

### Post by hooksie007 on 2009-01-19
Same here also..?

---

### Post by hooksie007 on 2009-01-19
Ok, got it to work...

Using a Seagate 40GB USB HD, tried to install multiple times after Live CD boot, but no go.  Even tried formatted drive, ext3, reisnerfs, fat 32, all didn't work.
But I did read another thread about installing 8.04 to a usb device an it worked.  All you need to do is install from the boot screen instead of booting into a live session.  For some reason it works, but just to let you know I had my internal HD unplugged, which I also had it unplugged when I tried to install from a live session...
I left it unplugged because I didn't want it to screw up my GRUB on my work computer.

Pretty happy here, first time I was able to actually help instead of waiting for an answer!

---

