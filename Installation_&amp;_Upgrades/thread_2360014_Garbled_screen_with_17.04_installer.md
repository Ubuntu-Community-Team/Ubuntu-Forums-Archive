---
title: "Garbled screen with 17.04 installer"
date: 2017-04-30
forum: Installation &amp; Upgrades
---

### Post by Explodinglemur on 2017-04-30
When I boot from the 17.04 desktop installer, all I get is this garbled screen for about a minute, then the video output goes blank and the monitor goes to sleep. [https://imgur.com/a/YLAfz](https://imgur.com/a/YLAfz)

---

### Post by Bashing-om on 2017-04-30
Explodinglemur; Hello;

 A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a 
               black screen or show corrupted splash screen. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use 
               this parameter

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Explodinglemur on 2017-04-30
nomodeset fixed it (though 1024x768 looks REALLY odd on a 21:9 screen :) )

---

### Post by Bashing-om on 2017-04-30
Explodinglemur; Hey.

That nomodeset was just to get ya booted . now ya want to install the proprietary driver ( Additional Drivers ) .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

