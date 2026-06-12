---
title: "Very old Compaq 8702: can it do it?"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by voided3 on 2006-10-17
Hello all. I have (fortunately not as my only comp) a Compaq Presario 8702 sporting a Pentium 1 @ 200mhz, 72mb of RAM, a S3 Virge integrated video card w/ 2mb of graphics RAM, and a 6 gig hard drive (and yes, it has ethernet). Now brace yourselves, it currently is running WINDOWS XP... and it actually works... on the classic theme with no background. Now, the thing is I would like to put Ubuntu 6.06 on it and only Ubuntu, however the thing can't boot from a cdrom; I got XP on it by putting on Win98 first through the means of a boot floppy to get command prompt. I also cannot access BIOS with any combinations of key strokes (the compaq website said either F1, F9, or F10... none of which worked) to access boot order. So, is there a way I can boot to terminal from a floppy and instigate a full GUI install from the alternate disk, or I am I just being ignorant to the fact that the computer is from 1996? All I have to say is if the thing can run (comparitively) RAM hungry XP, why not Ubuntu? Any thoughts or horror stories from similar attempts would be greatly appreciated. Thanks!

---

### Post by UltraM4n on 2006-10-17
I'm a Newb at this...but i think you need at least 10 gig HD space for the OS itself..and at least a gig of ram..

---

### Post by ivrobi on 2006-10-18
Hi!
Please, take a look at these pages:

[help.ubuntu.com/community/SmartBootManagerHowto](help.ubuntu.com/community/SmartBootManagerHowto)
[help.ubuntu.com/community/Installation/LowMemorySystems](help.ubuntu.com/community/Installation/LowMemorySystems)
[www.ubuntuforums.org/showthread.php?t=262724](www.ubuntuforums.org/showthread.php?t=262724)

Try Xubuntu with the alternate CD, or a server installation of Ubuntu. The requirements are not that huge as mentioned above, but don't expect miracles. 64 MB RAM should be enough to use the installed system (look here: [www.ubuntuforums.org/showthread.php?t=275297](www.ubuntuforums.org/showthread.php?t=275297) ) but go for more memory if you can.

Greetings!

---

### Post by voided3 on 2006-10-20
Yeah, I would have maxed out the RAM on it but I don't feel like spending money on it; the RAM in it now I got for free from my friend (it had 48mb +8mb on borad, now it has 64mb + 8mb on board and it can support up to to 128mb + 8 on board). It runs Winamp, AIM, and Mozilla just fine in Win XP, so i guess it would do it even better in Ubuntu. I'll try out the boot floppy link with Xubuntu, thanks!

---

### Post by K.Mandla on 2006-10-20
You can get by with much less than that. I have a PII-300 that boots to Openbox on less than 22Mb and under 600Mb of disk space. Installing Ubuntu **really **needs 32Mb of memory (I tried it with less -- it wasn't pretty), but after that, you can build a working GUI on very little.

Really the only thing holding you back is the practicality of the system. You can put Ubuntu on a Pentium machine and it will work -- but it tends to be sluggish and ill-suited to the task. 

ivrobi's links are a great place to start. I have a few more in my signature that you might want to look at. Have fun!

---

