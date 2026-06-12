---
title: "Reinstalled Ubuntu 10.10 now laptop won't boot"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by mkstallings1 on 2011-04-13
I have a laptop with two hdds.  Winsows XP is loaded on the first, and I used the second hdd to play around with linux distros.  I had Linux Mint and Zorin installed on the second hdd and everything was working fine.  I decided I wanted to go back to Ubuntu 10.10, so I installed it to the second hdd, overwriting everything on it.  Everything seemed to go fine, but when I went to restart from the install, I got some sort of I/O error and since then my laptop wont boot at all.  I have tried telling it to boot from different hdds n the Windows BIOS.  I have also tried 2 different live dvds of Ubuntu 10.10, all to no avail.  All I get is a blank screen with a flashing cursor.  Please help.

---

### Post by mkstallings1 on 2011-04-13
Alright, I burned yet another live dvd and now I can boot with that.  One problem solved.

---

### Post by mkstallings1 on 2011-04-13
I got it figured out.  Seems that Grub2 was not installed on the second hdd.  I just reinstalled it and now I have my machine back.

---

