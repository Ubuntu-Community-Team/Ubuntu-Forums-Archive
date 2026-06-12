---
title: "7 partitions on a netbook."
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by amiejay on 2009-12-29
I have an ASUS Eee PC Seashell 1005HA-PU17-BK, 250 GB HDD.
I'm going to put 3 different linux distros on it, like this:
1) 2 GB - xPUD (very fast booting OS, is pretty much just firefox and a music player) 
2) 4 GB - Puppy Linux (fast and cute, an actual full OS)'
3) 12 GB - *buntu (for when I need something bigger than the 100 MB puppy linux. I'm not sure whether i should use Ubuntu NBR or Eeebuntu NBR or Xubuntu or Eeebuntu LXDE edition...)
4) 40 GB - Windows 7 Starter (for running .exe's and games and testing some programs I'm currently developing for windows--going to branch out into linux, though. It works pretty good in regular ubuntu right now but the background doesn't load and it can't save or load...)
5) ? GB - Windows 7 recover (the built in recovery thing for windows since the netbook doesn't have a DVD drive for a regular recovery disk. I don't know how big Asus's are, or if they even had one. My HP netbook had an 11 GB one, but i returned that netbook and am getting an Eee PC now, and i don't know what Asus does)
 
The 6th partition is just a Fat 32 for storing all of my files and stuff for sharing between all OS's. It'll be 150+ GB, whatever is left.
The 7th will be a 2 GB swap partition.
 
I'm testing this out on a virtual machine first, but just with a 40 GB HDD on the virtual machine, and it will look like this except with larger sizes:
i49.tinypic.com/10y124h.png
 
Order of partition matters, right? The things that are first run faster? If so, the order will be just like in the screen shot:
Windows first, it needs the extra speed....then Ubuntu, then puppy, then xPUD, then all of my files, then the swap, and lastly, the recovery. I probably won't use the last 2 parititons very much since i don't really expect to hibernate or run into a problem, and if i do, then the performance different will be pretty negligible for just that once that it's accessed.

---

### Post by amiejay on 2009-12-29
So...I can just do a frugal install of puppy and xPUD onto my ubuntu partition, so it'd only need to be:
Windows 7
*buntu/pupp*/xPUD
Files
Swap
Recovery
 
or would a separate partition for each be more efficient?
I'm never going to fill up this HDD btw. I could be fine with a 10 GB files partition. I've always only used about 20 GB or so, INCLUDING a Vista or 7 installation, on my PC's (hence why a netbook is ideal for me. I pretty much just do software development and web browsing).
But then i got into games and my bro got a steam account so now i'm using 80 GB on THIS computer, but i won't be playing too many games on the netbook, and those would be part of the 40 GB windows partition anyways....
 
* The asterisks shows that i'm unsure still whether to throw on Eeebuntu or Ubuntu / Puppy or Puppeee Linux

---

