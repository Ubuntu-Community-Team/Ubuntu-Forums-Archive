---
title: "utf8 upgrade"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by jevb on 2005-10-16
Upgraded to Breezy, and after the first reboot I noticed a lightbulb icon in the upper right corner, on the panel. I pointed at it and a popup said there were two post install notifications. I clicked on it and a window popped up asling if I wanted to update my system to utf8. Not knowing if I should or not I just closed the window without doing the update. Then I came here to the forums to see if there was any info on it. I found nothing here, and now the notification icon is gone. 

Question, should I do the utf8 update? If so, how do I do that now that the icon is gone?

---

### Post by ubuntu_demon on 2005-11-18
This will upgrade your system :
$ sudo apt-get update ; sudo apt-get upgrade

If any package doesn't get upgraded do :
$sudo apt-get dist-upgrade

This will configure all the packages that aren't configured properly yet :
$ sudo dpkg --configure -a

Maybe this helps if you get into UTF8 troubles :

[https://wiki.ubuntu.com/UTFEightMigrationTool](https://wiki.ubuntu.com/UTFEightMigrationTool)

---

### Post by jevb on 2005-11-21
Thank you for the info.

:-)

---

### Post by ubuntu_demon on 2005-11-22
[QUOTE=jevb]Thank you for the info.

:-)[/QUOTE]
np :)

and keep clicking on the light bulbs :-P

---

