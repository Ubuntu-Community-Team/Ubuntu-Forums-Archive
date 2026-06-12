---
title: "Can I preserve wi-fi drivers with alternate ISO upgrade?"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2016-01-21
I'm running 11.10 and would like to install 15.10, but if I do a completely new install from the LiveDVD, I need to get new wi-fi drivers.  This is a problem for me because I'm new to Ubuntu, in a foreign country with no support, and have only my wi-fi connection to the Internet (no cabled connection available).

If I understand correctly, I can upgrade to 15.10 without doing a completely new install by using a LiveDVD with the alternate install image rather than the desktop install image.

With the alternate install LiveDVD, can I upgrade directly from 11.10 to 15.10, and (most importantly) will this upgrade preserve my current wi-fi drivers?

I think the answer is "no, the wi-fi drivers are specific to the OS release," but I wanted to double-check.  Thanks.

---

### Post by sammiev on 2016-01-21
Hi Chris,

Your best to download the ISO you want to try and install it to a USB/DVD and try it live. The wi-fi may just work.

Usually upgrades will preserve current wi-fi drivers.

Your best bet would likely be 14.04LTS ( Long Term Version ) but try 15.10 as well.

---

### Post by anotherChris on 2016-01-22
I already tried the LiveDVD boot with 15.10, and the wi-fi doesn't work.  At [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx), it mentions separate firmware for 12.04 and 14.04 releases, and at [https://launchpad.net/ubuntu/+source/b43-fwcutter](https://launchpad.net/ubuntu/+source/b43-fwcutter), it lists different fw-cutter packages for 14.04,15.04, and 15.10.  That's why I think I need new drivers even if I upgrade.

Unfortunately, while I can try a LiveDVD, I can't test upgrading vs. a fresh install, so I don't really know if upgrading can preserve my wi-fi unless somebody tells me.

I just tried a LiveDVD boot with 14.04.3 LTS, too.  It doesn't have wi-fi either.

---

### Post by Vladlenin5000 on 2016-01-22
In any scenario you'll have to install drivers for WiFi and for that an alternative internet connection, preferably by Ethernet cable, is highly recommended. Not strictly necessary but you'll have a really hard time without it.
Anyway, what you SHOULDN'T be running is an outdated release - 11.10 - for which you CAN'T install anything because it reached its end of life (and support) years ago.

---

### Post by anotherChris on 2016-01-25
> **Vladlenin5000 said:**
> In any scenario you'll have to install drivers for WiFi and for that an alternative internet connection, preferably by Ethernet cable, is highly recommended. Not strictly necessary but you'll have a really hard time without it.
Anyway, what you SHOULDN'T be running is an outdated release - 11.10 - for which you CAN'T install anything because it reached its end of life (and support) years ago.

Yes. I held on for a long time.  It was very fast, and I never had problems until this last year.  Now I'm on 15.10 and everything is great.  Thanks!

---

### Post by Vladlenin5000 on 2016-01-25
You're welcome :-)
Please use the thread tools to mark it as solved if you no longer need help with this issue.

---

