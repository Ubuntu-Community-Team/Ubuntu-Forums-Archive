---
title: "[SOLVED] Fomatting and Erasing EVERYTHING - fresh install"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by bmdavis on 2007-12-05
Hi all,

     About 4 months ago, I switched from XP to Feisty Fawn and have loved it.  I need to keep XP for some games and programs, but otherwise I've used 7.04 90% of the time.

     Now, I'm considering starting over with a fresh install. I won't go into details as to why, but it's what I've decided to do.

I would like to 

1 - Format / Erase the whole hard drive on my Inspiron 6400 laptop

2 - Install XP first.

3 - Install Ubuntu 7.04 second. 

      My biggest question is concerning #1.  What is the best way to do this?   Also, is it dangerous to do (I have everything backed up).  last time I can remember formatting a drive was when I had win98, so I'm not sure what changes have been made.

All advice is welcome, I would love to seriously get a fresh install of both and I have the discs to do it.

Thanks.

---

### Post by Pumalite on 2007-12-05
Use Gparted Live CD. The best partitioner around.

---

### Post by bmdavis on 2007-12-05
so you think I should run the LIVE CD, erase all partitions on that, and then do a fresh install?

Will it be difficult to reinstall XP after that?    

Also, what about DBAN ([http://en.wikipedia.org/wiki/DBAN](http://en.wikipedia.org/wiki/DBAN)).   I wonder if Gparted actually erases everything or just formats.

---

### Post by Pumalite on 2007-12-05
As difficult as Micro&%$ can be. Boot from Gparted and make one large partition of your whole hard drive formatted ntfs. Then install XP. Boot from Gparted again and resize your XP partition. Then install Ubuntu.
You can make 2 partitions from the start, but I've had best results with the first method.

---

### Post by bmdavis on 2007-12-11
Gparted did the trick.   A very good suggestion to do XP first, exactly what I had wanted.


Thanks!!

---

### Post by Pumalite on 2007-12-11
You are welcome. Good luck.

---

### Post by Doug11 on 2007-12-11
Pumalite's method worked great for me too. Very simple to do and with no complcations. For the amount of people trying to do this, should almost be a sticky.

---

