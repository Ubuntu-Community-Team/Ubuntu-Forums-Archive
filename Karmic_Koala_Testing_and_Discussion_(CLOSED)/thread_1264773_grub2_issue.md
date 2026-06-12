---
title: "grub2 issue"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2009-09-12
I installed kubuntu karmic alpha 5 on a UDMA CF.  Works really well on my laptop EXCEPT when grub-update runs, it gives some issue about not finding a device map and changes all of my UUID entries to /dev/sdXY and the XY is wrong if there is another drive plugged in when it updates.

**Just run**

> sudo dpkg-reconfigure grub-pc

---

### Post by berthiggins on 2009-09-12
sounds like my post!

[http://ubuntuforums.org/showthread.php?t=1262246](http://ubuntuforums.org/showthread.php?t=1262246)

---

### Post by maestrobwh1 on 2009-09-12
I pulled out the internal drive when I installed karmic to the CF card so I thought maybe that is why I may have had an issue.  Did you do something similar?  I am somewhat surprised that Ubuntu went away from the tried and true standard bootloader.  I have had some odd quirks with grub-pc.  It also likes to mount an external drive of mine and not release it when it updates.  I can say that is why I do not "trust" it and why I pulled the internal drive from my laptop when I installed Karmic.  

After I dpkg-reconfigured it, it wrote grub.cfg with uuids again.  I was not able to boot easily before I fixed it, and managed to boot by editing the grub entry at boot, changing /dev/sdc1 to /dev/sdb1, then got a boot and figured this out.

---

