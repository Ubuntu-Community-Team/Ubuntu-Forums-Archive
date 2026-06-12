---
title: "xsplash, how can I enable it?"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-08-12
Today I noticed aptitude installed xsplash,

However booting simply uses usplash, is that because it is not used yet, or is it because I customized my boot process to increase speed?
> 
xsplash:
  Installed: 0.4-0ubuntu1
  Candidate: 0.4-0ubuntu1
  Version table:
 *** 0.4-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status


---

### Post by castrojo on 2009-08-12
Currently this only shows up before gdm (but after usplash) and after gdm but before your desktop (as far as I can tell).

Still needs tweaking though, I see flicker and there's no fading going on (yet).

---

### Post by tekstr1der on 2009-08-12
xsplash fades the curtain into the desktop here. Switches back and forth between the curtain and my custom gdm background a couple of time first though.

---

### Post by plun on 2009-08-12
X start must be moved to start directly after boot, not done yet

This is also discussed within this thread and how it looks.

[http://ubuntuforums.org/showthread.php?t=1236727](http://ubuntuforums.org/showthread.php?t=1236727)


..

---

