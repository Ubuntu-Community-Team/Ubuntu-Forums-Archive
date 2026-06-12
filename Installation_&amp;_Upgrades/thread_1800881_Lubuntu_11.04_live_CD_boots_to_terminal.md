---
title: "Lubuntu 11.04 live CD boots to terminal"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Cpierce on 2011-07-09
Heard good things about Lubuntu 11.04 so I downloaded the .iso and burnt a CD to have a peek. When I boot up on the CD and choose "Try Lubuntu" the splash screen shows up then it jumps to command line. I tried startx, but it didn't work.

Can someone help me ?

---

### Post by Peadogie on 2011-07-09
I had the same problem. The way I got it to work was to chose 'Install Lubuntu'..... then quit the installer..... that brought up the desktop.

A crazy workaround, but it worked for me. 

Later I installed Lubuntu with no problem.

Hope this helps.

---

### Post by VanR on 2011-07-09
I had to press F6 repeatedly to get to a desktop.

---

### Post by Cpierce on 2011-07-09
Thanks Guys, I will try this. Seems like it should work properly, but oh well. I do love Lubuntu on the older computers. 

Someone must know a fix. I may just install in virtualbox to take a peek.

---

### Post by mörgæs on 2011-07-09
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by Noob672 on 2011-07-13
I have the same problem, i.e. the official Lubuntu Live CD boots to the command-line. I tested it on a desktop PC with 2 GB of RAM, and a modern video card (Radeon 5770).

The following command works for me:

$ sudo lxdm

Does it work for you?

I'm not sure why the Live CD doesn't boot straight to the graphical environment.

Regards.

---

