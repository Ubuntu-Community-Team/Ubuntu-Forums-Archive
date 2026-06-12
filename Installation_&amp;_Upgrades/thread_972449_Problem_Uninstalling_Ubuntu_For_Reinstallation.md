---
title: "Problem Uninstalling Ubuntu For Reinstallation"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by vincentjames501 on 2008-11-05
I'm having a very interesting problem trying to uninstall my unbuntu partition... I messed up Ubuntu and wanted to reinstall it first by fully uninstalling it.  

I had ubuntu x86 8.10 beta and I installed it on my windows vista x64 from within windows.

First, I went to add/remove programs and removed ubuntu.
I then rebooted and the option to boot into ubuntu was still there (along with windows).

I then proceeded to fix my mbr.  I've tried everything here!  I've booted w/ my vista disk and used bootrec /fixmbr which it said completed successfully but the option to boot into ubuntu was still there.  I have used EasyBCD, MbrFix.exe, and Super Grub Disk (fails).

Still the option to boot into ubuntu is present.  I have also gone to Disk Management and the only thing present is c: drive and not a ubuntu partition.

Stupidly... I went to my C:\ in windows and just deleted the 30GB folder of ubuntu and then tried again to fix my mbr.

STILL i have the option to boot into ubuntu (even though it wont boot into ubuntu)

I just tried gparted and that also failed.  I used a live cd and tried two different options on the disk and it said somethin along the lines of killed kernal.

Any Other Suggestions?

[http://i34.tinypic.com/fe1gmb.jpg](http://i34.tinypic.com/fe1gmb.jpg)
[http://i38.tinypic.com/ru4mx4.jpg](http://i38.tinypic.com/ru4mx4.jpg)

---

### Post by cariboo on 2008-11-05
Have a look here for a howto on editing the Vista bootloader menu:

[http://www.flexbeta.net/forums/lofiversion/index.php/t8373.html](http://www.flexbeta.net/forums/lofiversion/index.php/t8373.html)

Just remove the Ubuntu entry from the menu.

Jim

---

### Post by vincentjames501 on 2008-11-05
God i love you thank you!  That worked like a charm.

---

