---
title: "Booting System Without full Network Configuration"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Gorrest on 2011-10-17
I started the download of 10.10 and after about an hour the machine appeared to be locked up.  The download did not appear to be complete and perhaps I should have waited longer for a possible resumption but I pulled the power cord and restarted.  I get to the 97% point on the purple screen and maybe I should wait longer than 10 minutes for more progress but I reboot and restart and after 6 tries - no progress.  I can get the grub page and have tried going back to previous installation.  This computer is a simple one for surfing the net and watching Youtube only - it has an Asus board and Sempron 140 chip and 500 gig HD.  My solution is to load 10.10 from a USB stick which I have ready but it is one year old. I should have waited at least a month before attempting 11.10.

---

### Post by elbakly on 2011-10-19
i found a solution on this link and it did work for me
[http://www.totalcomputersusa.com/2011/10/ubuntu-11-10-booting-system-without-full-network-configuration/](http://www.totalcomputersusa.com/2011/10/ubuntu-11-10-booting-system-without-full-network-configuration/)

---

### Post by ramasamyz on 2012-08-21
Removing certain lines from /etc/network/interface solved my issue.

Follow this [link]("http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time") for more help.

---

