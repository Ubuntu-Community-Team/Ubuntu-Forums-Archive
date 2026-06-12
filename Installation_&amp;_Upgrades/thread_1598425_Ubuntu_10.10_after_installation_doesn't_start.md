---
title: "Ubuntu 10.10 after installation doesn't start"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Dsky on 2010-10-16
After the installation (tried 2 times) ubuntu doesn't start... it freeze with the ubuntu word in the middle of the screen....

What can it be?

Thanks

---

### Post by Dsky on 2010-10-16
up...

---

### Post by mörgæs on 2010-10-16
Bumping your thread within one hour is completely unnecessary and will only annoy people who would otherwise help you.

---

### Post by Dsky on 2010-10-16
i'm sorry.. you're right...

do you think i've to try installing the 10.04 ?

---

### Post by Dsky on 2010-10-16
noone can help me? pls

---

### Post by arpanaut on 2010-10-16
Please give us some more information

What are the specs of your 'puter?
What method did you use to install?
Did the Live-CD work, Did you use wubi?

Without  further info none of us will be able to help you!

---

### Post by Dsky on 2010-10-17
i've a Toshiba M40-282, with Ati x700.. maybe thats the problem?

i'm such a noob so i installed it normally... :)

---

### Post by Dsky on 2010-10-17
the /etc/X11/xorg.conf i could try to edit it's empty...

---

### Post by Dsky on 2010-10-17
sudo startx

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
xinit:  Server error.



im now using the xorg.config.failsafe data in the xorg.config

---

### Post by kansasnoob on 2010-10-17
> im now using the xorg.config.failsafe data in the xorg.config


So, does that allow you a gui desktop?

If so go to System > Administration > Additional drivers and see if it finds the ATI driver for your GPU.

---

### Post by Dsky on 2010-10-17
it tells me that there aren't proprietary drivers..

---

### Post by Dsky on 2010-10-17
up

---

### Post by Dsky on 2010-10-17
have i to try another distribution?

---

