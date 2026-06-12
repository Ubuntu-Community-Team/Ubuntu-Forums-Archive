---
title: "What is wrong in Hardy and Nvidia?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2008-05-01
As I look through the threads here, I am finding a lot of people have difficulty configuring Hardy and Nvidia.  I just upgaded on my desktop from Gutsy, and it is wreaking havoc with my display.  I never had any problem like this in any previous version of Ubuntu, but I can see I am not the only one.  

I have an Nvidia Geforce 5500 for which I have been using the 169. driver (latest) in Gutsy.  I have a Samsung Syncmaster 19" LCD monitor.  Hardy failed to recognize either of them.  If I install the restricted driver from the Synaptic, it will only accept resolution of 800X600, and the installation of the driver through EnvyNG does the same thing.  I have not found a solution, but I know others are experiencing the same issue.

If anyone has found a solution, I would sure like to know about it.

Any help is appreciated.

Bob

---

### Post by bobnutfield on 2008-05-01
Sometimes I do some really stupid things, and this is one of them.  I upgraded to Hardy, complained about Nvidia not working when all I had to do was make sure I was booting into Hardy's 2.6.24-16 kernel instead of the leftover Gutsy 2.6.22 kernel.  Once I edited my Grub menu.lst file, everything worked perfect.

Maybe my studity will help someone else check this out when they find that Nvidia doesn't work.

Bob

---

