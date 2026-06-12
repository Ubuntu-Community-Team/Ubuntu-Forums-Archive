---
title: "boot hangs after &quot;Running local boot scripts (/etc/rc.local)...............[OK]&quot;"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by marxus on 2007-07-25
Hi
I (new to Linux)  managed to install Xubuntu 7.04 on an old 266Mhz 64MB RAM laptop from alternate install CD copied on hd.
Finally I got it booting, but it hangs after displaying 
"Running local boot scripts (/etc/rc.local)...............[OK]"

Then I found  pressing enter brings a login prompt where I can log on subsequently.

I found in [http://ubuntuforums.org/showthread.php?t=413975&page=2](http://ubuntuforums.org/showthread.php?t=413975&page=2)
there is a known issue about this so changed via sudo vim /etc/event.d/tty1
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1
to
exec /sbin/getty 38400 tty1
respawn

Still, boot just hangs.

Do I miss something here ? Can I start xfce or whatever is missing manually ?

 I've already spent much more time than I wanted on this
- just to replace Windows98 with something created in this millenium...

Thanks for any help !
M

---

### Post by Pumalite on 2007-07-25
If you have integrated video, you have less than 266 MB RAM and therefore the issue might be too little memory. In that case you could try Zenwalk or DamnSmallLinux.

---

### Post by marxus on 2007-07-26
hmmm, in [http://xubuntu.org/get](http://xubuntu.org/get) they say
*Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.*
I know my equipment is skinny, still I had some hope to replace W98...

cheers
M

---

