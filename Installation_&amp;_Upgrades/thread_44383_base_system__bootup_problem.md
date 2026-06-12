---
title: "base system / bootup problem"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by albar129 on 2005-06-25
Hi,
I downloaded the .iso file ... burned it on cd and tried to install it on my hard drive ... I have one HD with two partitions ... a windows xp is running on one partition .. when i inserted the CD, in partitioning step i deleted the other partition and made a new partition out of the resulting free space (about 15GB)...
so everything went fine... until it went to next step: base system installation.... during the process it counts up to 6% .. stops.... and then an error message indicates that it cannot continue this step and it suggest that I should burn the cd in lower speed .... 
Now the problem is that I have burned 4 cds with different speeds but they all fail in base system installation step ... 
and the other problem: after aborting the setup, when I restart the computer windows does not boot up ... it appear that it finds bootable sector on IDE0 (hd) but  then nothing happens ...

Plz help ...  I'm so desperate ... :???:

---

### Post by TristanMike on 2005-06-25
Hi, don't know if I can be of much help, but when burning the cd, it must be burned as a bootable cd (done I take it), and if it's a speed issue, from my experience, 2-4x will pretty much ensure a proper burn.  If you've done all this, I sorry I couldn't be of more help.  Maybe someone else can help.
TristanMike

---

### Post by C.B. on 2005-06-26
Had some install problems too. Though I was installing to a second HD and not repartitioning an existing Windows HD. Anyway, some things you might try are:

1. Double-check you've got the download right. Even if you think it's okay, maybe take another look at [www.ubuntulinux.org/wiki/BurningIsoHowto](www.ubuntulinux.org/wiki/BurningIsoHowto) -- esp.  "Burning/writing an .iso Image to CD with Windows XP."
2. Definitely CheckSum is worth using to see if there is a faulty file tucked in there somewhere.

If CheckSum looks right you might just try putting the same install CD in again. Not sure, but if I remember right this may have happened to me: install stalled at some point with "reburn at slower speed" error message. By that time I had done a couple of burns and had run CheckSum so knew the CD was okay. I think I just turned machine off, put in same CD and it worked okay second (or third?) time around. Go figure?!?

And make sure your internet connection is working too, because I think Ubuntu won't install properly if it isn't. Someone correct me here if I'm wrong.

CAUTION: I'm new to Ubuntu too. If you get better/conflicting advice from s.o. more experienced, go with that.

Good luck.

---

