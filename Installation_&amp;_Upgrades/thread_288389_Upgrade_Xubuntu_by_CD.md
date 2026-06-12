---
title: "Upgrade Xubuntu by CD"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by racoq on 2006-10-29
Hello everyone.

Since i'm using Xubuntu, i've always decided to install each release from scratch. However know i have xubuntu dapper much configured and customized, and i would like to upgrade to xubuntu edgy from the CD i've downloaded, in a place where i have internet(since i don't have any network connection on my PC)

Is it possible and safe to upgrade from dapper to edgy in Xubuntu with for instance an alternate cd?
How can i do this? can anyone show me the necessary steps?

Please reply

---

### Post by zek725 on 2006-10-29
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

[https://help.ubuntu.com/community/EdgyUpgrades#head-0ee455b2d02f220b043c084f09dffb86c1c6bd79](https://help.ubuntu.com/community/EdgyUpgrades#head-0ee455b2d02f220b043c084f09dffb86c1c6bd79)

---

### Post by aysiu on 2006-10-29
My advice:

If you have Dapper configured and customized exactly the way you want it, [use PartImage to make an exact backup copy of your partition](http://www.psychocats.net/ubuntu/partimage) before you do anything else.

Then, you can do whatever you want, and if the upgrade screws up, you can restore your Dapper installation exactly as it was.

As for upgrading with an Alternate CD, it's quite easy, actually: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo mv /etc/apt/sources.list /etc/apt/sources.list.dapper
sudo apt-cdrom add
``` Pop in the Xubuntu Edgy Alternate CD when prompted ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

