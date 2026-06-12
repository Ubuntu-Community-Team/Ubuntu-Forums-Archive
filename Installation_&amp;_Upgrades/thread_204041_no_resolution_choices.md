---
title: "no resolution choices"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Sasquatch2000 on 2006-06-26
Installed Xubuntu 606 on a PC. Everything went without a hitch until I started up and cannot change the resolution. This is with an All in Wonder Radeon (9600?) ATI graphics card on an AMD Athlon XP chip ASUS motherboard.

Any idea what might have happened?

Thanks.

---

### Post by b0bby on 2006-06-26
have u tried to install the fglrx-drivers as described here,
[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

or have a look se in yout xorg.conf file and see if you can add more resolutions there that u know work =)

---

### Post by MrTroll910 on 2006-06-27
Just in case you haven't resolved this by now...
I had the same problem with my first install, and my second, and my third, and my fourth.  Each time I had to reinstall for unrelated reasons and each time installing the ATI drivers fixed it.  Finally though, I found an easier was.  One of the problems I had ended up being XServer crashing.  So I followed the instructions in this post:
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

Once that's been done after a clean install, I can get all the resolution choices I need.  It isn't as good as installing the drivers, but it's a big help.

---

### Post by Sasquatch2000 on 2006-07-07
Would updating the Xfce desktop environment help this at all? The latest shown is Xfce 4.4 beta1 (4.3.90.1) . What version does Xubuntu 6.06 use? How does one update this part of the system?

Thanks.

---

