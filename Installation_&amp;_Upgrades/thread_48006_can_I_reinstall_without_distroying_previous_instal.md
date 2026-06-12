---
title: "can I reinstall without distroying previous installation? and other recommendations"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by tigerstripedcat on 2005-07-10
I have no way of relibably checking this at the moment.

I installed kubuntu and had everything working great, then I tried to get my unichrome drivers, lost my via kernel module, now my Xserver is hosed (I tried upgrading to breezy, and a few other things to try and get back via_drv.o.

I'm pissed enough to reinstall.  Is there an option (like on mandrake) to reinstall the system files (Xserver, etc.) without touching my personal files (mp3s, docs) or config files (/etc)?  I'd hate to reinstall everything again.

If you have any recommendations as to how to go about reinstalling, please let me know.

THANKS!

---

### Post by Xian on 2005-07-10
[QUOTE=tigerstripedcat]Is there an option (like on mandrake) to reinstall the system files (Xserver, etc.) without touching my personal files (mp3s, docs) or config files (/etc)?  I'd hate to reinstall everything again.[/QUOTE]
You can reinstall any packages you want while still in your system.
```
$ sudo apt-get --reinstall install <packagename>
```

---

