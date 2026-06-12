---
title: "Make a disk image of Ubuntu"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by tkexer on 2010-10-27
I need to make a disk image of Jaunty. Something like Acronis True Image or Norton Ghost in the Windows contingence. I have tried Remastersys and Ghost 4 Linux. The former simply created an ISO file, which is 1/10th of the size of my hard drive and I do not know how to restore my computer using the ISO. The latter seems to be stuck at 0% even after leaving my PC on for 4 hours and verifying that all the settings are correct.

If you know a program like Norton Ghost, but for Jaunty, please let me know.

---

### Post by zeroseven0183 on 2010-10-27
Try [PartImage]("http://www.partimage.org"). The HowTo/Manual is here [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by tkexer on 2010-10-27
Thanks, but how do I even run the program? I downloaded the tarball and extracted it. What's next?

---

### Post by Mark Phelps on 2010-10-27
It's been so long, so I don't really remember what default filesystem Jaunty used, but for future reference, Partimage does NOT work with Ext4 Linux filesystems.

The alternative, which works as well as Partimage, is Clonezilla.  You can get it from the distrowatch.com site.  You download the image, burn it to a CD, boot from that, and can then use that to image off your install in a manner similar to GHOST.

---

