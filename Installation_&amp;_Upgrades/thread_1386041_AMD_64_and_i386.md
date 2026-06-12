---
title: "AMD 64 and i386"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by myzonez on 2010-01-20
Acutally, I'm looking for an answer to this thread:
[http://ubuntuforums.org/showthread.php?t=1386022&highlight=xubuntu+internet](http://ubuntuforums.org/showthread.php?t=1386022&highlight=xubuntu+internet)

But now I suspect that my problems are a result of installing a 64-bit OS.
The file I downloaded from the Xubuntu australia server was :
[xubuntu-9.10-desktop-amd64.iso]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/9.10/release/xubuntu-9.10-desktop-amd64.iso")

and my processor is AMD-sempron.
and When I was running the live CD, I got the following error message :

"XFCE volum Daemon closed unexpectedly"

and

"There is a serious error with your Kernel" 

and something like that....
I ignored the warnings and isntalled it in my system. As u can see, no internet or sound!
I suspect because its designed for amd64, and I should have used i386.
I have used uname -r in every distro I've used in the past few years and they say "unknown" about the CPU architecture.
Can somebody explain to me what this i386 and AMD 64 is all about? Mine is AMD sempron (its 64 bit) and still the it won't work on mine? 

And maybe I should do a reinstallation after downloading this file:
[xubuntu-9.10-desktop-i386.iso]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/9.10/release/xubuntu-9.10-desktop-i386.iso")

---

### Post by wojox on 2010-01-20
AMD Sempron is I believe a 32 bit processor. Download the i386 and you shouldn't have any problems. Post back if you do. [http://en.wikipedia.org/wiki/Sempron](http://en.wikipedia.org/wiki/Sempron)

---

### Post by oldos2er on 2010-01-20
"XFCE volum Daemon closed unexpectedly"

and

"There is a serious error with your Kernel"

These errors don't strike me as being related to bitness. Have you run fsck lately? Just a thought. 

"uname -r" will show you which kernel version you're running. If you want to see info on your CPU, run "cat /proc/cpuinfo"

---

