---
title: "Unable to upgrade Ubuntu Cinnamon 23.04 to 23.10"
date: 2023-11-14
forum: Installation &amp; Upgrades
---

### Post by john4879 on 2023-11-14
SOLVED

Upgaded the ubuntucinnamon-desktop from Synaptic Package Manager

==


I'm stuck regarding upgrade the Ubuntu Cinnamon distro from 23.04 to 23.10.
How do I upgrade lunar from 22.10.2 to 23.04.4?

Some info:

**apt -a list --upgradeable**
results in:
ubuntucinnamon-desktop/lunar 23.04.4 amd64 [upgradable from: 22.10.2]
ubuntucinnamon-desktop/now 22.10.2 amd64 [installed,upgradable to: 23.04.4]

**sudo apt update**
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar InRelease
Hit:2 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-backports InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

**sudo apt upgrade**
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  yaru-theme-gtk
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  ubuntucinnamon-desktop
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

**cat /etc/apt/sources.list |grep lunar**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security multiverse

---

