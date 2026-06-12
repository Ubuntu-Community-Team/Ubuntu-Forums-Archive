---
title: "Cpu Usage very High after installing Ubuntu Dapper 6.06"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by TheWind on 2006-06-27
Hi To All of you,
So Finally i have upgraded my ubuntu 5.10 to this new version Dapper drake, but since then i have some really big problems to use my computer. Everything it's very slow, whenever i open one or two more windows in Ubuntu or one or more programs, it's really difficult to do whatever even the simpliest things, like closing windows, copying files ecc. I have to say that t the end of the upgrading process i got an error about firestarter, and the process ended without the cleaning part. 
I've made a reboot and everything seemd to be ok, but as i said since than the computer is very slow and the Cpu usage it's very high (100% for minutes), i really can not understand where is all these cpu power engaged? 
I wish i could continue to use Ubuntu and not returning to windows...i hope someone of you can help me with these issue. For example is it possible to make a disupgrade and then do it again without formating the hard disk?
Thank you in advance.

---

### Post by arejensen on 2006-06-27
To help us help you, could you open up a terminal window, execute the top command and post the output here?

---

### Post by zgoda on 2006-06-29
I observe the same effect on nine HP nx6110 (Celeron-M 360J, 1.4GHz) laptops, of which 3 have 256 megs and 6 have 512 megs of RAM. CPU usage stays at about 60% when idle and jumps to over 90% after starting any application. Top output shows that process "lsb_release" eats 20% CPU from time to time then drops to 0% CPU usage. In Gnome System Monitor I see 2 such processes, each labeled as "zombie". Also worth of noting is huge amount of RAM consumed by Nautilus, compared to 5.10 (over 75 megs in 6.06 compared to 35 megs in 5.10). All these machines had 5.10 installed previously and these with 256 megs was somewhat slow, but not sluggish, now they are nearly unusable, while these with 512 megs are sluggish.

I have no idea where to look for possible cause.

---

### Post by zgoda on 2006-06-29
Digging in forums shows possible cause: HAL (in conjunction with current kernel) is polling IDE channels for CD/DVD drive status changes. No resolution as of yet, unfortunately.

---

### Post by Azrael Nightwalker on 2006-07-09
[http://www.ubuntuforums.org/showthread.php?p=942785](http://www.ubuntuforums.org/showthread.php?p=942785)
Here you have a solution to the HAL problem with HP laptops.

---

