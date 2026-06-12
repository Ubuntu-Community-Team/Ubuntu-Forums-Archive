---
title: "Feisty  Bug?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ouellettesr on 2007-04-20
Hello, I have a big problem.

I have a wd 500gb sataII hd. Vista is installed on the first 250 gb of the hd. Today I tried installing the new ubuntu version "feisty" onto the unpartioned space.

I have two major problems. Lets start with the first.

I selected the first option during the install which was the "guided" one. Everything seemed to be going fine until it got to about 70% and then just quit installing. a little pop up in the bottom right hand corner of the screen came up and said that the disk was 100% in use or something like that. 

I tried reinstalling a second time and chose manual partitioning. I noticed how it partitioned the drive and it was not normal, I cant say exactly how it was (bad memory) but i do remember it only partioned off 120 something megabytes for swap.

So I decided to manually do the partitions how I have always done them in the past. when I clicked next it immediately brought up that little popup saying that the disk is 100% in use. Not Good.

So I rebooted.

Heres my second Problem.

During all that partioninig I assume my vista partition was untouched. Obvioulsy grub wiped out my bootloader and it was going to use its own. In my case however ubuntu did not finish installing and it still wont install, so my only option is to fix my mbr so I can at least boot into windows. 

Well, vista has changed the way it lets you fix the bootloader as decsribed on this page [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

, I have tried to /fixmbr, it says successful, but still doesnt work when you reboot. If you try /fixboot it says it cant find a suitable installation for fixing. If you try /rebuildbcd it sees the installation to rebuild and when you click ok, it says it is not a valid installation or something. So basically none of the optiones work.

Now I know my installation is still there, i just do not know how to fix it. I am pretty good with fixig things but this has got me stumped.

Well (20 minutes later) just for shits and giggles i tried installing the older version of ubuntu and everything worked out well. It sees my vista installation and I can boot into it. I definately dont see it as a way of fixing the problem though, because if I cant fix the mbr when I delete ubuntu, what will I do then? I plan on giving ubuntu its own pc one day and at that time I will want to use the whole 500 gb for vista.

I look forward to some insight on this problem , I want to get feisty up and running on this machine.


If anyone is curious here are the specs:

BFG 680i Motherboard
BFG GeForce 7300 GT OC Video card
Patriot 1gb DDR2 Ram
WD 500gb SATAII Hard Drive

:guitar:  Rock On

---

