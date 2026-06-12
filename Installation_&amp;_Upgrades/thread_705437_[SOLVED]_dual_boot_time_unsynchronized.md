---
title: "[SOLVED] dual boot time unsynchronized ?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by -random on 2008-02-23
Yosh.. so..

I have Ubuntu32bit and Ubuntu64bit (both gutsy gibbon) and Windoze Vista/Longhorn on my pc, and the time's in each of them are different.

When I configure the time in one o/s, the time is out in another o/s.

I've checked out [http://ubuntuforums.org/showthread.php?t=49022](http://ubuntuforums.org/showthread.php?t=49022)
and 
'Open a command prompt. Type sudo gedit /etc/default/rcS
Change UTC=yes to UTC=no' & 'sudo /etc/init.d/ntpdate restart' didn't work.

Any ideas to get my time synchronized in all 3 o/s plz?

---

### Post by -random on 2008-02-24
Ok.. how about if i ask if someone knows how to change the system time, without changing the bios clock?:confused:

- - - never mind that.. (i'm still curious though)

I adjusted my time in the bios, then when i booted up rigt-clicked on time > prefrences > use Utc.

solved! :D

lol.. if i could thank myself here, i would ;P

---

