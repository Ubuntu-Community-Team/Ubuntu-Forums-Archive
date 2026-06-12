---
title: "How to restore GRUB"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by polloz on 2006-07-07
hello,

i have the following problem. i did a clean install of dapper, everything went ok. when i was partitioning the hard disk, i left a ntfs partition for installing windows xp later on. so after using ubuntu for a while, i decided to install windows xp on the partiton a left for it. once i installed it, everytime i reboot my machine it loads windows xp atomatically without showing me the GRUB boot manager. because of this, i can't load to ubuntu :( 
i guess this problem is because when i installed windows xp, during the instalation the MBR was erased, so GRUB was erased too.
how can i restore grub so i can choose which OS to load? help please, i'm stuck!

thanks

---

### Post by scxtt on 2006-07-07
the command you're looking for is grub-install ... boot to your LiveCD and you should be able to run it from the live environment ... you should probably read the man-page or some other research ...

---

