---
title: "Upgrade 14.10 to 15.04 Boot Issue"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by mrkeef on 2015-04-24
Since upgrading from 14.10 to 15.04 today, I have this issue that the computer will not start correctly. Part way through it just goes from the blank purple screen to a blank black screen.

This started with the restart that happens during the upgrade.

If I reset the machine at this point I can go to the GRUB screen and select "Advanced Options" and then "Upstart" and everything works fine.

---

### Post by dino99 on 2015-04-24
hm, already have seen several users complaining about such issue. Is it u/k/xubuntu ? Maybe the logs will give you some ideas about the problem. You can try to purge the graphic driver, then re-install it.

---

### Post by mrkeef on 2015-04-25
I discovered this is due to the transition to systemd. The old init system was called upstart.

Found this page: [https://wiki.ubuntu.com/SystemdForUpstartUsers ]("https://wiki.ubuntu.com/SystemdForUpstartUsers") which shows you how to set upstart as the permanent init system.

---

