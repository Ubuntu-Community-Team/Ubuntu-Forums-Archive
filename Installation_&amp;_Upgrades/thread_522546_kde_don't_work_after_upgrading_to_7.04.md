---
title: "kde don't work after upgrading to 7.04"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by sv75 on 2007-08-10
Something gones bad when upgrading to 7.04. Every program that uses kdelibs is crashed, KDE itself included. Gtk apps work fine. The full story:

1. KDE halts on "Loading window manager"

2. Following messages apppear when running kde apps from gnome:
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
 
3. Then I read [http://www.mail-archive.com/debian-bugs-dist%40lists.debian.org/msg354475.html](http://www.mail-archive.com/debian-bugs-dist%40lists.debian.org/msg354475.html) and run kbuildsycoca.

4. Nothing is working anyway:

$ konqueror
DCOPClient::attachInternal. Attach failed Could not open network socket
Segmentation fault (core dumped)

$ kwrite
Failed to open device
Segmentation fault (core dumped)

Please advice :(

---

### Post by aysiu on 2007-08-11
Not sure if this'll just lead you to more dead-ends, but I figured it couldn't hurt, since you've had no responses within eleven hours.

This thread has a bunch of possible solutions to try:
[http://dot.kde.org/1021838067/1022774059](http://dot.kde.org/1021838067/1022774059)

---

### Post by sv75 on 2007-08-11
Thnaks aysiu, 

but this thread does not look like my problem. Dcopserver starts, creating new user change nothing, resintaling kde does not help, copying /etc/kde3 from my 7.04 laptop does not help too. 

Sh%t, it's "windows-like" bug.  Ok, I'll backup my home and resintall the whole system, not a big problems. It was kind of testing desktop computer. Still it hurts me that I found a problems and cannot solve it :(

---

### Post by Pumalite on 2007-08-11
Your best bet is to delete ~/.ICEauthority, reboot and let the system rebuild the file.

---

