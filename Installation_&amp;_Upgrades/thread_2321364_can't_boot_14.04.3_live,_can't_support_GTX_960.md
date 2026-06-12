---
title: "can't boot 14.04.3 live, can't support GTX 960"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by Kris_M on 2016-04-22
it reads in the cd/dvd and then just sits there.

(dvd burned from iso on 12-20-15).

brief: 64 bit system
I wrecked my SSD and have been running win7 for last 3 weeks.
Restored my 3 week old clonezilla to a new ext4 partition (on SSD extended ptn)(where it was before) and used rescatux to try to install grub but it ended with an error.   typing this on win....

In there somewhere i tried to boot 14.04.3 live to have it install grub and then maybe restore the clonezilla image on top of it.  Tried booting as install 14.04.3, also as live.  both just stuck.

Only thing I can think of is it doesn't like the gtx960 I got a week ago and linux hadn't seen it yet.

system is: GA-Z97X-UD3H, i5-4670K 3.5@4.3, Corsair H80i V2 liquid, 8GB ram, 64bit Ubuntu Unity 
14.04.3/64 bit Win7, Sammy 250GB SSD, EVGA GTX 960 4GB, EVGA 850 B2 PSU.

I've been up all night so will not respond to any answers until +8hr from now.
Thanks!   ](*,)

---

### Post by Kris_M on 2016-04-22
added psu info.

---

### Post by Kris_M on 2016-04-22
solved by abandoning Linux.  14.04.3 doesn't support a GTX 960. 16.04.0 is not ready for prime time - got my FF set up and on next boot it would not give me the window.  I have spent a ton of time.  This is old technology.


:icon_frown:

EDIT: hmmmmmm - most of my 16.04 probs (and fedora) were that I didn't really have a primary slot available.  Ubuntu (and fedora) install would stall with no message - finally got an error on ubiquity - google - "storage".  Moved a primary to logical and then install worked fine and put both "/" and swap on logical partitions.

---

