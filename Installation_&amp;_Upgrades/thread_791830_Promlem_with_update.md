---
title: "Promlem with update"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by rBGH on 2008-05-12
I intend to have a duel boot system with HH and XP. I have used Gparted to create the partitions I think I will need

EXT 3 /boot  47.07mb     41.10 used
Swap         1004.06
EXT3  /      6.83        3.47  used
EXT2  /home  448.13      7.28  used

ntfs  /media/sda5        for windows      9.77

When I try to update HH, I get this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

I wonder if my boot is too small? 
Any help is appreciated.

---

### Post by dstew on 2008-05-12
Yes, it may be too small. Usually 100 or 200 MB is used. If the update wanted to install a new kernel, there is probably not enough room. But, did you run the **dpkg --configure -a** command as recommended?

---

### Post by rBGH on 2008-05-12
Yes, and it made a reference to there not being enough room. I don't understand all of the terminology so I had to kind guess as the what was meant. I will use Gparted and change the partitions, I hope for the last time.

Thanks, and here's a tip for you. Put lemon in your Hef>no lemon.

---

