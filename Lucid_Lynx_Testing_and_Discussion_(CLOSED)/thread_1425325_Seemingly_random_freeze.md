---
title: "Seemingly random freeze"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kebabji on 2010-03-08
Starting a few weeks ago, after a few updates, my Lucid laptop is prone to freezing at random times. It will last when leaving it idle for hours, but when going through my rhythmbox library, surfing the net, or whatever, it just locks up and restarts. An almost sure way of ensuring a lockup is watching anything in flash a few times.

I've got a couple of experimental repositories so it could be anything, so my question is this - which log file should I be going through that would hint at a problem?

(p.s. not the plymouth enter key problem)

---

### Post by lidex on 2010-03-09
Xorg.0.log, messages, dmesg, syslog

If you have the gnome-utils package installed you can go to "applications>system>administration>log file viewer" and see them all.

---

### Post by zika on 2010-03-09
> **lidex said:**
> Xorg.0.log, messages, dmesg, syslog

If you have the gnome-utils package installed you can go to "applications>system>administration>log file viewer" and see them all.As far as my knowledge goes, no info can be extracted from log files in this case... [http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430) because freeze takes them away...

---

### Post by lidex on 2010-03-09
Hmm, interesting. So no one knows exactly what is causing this, other than a suspicion KMS is involved and Firefox/flash may be setting it off?

---

### Post by zika on 2010-03-10
It seems we have, at least, 3 threads about the same thing so, here is the list:
[http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)
[http://ubuntuforums.org/showthread.php?t=1425325](http://ubuntuforums.org/showthread.php?t=1425325)
[http://ubuntuforums.org/showthread.php?p=8945962](http://ubuntuforums.org/showthread.php?p=8945962)

---

### Post by lidex on 2010-03-10
Guess I'm one of the lucky ones - no freeze issues whatsoever.

---

