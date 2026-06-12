---
title: "Unable to run &quot;make&quot; in hardy"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by mhedges48 on 2008-07-11
Hello,
Since I've upgrade to Hardy, I cannot make/install anything. I have tried installing several things (madwifi and ndiswrapper for example) and always get the same error:

""
make[1]: Entering directory `/home/matt/My Documents/Code/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/matt/My Documents/Code/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** No rule to make target `Documents/Code/ndiswrapper-1.53/driver'. Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/matt/My Documents/Code/ndiswrapper-1.53/driver'
make: *** [all] Error 2
""

I believe I have installed all necessary packages, and again I didn't have this problem in Feisty or in Gutsy.

uname -r shows 2.6.24-19-generic


Please help solve this problem.

many thanks
Matt

---

### Post by Rallg on 2008-07-11
Do you need to run ./configure first? Yes, I know you've compiled things before, but once in a while we forget stuff...

May I ask, do you want ndiswrapper in order to make a wireless driver work? It may be that you don't need to do it, in Hardy. My wireless needed ndiswrapper in Gutsy, but Hardy has the problem solved (it detects a missing driver, and instructs you to download it via cable, without needing to compile ndiswrapper).

I have successfully compiled some other things in Hardy. Can't say I've done it in kernel -19, though.

---

### Post by mhedges48 on 2008-07-12
Thank you... but ./configure is not needed; the instructions (and how I've done it previously) start just with the "make" but now I get the error I previously posted... 

Hardy detects my wireless fine (Atheros Communications Inc. AR5418 802.11abgn Wireless) but doesn't run it (in Network Settings there is just Wired Connected and Point to Point in Network Settings)...

---

### Post by Pumalite on 2008-07-12
Have you tried installing automake and autocof?

---

### Post by mhedges48 on 2008-07-12
Thank you. I do not understand the logic of this, but I moved the installation folder to the Desktop, and did the Make, and it ran fine!  I wonder if the fact that originally it was in a folder with two words (My Documents) through it for a loop????

---

### Post by mc4man on 2008-07-12
> I wonder if the fact that originally it was in a folder with two words (My Documents) through it for a loop???? 
you can see it right here
> make[2]: *** No rule to make target `Documents/Code/ndiswrapper-1.53/driver'. Stop.

---

