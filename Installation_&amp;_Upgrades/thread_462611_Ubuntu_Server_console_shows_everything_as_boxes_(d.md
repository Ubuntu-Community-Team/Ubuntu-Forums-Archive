---
title: "Ubuntu Server console shows everything as boxes (defaults to Chinese)"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by ToniCipriani on 2007-06-02
I'm installing an emulated server in VMWare, which will be actually implemented on real machines in company in Hong Kong later on. I've installed Ubuntu Server Dapper, and selected the language to be Chinese (since I do need the file system support for Chinese file names). But now, everything seems to be showing up as boxes (see screenshot). I understand it's just the locale set to Chinese, and everything tries to display Chinese. But is there a way for me to switch the display back to English, or set the console to be able to display Chinese? I don't really want to install X, since I want to keep the server minimal, and the server won't be running on very fancy hardware (Northwood Celerons).

[IMG]http://img245.imageshack.us/img245/6315/aptgetoutputwe0.jpg[/IMG]

---

### Post by ToniCipriani on 2007-06-12
Sorted it out. Just change the LANG export to en_US. Hopefullly Chinese file names still work.

---

