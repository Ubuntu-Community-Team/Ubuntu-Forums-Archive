---
title: "Boot problem when dual monitor is not attached"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by xtrailrunner on 2012-10-22
I have upgraded resently my Lenovo T430 from Ubuntu 12.04 to 12.10.
Dual monitor was detected and usable after upgrade.
When I boot the laptop without the second monitor Ubuntu will not enter into graphics mode but I can activate console with <Ctrl><Alt><F1>.
When I attach the second monitor graphics mode will display immediately.

How to correct the installation so that I can use laptop with and without second monitor ?
Thanks
Juergen

---

### Post by xtrailrunner on 2012-10-23
Possibly I could solve the problem by removing gsettings-data-convert.desktop from directory /etc/xdg/autostart but I'm not sure what the consequences are.

---

### Post by xtrailrunner on 2012-10-24
I have reactivated gsettings-data-convert.desktop and the problems are still there. I noticed that after nearky each reboot system reported a crash of Nemo and problems with xorg.

---

### Post by xtrailrunner on 2012-10-26
It seems that the service lightdm takes very long time to start. I have already executed:
dpkg-reconfigure lightdm
and purged gdm.

---

### Post by xtrailrunner on 2012-10-29
Solved:
Including "sleep 2" into /etc/init/lightdm.conf solved the problem for now: 
[SIZE=3][COLOR=#0000ff]_[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410)_[/COLOR][/SIZE]

---

