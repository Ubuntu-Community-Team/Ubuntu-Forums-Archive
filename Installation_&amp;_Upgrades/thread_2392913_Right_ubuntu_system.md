---
title: "Right ubuntu system"
date: 2018-05-27
forum: Installation &amp; Upgrades
---

### Post by bluesbird2 on 2018-05-27
PC-Daten
 3,9 GiB
 Prozessor Intel Pentium (R) D CPU 3.4 GHz x 2
 Grafik Intel G 41 x 86/MMX/SS E 2
 Typ Betriebssystem 32 Bit
 Datenträger 291 GiB
 Momentan Ubuntu 16.04 LTS
 
 


 
 Dear community,  
 
 
 could you help me with one question? I need to know, which ubuntu system would be best to use for a pc with the above mentioned detrails.
 I have massive problems with the system, it crashes all the time, the browsers crash and i often can not install things. Is it needed necessarily to install a 32-Bit-programme?
 
 
 Thanks you!

---

### Post by kerry_s on 2018-05-27
you might want to try elementary os
[https://elementary.io/](https://elementary.io/)

where it says custom put 0 & click download.

---

### Post by TheFu on 2018-05-27
If things are crashing, there is probably a hardware issue. I'd check the GPU, power supply, disk controller, disk cables, and any storage. I'd check the RAM first.  Use memtest and let it run at least 12 hrs.

After you solve the hardware issue, I would install one of these:
* ubuntu-mate
* Xubuntu
* Lubuntu
That order is in heaviest (still lite) to lightest.  Mate should work fine on that system.

To figure out the hardware issue, check the system logs.

---

### Post by bluesbird2 on 2018-05-31
Thank you!!

---

### Post by bluesbird2 on 2018-05-31
Thank you very much!  I am glad to get some good help and advice, i will try it out! Thank you for bothering about a beginners problem!!

---

### Post by Autodave on 2018-05-31
Crashes, especially when browsers are running: my first thought was already mentioned: run a memtest.  Second thing I would look at is CPU overheating. Check to make sure fans are running. Make sure that there is no dust plugging the cooling fins on the CPU cooler. Also make sure that the power supply inlet is clean and that that fan is operating.  If the computer is in a hot climate, you could also try removing the side cover and running it that way to see if it helps. If that does help, then you need to figure out why it isn't getting enough cool air through the system.

---

