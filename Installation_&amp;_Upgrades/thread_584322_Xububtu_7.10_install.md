---
title: "Xububtu 7.10 install"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jasonlfunk on 2007-10-20
I just installed the 7.10 release of Xubuntu and it installed. But now when I log in, the X server fails to start and tells me:

Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

It gives me a process number but it seems to kill the process as it is never there when I look for it after trying to log in. Is there a way I can log processes to see what it is, or does somebody know what is causing this problem?

---

### Post by jasonlfunk on 2007-10-20
I have manged to determine that it is 'gdmflexiserver' that is causing the error, though I have chmod 755 gdmflexiserver (and i'm pretty sure it wasn't setuid/gid anyways) though it is still causing the error.

---

### Post by jasonlfunk on 2007-10-21
Well, I fixed it with
apt-get remove --purge gdm
apt-get install gdm

Eh, oh well.

---

