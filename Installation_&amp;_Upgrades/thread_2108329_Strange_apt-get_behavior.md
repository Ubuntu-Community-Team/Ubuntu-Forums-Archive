---
title: "Strange apt-get behavior"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by zubor on 2013-01-24
Hi all, 

I'm trying to do a relatively lightweight 12.04 install. I downloaded mini.iso and did a command line install. One my first login, I execute a custom script for app setup

#!/bin/bash

apt-get update

apt-get install -y xfce4 xubuntu-artwork xubuntu-default-settings cups wicd gvfs-backends gvfs-bin gvfs-fuse ubuntu-restricted-extras xfce4-power-manager mousepad chromium-browser xfburn xarchiver vlc evince ristretto gmusicbrowser gimp transmission libreoffice-writer libreoffice-calc libreoffice-impress sound-juicer filezilla xfce4-taskmanager alacarte

apt-get upgrade
apt-get clean
reboot
 
When I reboot into XFCE, something has pulled in a bunch of gnome stuff. I think gnome-shell, brasero, network-manager-gnome, ubuntu one, etc....

So I tried to investigate. I did a clean install, then installed only:

apt-get install -y xfce4 xubuntu-artwork xubuntu-default-settings

Rebooted into XFCE4. Then I installed the remainder of the packages one by one to try and see which was pulling in the gnome dependencies. However, when installing one by one, none of them do! The install was clean!

Any help would be really appreciated!

---

### Post by zubor on 2013-01-24
Update: It is alacarte.

But why does it pull in 1000 dependencies when executed as part of the single agt-get install with all the packages, as opposed to installing one by one individually?

---

### Post by ibjsb4 on 2013-01-24
Im not seeing those 1000 depends.  Can you post what you are seeing?

[http://packages.ubuntu.com/precise/alacarte](http://packages.ubuntu.com/precise/alacarte)

---

### Post by Cheesehead on 2013-01-24
alacarte is a GTK application. It recommends a lot of Gnome dependencies because that's what it is designed to work with.

I suspect you are seeing the difference between Depends and Recommends dependencies.

---

