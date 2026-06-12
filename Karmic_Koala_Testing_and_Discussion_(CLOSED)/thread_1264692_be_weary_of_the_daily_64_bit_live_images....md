---
title: "be weary of the daily 64 bit live images..."
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by woedend on 2009-09-12
Just a heads up..for the past 5 days or so the daily live 64 bit cd images are a bit of trouble.  As of today, ubiquity is still @ version 1.99.17 which won't let you manually partition the disk.  You can upgrade to version 1.99.18,which at least takes you into the partitioning menu, but any changes I make aren't actually applied.  This can be averted by installing ubiquity ubiquity-frontend-gtk and ubiquity-ubuntu-artwork version 1.99.15...
Another issue is that these don't seem to be "daily images"...it's still shipping firefox 3.5.2, the aforementioned superceded ubiquity, and after install needs about 150 megs of upgrade.  I wonder what's going on...

---

### Post by Podex on 2009-09-12
I can confirm this problem with Ubiquity since I was the one that reported it: [https://bugs.launchpad.net/bugs/427347](https://bugs.launchpad.net/bugs/427347)
I actually noticed that the changes made in the manual partitioner were not shown. I tried to set one partition as root and had it formatted as ext4 but when returning to the partition list it was not listed as one that was going to be formatted. However I just continued and it did actually listed the right partition as the location for the install.

I had a seperate issue however (non ubiquity related) which caused me to try today's alternative ISO instead. I can confirm too that it had to upgrade a few dozen packages when install was finished.

---

### Post by garba on 2009-09-12
thanks for the heads up, run into this issue myself testing the daily iso :(

---

### Post by woedend on 2009-09-12
I don't keep up much with development plans, or ubiquity for that matter, but i'm hoping the latter bug is part of a move to let you mark partition changes without refreshing each time.  I see no real reason why I must wait 5 seconds or so after setting each partition so that it can resync.

---

### Post by DougieFresh4U on 2009-09-12
I have been using an alpha 3 DVD (don't have any blank DVD) to do fresh install the past week and right before partition editor comes I get a box telling me Ubiquity crashed

---

### Post by inportb on 2009-09-14
Yeah, I just saw that myself. Also, if you install using the minimal disc, you might have problems installing the kernel and such.

---

### Post by DougieFresh4U on 2009-09-14
> **inportb said:**
> Yeah, I just saw that myself. Also, if you install using the minimal disc, you might have problems installing the kernel and such.

Actually after seeing that, all installed perfectly and all 4 partitions are there as well.

---

### Post by gmc on 2009-09-14
The 32bit Alternate images are borked too. I tried to do a fresh install from the 13/Sept release and it flat refuses to install.

GMC

---

### Post by Podex on 2009-09-14
It sounds like all of you are experiencing different problems than me. You should file seperate bug reports. Mine was fixed very quickly, yours might be too.

---

