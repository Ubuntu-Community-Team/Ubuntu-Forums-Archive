---
title: "Video &quot;noise&quot; when moving mouse"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by VK2XCI on 2006-08-01
This is a brand new install, where Mandrake 9 used to be. I think the change from Mdk9 to Ubuntu is as traumatic as that from Win to Mdk!!!

In 1024 x 768 mode, I get video noise (aka sparkles or flashes) whenever the mouse moves! At 800x600 this doesn't happen.

Also, the choice of modes and refresh rates is very limited, which sounds like an xconfig problem to me.

Alas, I can't find "Hardrake" to fix it:rolleyes: 

Do I have to edit xconfig by hand or is there a better way? (It's been a looooooong time since RedHat 6.2!):p

---

### Post by VK2XCI on 2006-08-01
Anyone else had this problem? Using an old S3 Virge PCI card and Samsug 17" monitor.

---

### Post by ekarni on 2006-08-01
Try *sudo dpkg-reconfigure xserver-xorg* to reconfigure the xserver using an ncurses terminal GUI.  If you want to get your hands dirty, take a look at /etc/X11/xorg.conf for starters.

---

### Post by VK2XCI on 2006-08-01
> **ekarni said:**
> Try *sudo dpkg-reconfigure xserver-xorg* to reconfigure the xserver using an ncurses terminal GUI.  If you want to get your hands dirty, take a look at /etc/X11/xorg.conf for starters.

Thanks ekarni,
I almost gave up waiting for a reply. RTFM'd everything I could find and I'll give xorg.conf a run tonite when all is quiet! It's a pretty generic sort of conf, didn't find my monitor type so it's generic, and also called a generic S3 card.

Both are dated but not exactly legacy!

Norm

---

