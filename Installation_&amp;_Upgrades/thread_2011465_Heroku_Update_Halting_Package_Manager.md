---
title: "Heroku Update Halting Package Manager"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by kpryde on 2012-06-27
jennifer@computer:~$ sudo apt-get install pulseaudio
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/toolbelt.heroku.com_ubuntu_._en
E: The package lists or status file could not be parsed or opened.

I can't get updates or packages because I'm getting this error. Any suggestions? I'm running Ubuntu 12.04 on an Asus.

---

### Post by dino99 on 2012-06-27
open a terminal to run:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

