---
title: "Error installing programs, Searched a little and couldnt find help..."
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Shmargin on 2008-01-05
OK, I'll start off with the fact that I'm a linux noob, but have been building and working with computers for around 15 years, I know DOS and Windows inside and out, but having some troubles here with Ubuntu.

Initially after installing Ubuntu everything seemed fine, I used the System> Administration> Synaptic Package Manager menu to download and install some games and a couple apps, and they seemed to work just fine. I also downloaded a port for Quake Wars to play on Linux, all this seemed to download and install just fine, but after a couple days (and probably a couple reboots) I went to use the System> Administration> Synaptic Package Manager menu again to install some stuff, and it downloads just fine, and looks like it installs, but after the install completes, I get this error message:

**An error occurred** (but occurred is actually spelled '*occured*' on the error :) )

**The following details are provided:**

**E: ggzd: subprocess post-installation script returned error exit status 134**

I get this error for _anything_ I try installing now, any advice?

Thanks in advance!

---

### Post by Pumalite on 2008-01-05
What have you installed lately?
Try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
Post results.

---

### Post by taurus on 2008-01-05
Double post!

[http://ubuntuforums.org/showthread.php?t=659511](http://ubuntuforums.org/showthread.php?t=659511)

---

### Post by Pumalite on 2008-01-05
Stick with taurus.

---

