---
title: "Partitiong Help"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by xamlah on 2008-06-16
Hey people!

I just reinstalled Hardy on a 20GB harddrive... after the previous one crashed! I was wondering what would be the best partitioning scheme for my system. The specs are:
HPNX6320
Intel Core2Duo T7200 2.0GHz
20GB external HHD for Hardy
1 GB RAM


Plaese?
Thanx!

---

### Post by wpshooter on 2008-06-16
Are you saying that you have 20gb of available hard drive space on that system or that the hard drive is only 20gb in total ?

Or did you mean 200 gb ?

O.K., sorry, I did not notice that word external.

I would partition it as follows:

/ = root - make 8gb - filesystem ext3
/home = home - make 11gb - filesystem ext3
/swap = swap - make 1gb - filesystem swap

Good luck.

---

### Post by xamlah on 2008-06-18
Thanx a lot!
I will try to do that! I can create mountpoints with Gparted...right?
I have used Ubuntu beofre on the same system for testing purposes... The performance in terms of speed and everything else was superb. BUt after the last install the perfpormance has gone really down.

Thanx again!
Will update u on the latest!


Cheers!
Peace!

---

