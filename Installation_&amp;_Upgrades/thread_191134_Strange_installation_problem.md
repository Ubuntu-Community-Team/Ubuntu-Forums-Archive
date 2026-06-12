---
title: "Strange installation problem"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by seshomaru samma on 2006-06-07
Been running into problems installing dapper on this machine at work. It is a dual boot Breezy/XP . I used a CD which I know is good cause I install Dapper on another machine with it.
Anyway , when the CD boots I chose the first option (I tried the second with same results) which is something like “start Ubuntu and install” (can’t remember the exact wording), a screen comes up with the Ubuntu logo which says “mounting disc partitions” for about 5 minutes. Then the screen turns black it says “decompressing linux…Ok loading the kernel” (or something similar…) and then I get an error :
```
&#12304;4294860 &#65293;624000&#12305; Buffer I/0 error on device hda, logical block 1 
```
The screen then slowly fills with similar errors except the numbers change.
Any advice?

---

### Post by Flyn on 2006-06-07
Erm.
Try disabling DMA? 
Look around the CMOS setup for any other settings that might cause problems.
Also, googling with the error message might provide some more info.

---

