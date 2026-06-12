---
title: "Live CD fail."
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by celles on 2008-10-12
I'm no stranger to wrestling with weird live CD problems (like the 64 bit version of 7.10), but this one is really stumping me.

I today downloaded 8.04.1, burned it to disc nice and carefully on good media, and tried to run it on my desktop.  No dice; after going through the usual boot sequence, when the screen blanks and should go to the desktop it merely remains blank and the system just sits there (no CD or HDD activity) until I hit the reset button.

This is bizarre to me, because my desktop in its *current configuration* has successfully (and without hassle) booted an 8.04 CD before...  :confused:

I've tried everything that I can think of (keep in mind that I'm pretty noobish at Linux); burned a new disc, no soft boot, safe graphics mode, safe graphics mode and no soft boot, install instead of 'try Linux'.  Nothing works, despite everything looking A-OK in the boot.  I even tried the Gparted live CD, and THAT boots properly.

So, what gives?

My system config:

AMD Athlon 64 x2 4200+
2 GB RAM
Radeon HD 4870
SATA primary HDD, data drive, and DVD burner
IDE (slave) DVD burner
Vista Home Premium (64 bit version)

Many thanks in advance.

---

### Post by Pumalite on 2008-10-12
Maybe a bad burn. Do md5sum on the iso, burn at 4x or less, check CD integrity before install, clean the lens in your burner. Do not use CD-RW

---

### Post by celles on 2008-10-13
By burning it 'nice and carefully' I do mean slowly and on good quality media.  I should also have pointed out that the same CD boots properly on my laptop.

---

