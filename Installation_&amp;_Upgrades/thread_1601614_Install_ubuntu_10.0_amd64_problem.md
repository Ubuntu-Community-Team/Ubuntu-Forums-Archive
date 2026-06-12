---
title: "Install ubuntu 10.0 amd64 problem"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Jorge Iten on 2010-10-20
Hello!

I am trying to install the ubuntu 10.0 amd64 version in my notebook hp dv6750br, the installation take a long while, compared with windows, but at end it finishes ok. My problem is when I start the ubuntu my screen is unconfigured. Just like the image below. I try to install through the windows and the error is the same, i try just run ubuntu and the same again. Do you know if I can change the resolution or other configuration by command line?
thks.

image: [http://img139.imageshack.us/i/ubuntux.jpg/](http://img139.imageshack.us/i/ubuntux.jpg/)

---

### Post by lemming465 on 2010-10-21
The first thing I'd try is Ctrl-Alt-F1 to shift to a text console, log in, and run```
sudo aptitude update; sudo aptitude full-upgrade
```.  If the X driver bug giving the wacky screen resolution has been patched, that may fix it.  If not, write back for more advice, and attach a copy of /var/log/Xorg.0.log.

---

