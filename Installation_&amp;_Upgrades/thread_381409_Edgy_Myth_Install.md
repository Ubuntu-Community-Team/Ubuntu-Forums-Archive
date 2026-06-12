---
title: "Edgy Myth Install"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by affeking on 2007-03-10
Trying to install mythTV under Ubuntu Edgy using these instructions:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)
(I am doing just a backend/frontend with no desktop manager)

All was going (mostly) well until I got to the "Install MythTV" portion.  I'm getting a ton of problems trying to run this:
[INDENT]sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu[/INDENT]

First I get:
E: Couldn't find package openbox

When I remove openbox (out of desperation) I get:
E: Package msttcorefonts has no installation candidate

When I remove that, I get:

The following packages have unmet dependencies:
  mythtv-backend: Depends: libjack0.100.0-0 (>= 0.101.1) but it is not installable
                  Depends: liblame0 (>= 3.96.1) but it is not installable
                  Depends: libmyth-0.21 but it is not going to be installed
  mythtv-frontend: Depends: libjack0.100.0-0 (>= 0.101.1) but it is not installable
                   Depends: liblame0 (>= 3.96.1) but it is not installable
                   Depends: libmyth-0.21 but it is not going to be installed
E: Broken packages

By the way, I'm using the standard repositories PLUS these (added per the instructions on the walkthru):
deb [http://download.silicondust.com/](http://download.silicondust.com/) ubuntu/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

Any ideas what I'm doing wrong?

Thanks,
Jeff

---

### Post by majoridiot on 2007-03-16
the ubuntu mythtv guides are being re-worked for the impending feisty release- and that particular
guide happens to be next on the agenda.  Any problems with accuracy should be shaken out quickly.

if there are no problems with the feisty install, i'll try an edgy install to see if there are package
problems- which may take a day or two.

if the problem has already been resolved, please let me know.

---

### Post by electronikjunkie on 2007-03-16
i was in a similar situation before. i just wrote down all the unmet dependencies and installed them before mythtv (or whatever package has the dependencies) on a fresh install.

---

### Post by majoridiot on 2007-03-19
the problem does not exist on the feisty packages (they are AWESOME, by the way).  i haven't
had an opportunity to check the edgy packages yet...

---

