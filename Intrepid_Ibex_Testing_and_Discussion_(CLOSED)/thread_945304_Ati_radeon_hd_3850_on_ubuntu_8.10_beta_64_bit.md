---
title: "Ati radeon hd 3850 on ubuntu 8.10 beta 64 bit"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Eugen184 on 2008-10-12
When ubuntu starts it says i need to reconfigure the graphics setins.I chose to start with low graphics mode.After that i install the fglrx kernel module but when it loads it says "The flgrx kernel module is loaded.This can be obious" and i have to start low graphics mode again.
I have an sapphire 3850 ultimate.Please help:(

---

### Post by drfanatic on 2008-10-15
Hello,

same problem here. The Xorg in 8.10 is not compatible with the fglrx driver. Set "radeonhd" as driver in your xorg.conf.

MfG
DrFaNaTiC

---

### Post by overdrank on 2008-10-15
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by NullHead on 2008-10-15
According to [this](http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1) you should be able to "sudo apt-get install xserver-drver-fglrx" and you "*should*" get video working in ibex. 

I haven't tested it, but it's worth a shot.

---

### Post by inportb on 2008-10-15
Right; AMD released a working fglrx yesterday.

---

