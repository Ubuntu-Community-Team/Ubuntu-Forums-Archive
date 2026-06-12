---
title: "[SOLVED] xubuntu install question"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by shalemjale on 2008-04-04
I read that Xubuntu was the OS to install on older systems. The computer in question has  about 128 Mb RAM  w/ a 500 MHz celeron processor. Current OS winXP. My goal is to overwrite the entire xp OS.

Have tried to install it from a .iso disc but it takes forever & never gets past 3% loading the Kernel before it asks to reboot.

Is this possible on that computer? Suggestions?:-k

---

### Post by Rocket2DMn on 2008-04-04
It's possible the disc is corrupt, or that your computer just doesn't have enough memory to run the LiveCD.  I would suggest using the alternate install cd, which is a text based installer - it is very easy to use, and doesn't load a live session before you install.  Choose your location from [http://www.xubuntu.org/get](http://www.xubuntu.org/get) then select the alternate install cd (below the desktop cd).

---

### Post by shalemjale on 2008-04-07
Thanks Rocket2DMn,
The text version worked fine but with one hitch....the install did not pick up the internet connection.
Anyone have clues as to the method for approaching this problem?

---

### Post by Rocket2DMn on 2008-04-07
Wireless is still one of the biggest problems in linux.  You should search the forums for posts regarding your specific wireless card.  I'm not very good with getting wireless setup, you really gotta get feedback from people who have used or setup your card.  For example my intel ipw2200 worked out of the box on my laptop, and I am still working on getting my Broadcom 4318 setup in Hardy Heron on a desktop without an internet connection.
Run a forums search (make a bona fide attempt to solve your problem), then if you still don't have it, make a new post and somebody with that knowledge will help you out.

You should be able to find your wireless card in the output of
```
lspci
```
Good luck.

---

