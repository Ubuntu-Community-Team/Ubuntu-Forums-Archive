---
title: "xorg-edgers and intel video"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-10-11
Using the xorg-edgers PPA [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) for my intel card, I've noticed that the package xserver-xorg-video-intel it is not updated through PPA but the system keep the version from official repos one.
```
apt-cache policy xserver-xorg-video-intel
```
> xserver-xorg-video-intel:
  Installed: 2:2.9.0-1ubuntu1
  Candidate: 2:2.9.0-1ubuntu1
  Version table:
 *** 2:2.9.0-1ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status
     2:2.9.0~git20091010.8b2d2ff0-0ubuntu0tormod 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Someone else have this scenario?

Btw, the system is quite good, at the boot no more messages on console:
grub -> usplash (white logo on black) -> xsplash (ufo environment with lights) -> gdm login -> xsplash again

---

### Post by dino99 on 2009-10-11
need first to clean the cache then update ppa repo & upgrade

---

### Post by dentaku65 on 2009-10-11
> **dino99 said:**
> need first to clean the cache then update ppa repo & upgrade

I did clean, update and dist-upgrade, but nothing happens

---

### Post by Zorael on 2009-10-11
I think that's expected behavior?

2:2.9.0**-**1ubuntu1
2:2.9.0**~**git20091010.8b2d2ff0-0ubuntu0tormod

The xorg-edgers build would have to be named **-2~git**... to get priority.

(Stuff with tilde additions get lower priority; **-1** overrides **-1*~ppa***. Hence unofficial/PPA versions are incremented to **-*(n+1)*~ppatext**, so the real **-*(n+1)*** release overrides when available.)

---

### Post by dentaku65 on 2009-10-12
> **Zorael said:**
> I think that's expected behavior?

2:2.9.0**-**1ubuntu1
2:2.9.0**~**git20091010.8b2d2ff0-0ubuntu0tormod

The xorg-edgers build would have to be named **-2~git**... to get priority.

(Stuff with tilde additions get lower priority; **-1** overrides **-1*~ppa***. Hence unofficial/PPA versions are incremented to **-*(n+1)*~ppatext**, so the real **-*(n+1)*** release overrides when available.)

Uh! I suspect such thing of incorrect package versioning... I'm going to write an e-mail to them.

Thx

---

