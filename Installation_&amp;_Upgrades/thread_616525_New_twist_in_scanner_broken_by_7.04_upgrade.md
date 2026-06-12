---
title: "New twist in scanner broken by 7.04 upgrade"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-11-18
I previously posted a problem where upgrade to 7.04 broke my usb scanner. Well I found out the scanner would still work. But, just took a damn long time the first time you use it. 

I tested again and entered scanimage -T, the scanner made some noises and just hung. I left it alone and lo and behold about 4 to minutes later the scanner started and completed the scanimage command ok. I then could use xsane also.

So what is causeing the long delay the first time?
The scanner is a Canon FB630U.

999alfred

---

### Post by torgrot on 2007-11-18
They made some change to the USB drivers that causes the problem with scanners.  Basically, they turn the port off to quickly.  If you upgrade to 7.10 your scanner will work fine.  I also believe there was a patch late in the life cycle of 7.04 that fixed the problem.  I don't remember now.  I have the same scanner and ran into this same problem, but now on 7.10 and it works fine.

torgrot

---

### Post by 999alfred on 2007-11-18
Upgrade to 7.1. Isn't that the version eveybody is calling Bugtsy instead of gutsy?

999alfred

---

### Post by 999alfred on 2007-12-07
Well, updated to 7.10 and I STILL HAVE THE PROBLEM.Run scanimage -T and it might sacn and it might not and it may start scanning after waiting an indeterminate amount of time.

So, how do I get it to work???

999alfred

---

