---
title: "Just a question before installation.."
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Floatingclouds on 2011-05-23
So..., I used Wubi to do the install and pointed it to D drive because it was basically free except for itunes... anyway, once it had finished, I turned off my laptop, turned it back on and it showed Windows and Ubuntu, I loaded Ubuntu and it said it was continuing installation, anyway it said copying files, and stuff and I didn't know if it was overwriting vista so it would go on the C drive instead of the D drive. Anyway, I just want Ubuntu on D and Vista on C.
Is Ubuntu gonna' overwrite Vista? :-s

---

### Post by linuxinstalledfromhdd on 2011-05-23
I have never used Wubi to install Ubuntu.  So I would wait for someone else to comment.  I think best way to do it however it from a disc or live usb bootable stick of Ubuntu.  If you want information on that you can find it out here:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Hang in there while someone gets to your question..

Bump

---

### Post by Floatingclouds on 2011-05-23
Yeah, my 4 gig stick broke and I have no cds at the moment, it's working though and is at the stage of finally installing, I just want to make sure that if all the files are in d then they won't do anything to anything in c because vistas on it.

---

### Post by prshah on 2011-05-23
> **Floatingclouds said:**
> 
Is Ubuntu gonna' overwrite Vista? :-s

Nope. If you have chosen a wubi install, it will not disturb your "drive c" (Windows) partition at all.

---

### Post by Floatingclouds on 2011-05-23
Oh, okay Thanks :)
Off to install Ubuntu :)

---

### Post by sanderd17 on 2011-05-23
Wubi makes a file with the specified size. That file is a virtual HDD. So Ubuntu will only touch one file at all. 

The advantage is that you don't have to repartition, the disadvantage is that extra layers of virtualisation make your computer slower. This is only a virtualisation of your HDD (which is always slow) so that's not such a disadvantage.

As a second thing: Wubi trusts in windows to boot itself. The first part that gets loaded before you choose an OS is a part of windows. So if windows crashes, then Ubuntu won't be bootable either. In regular installations, the first part you load is a part of Linux (it's called GRUB: GRand Unified Bootloader) which will only boot windows if you choose to. Likewise, if Linux crashes badly, you can't boot windows either. But you can reinstall GRUB without having to reinstall the whole OS.

These are the differences between WUBI and an regular installation in terms of stability and speed.

---

