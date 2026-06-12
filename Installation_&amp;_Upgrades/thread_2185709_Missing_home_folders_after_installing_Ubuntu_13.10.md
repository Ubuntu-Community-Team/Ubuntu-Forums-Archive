---
title: "Missing /home folders after installing Ubuntu 13.10 over previous LVM'd linux OS"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by darren-garvey on 2013-11-03
[COLOR=#333333][FONT=UbuntuRegular]I have just installed Ubuntu 13.10 onto a system that's had various flavours of Fedora, then Debian on it. It has also been dual-boot with Windows 7 for a couple of years. I had been using LVM with those linux installations so for instance when I installed Debian I kept all of my original /home directories.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]During the Ubuntu isntallation I manually set up the partitioning, setting /home to be mounted from the original LVM /home volume (/dev/fedora/home in my case), making sure to not tick the "format" box. This worked fine for Debian.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After completing the installation and booting, I can't see any of the previous home directories. The only cause I can think is that during installation I said to encrypt my user account's home folder. I made sure to pick a different user name to keep the original home directories intact, but something seems to have gone wrong. Ubuntu didn't warn me that it was going to wipe out /home after I told it not to.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any suggestions as to where my directories may have gone?[/FONT][/COLOR]

---

