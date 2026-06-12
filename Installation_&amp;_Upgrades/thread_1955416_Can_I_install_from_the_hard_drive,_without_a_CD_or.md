---
title: "Can I install from the hard drive, without a CD or internet?"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by petermg on 2012-04-09
I have a laptop that has problems reading from the CDROM drive, no floppy drive, and no internet access at the moment.  Can I just hook the drive into one of my working Ubuntu PCs and somehow create a partition that it will boot from and start the install?  I mean like how you can copy the i386 directory off of the windows CD and then boot into DOS and start the install from the command line?  Is there a way I can copy files to the laptop hard drive if I hook it up to my other PC via a USB to IDE device (which I have), and do the equivalent of that?  Not sure I'm making sense but the laptop most of the time can't correctly read from the CDROM drive, won't boot from USB ANYTHING, has no floppy and no internet access.  But I CAN take that hard drive out and make it a secondary drive on another working Ubuntu PC and can I then set it up from there to start an install once I place it back in the laptop??

---

### Post by LinuxFan999 on 2012-04-09
Deleted post.

---

### Post by ajgreeny on 2012-04-09
This thread may help you.  It explains how you can boot a live system from an iso file on hard disk.  I presume it is then possible to use that live system to do a proper full installation, but I've never tested out the possibilities for myself.

---

### Post by David Andersson on 2012-04-09
Try to do a normal install of Ubuntu onto the laptop hard drive while it is in the desktop computer, and then move the hard drive back to the laptop. It usually works to move systems between desktop computers with the same processor generation. If a desktop and a laptop are too different, I don't know, but you can try. Anyway, avoid installing/configuring hardware drivers while in the desktop computer. You may want to remove all other hard drives in the desktop computer while installing, to avoid confusion/mistakes.

---

### Post by rattking on 2012-04-09
yes. look into debootstrap.

---

### Post by nonamedotc on 2012-04-09
I have switched hard drives with ubuntu installed between different hardware in the past. Generally works well. If you have a USB slot, try liveusb.

---

### Post by petermg on 2012-04-09
> **ajgreeny said:**
> This thread may help you.  It explains how you can boot a live system from an iso file on hard disk.  I presume it is then possible to use that live system to do a proper full installation, but I've never tested out the possibilities for myself.

COOL!... but what thread?  Did you forget to post the link?

---

### Post by ajgreeny on 2012-04-10
> **petermg said:**
> COOL!... but what thread?  Did you forget to post the link?
Yes, I did. Stupid me!

Here you go.  Good luck.
[http://ubuntuforums.org/showthread.php?t=1838959](http://ubuntuforums.org/showthread.php?t=1838959)

---

