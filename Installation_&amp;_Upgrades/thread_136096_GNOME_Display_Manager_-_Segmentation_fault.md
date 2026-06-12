---
title: "GNOME Display Manager - Segmentation fault"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by msinger1 on 2006-02-25
Hey guys,

So I recently upgraded from Hoary to Breezy after months of procrastination for fear that it would break.  Well, it broke.

The upgrade initially seemed to go ok.  I think the errors starting popping up after I uninstalled and reinstalled some video progs since my video never worked.  My video started acting funky and the colors were all messed up especially through gXine.  Now I can't boot into X and the following message comes up on boot:

* Starting GNOME Display Manager ...
/etc/rc2.d/S13gdm:  line 40:  5721 Segmentation Fault start-stop-daemon --start --quiet --pidfile $PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1  [fail]

I thought that perhaps something went funky with the NVIDIA drivers so after the boot problems I tried reinstalling them and editing xorg.conf, etc.  That didn't seem to do anything.

Any help would be appreciated.

Thanks. :-k

---

### Post by Xian on 2006-02-25
[QUOTE=msinger1]* Starting GNOME Display Manager ...
/etc/rc2.d/S13gdm:  line 40:  5721 Segmentation Fault start-stop-daemon --start --quiet --pidfile $PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1 [/QUOTE]

I would suggest purging gdm from your system and then reinstalling.

$ sudo apt-get remove --purge gdm
$ sudo apt-get install gdm

---

### Post by msinger1 on 2006-02-25
Xian,

Thanks so much for your expertise.  I spent 4 days Googling and combing the forums before posting this thread and your solution fixed me up in 2 minutes.  Thanks again.

--Mike

---

