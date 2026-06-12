---
title: "Howto install lastest upgrade of various apps."
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by kline on 2006-07-01
[FONT="Times New Roman"]Is there a way of installing, either automatically or by-hand, the latest verion of an application?  The default version of amaroK, e.g., is 1.3.X whereas on their website, the version is 1.4.Xb.  I did click around looking for download instruction but couldn't understand the instructions.  Openoffice.org is another example.  The default on 6.06 is something like 195.X but the latest source and package are both at level 2.0.3.

Thanks for any insights!

gary kline[/FONT]

---

### Post by aysiu on 2006-07-01
I don't know about Beta, but you can get 1.4 Alpha by following these instructions:
[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

Version 2.0.3 of OpenOffice is available in the unstable branch of Debian:
[http://openoffice.debian.net/](http://openoffice.debian.net/)

---

### Post by kline on 2006-07-02
Well, I still couldn't figure out howto get the latest amaroK (1.4).  It looked like there were Kubuntu dependencies that required me to install an upgrade of KDE, so I passed.  With OO,  the newest stable 2.0.2_2 version was installable via Synaptic, so that upgrade is done.

Is there any way--thru GUI or CLI--to let [application] package upgrades be automagically installed??  On my BSD servers I have this cron'd ; with Ubuntu, still learning.

---

### Post by aysiu on 2006-07-02
Ubuntu is generally "frozen" for six months at a time, unless an application needs security updates.

At the time Ubuntu is released, it will use the latest software versions currently available, and then you'll essentially be stuck with those for six months until the next Ubuntu version is released.

There's a repositories project called *backports* that will sometimes compile .deb pools of the newest versions of some packages, but I think that's community-driven, not policy driven (so if someone actually puts it together, it's there; otherwise, it's not).

---

### Post by kline on 2006-07-04
What CLI command do I use to install a *package*.deb file?  (dpkg comes to mind, but I'm missing something.)  Also, it there is src available, howto install?  I'm pretty sure I have gcc installed, but if I type 

**% gcc test.c**

the system gets confused.

---

### Post by aysiu on 2006-07-04
```
sudo dpkg -i package.deb
```

---

