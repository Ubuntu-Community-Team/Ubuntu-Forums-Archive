---
title: "broken dependencies/update manager"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by ub newb on 2010-03-27
I have been unable to update due to "broken dependencies". Please take a look at the message: 

Fetched 8904kB in 1min29s (99.7kB/s)                                           
Reading package lists... Done
XXXXXX@MDdesktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cpp: Depends: cpp-4.2 (>= 4.2.3-1) but it is not installed
  deskbar-applet: Depends: libffi4 but it is not installed
  gcc: Depends: gcc-4.2 (>= 4.2.3-1) but it is not installed
  python-gnome2-desktop: Depends: libffi4 but it is not installed
  python-gobject: Depends: libffi4 (>= 4.1.1-21) but it is not installed
  python-gtksourceview2: Depends: libffi4 but it is not installed
  python-launchpad-integration: Depends: libffi4 but it is not installed
  python-notify: Depends: libffi4 (>= 4.2.1) but it is not installed
  python-vte: Depends: libffi4 but it is not installed
  rhythmbox: Depends: libffi4 but it is not installed
  totem-gstreamer: Depends: libffi4 but it is not installed
E: Unmet dependencies. Try using -f.
XXXXXX@MDdesktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
XXXXXXX@MDdesktop:~$ 


I have never done anything as root. I posted this request in absolute beginner talk, because I am, but there has been no resolution after three weeks or so. 

Thanks

---

### Post by zvacet on 2010-03-27
```
sudo apt-get -f install
```

---

### Post by ub newb on 2010-03-27
thnx, all fixed!

---

