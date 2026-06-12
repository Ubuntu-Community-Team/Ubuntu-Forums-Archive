---
title: "fiesty downgrade? possible?"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by oxyrosis on 2007-04-26
fiesty has been a very bad fox.

my computer was running superbly until i upgraded to fiesty. Being a inexperienced user, i didnt have a backup version of edgy eft to fall back upon. oops.

After i rebooted my computer i experienced some problems with my login. Mainly it wouldn't open the login screen (instead it would show my mouse on "loading" mode forever) I tried several methods for repairing it...

**number one**
> dpkg-reconfigure xserver-xorg 
then
> sudo apt-get install xserver-xorg-video-vesa
then
> sudo /etc/init.d/gdm restart

**number two**
> sudo dpkg-reconfigure xserver-xorg
then
> sudo apt-get install --reinstall xserver-xorg

neither worked.

what i want to do is downgrade back into edgy eft, is it possible to go back without losing any of my settings or files? i'd really like that.

gracias

---

### Post by zvacet on 2007-04-26
[https://help.ubuntu.com/community/DowngradeHowto]("https://help.ubuntu.com/community/DowngradeHowto")

---

