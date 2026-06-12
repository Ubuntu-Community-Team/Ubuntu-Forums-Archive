---
title: "Xterm starts after login to Kubunu"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by pgk3734 on 2006-08-08
I originally installed Dapper Drake 6.06 and liked it but wanted to
also install KDE window manager. I used Adept (very good) but still like
apt-get. Anyhow when I restart after signing in to KDE with name
and pw I get Xterm in upper left corner of screen and must start
KDE by hand (startkde). I can't seem to find out why this is happening.
Naturally if xterm is killed poof there goes kde.[-X 
Any help appreciated.
tia,
pgk

---

### Post by zxee on 2006-08-09
Here [http://www.ubuntuforums.org/showthread.php?t=15193&highlight=changing+window+manager](http://www.ubuntuforums.org/showthread.php?t=15193&highlight=changing+window+manager)
is a thread that covers most of the procedures/pitfalls.
Hope that helps.

---

### Post by pgk3734 on 2006-08-10
Sorry, that didn't help.
Does anyone know where could there be
a script to start xterm after login?
I have the default display manager set
for kdm in /etc/X11/default-display-manager.
And also init 5 for startup. And yet, it goes
to the xterm and waits for startkde to enable
my desktop in kde.:confused: 
tia,
pgk

---

### Post by pgk3734 on 2006-08-10
/usr/bin/kdm starts /usr/bin/xterm starts /bin/sh which starts kwrapper
(probably after I type startkde in the xterm.

I can't figure why it's starting like this, almost like in failsafe.

---

