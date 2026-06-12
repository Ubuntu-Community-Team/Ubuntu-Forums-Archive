---
title: "Failed to start session"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by ron17 on 2014-04-18
After getting notified to update my ubuntu server to version 14.04 (one with graphical desktop) the upgrade procedure went without any major issues.
Restarting the server and trying to logon into my graphical desktop i get the error "Failed to start session", so something seems to went wrong with the upgrade procedure.

Anyone who can guide me how to recover from this error? Thanks in advance.

---

### Post by ron17 on 2014-04-18
Solved the issue by pressing CTRL+ALT+F1

Issueing the following commands reinstalling ubuntu-desktop, since couldn't reinstall it after apt-get update

sudo su
apt-get clean
cd /var/lib/apt
mv lists lists.old
mdir -p lists/partial
apt-get clean
apt-get update
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install ubuntu-desktop[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]dpkg-reconfigure ubuntu-desktop
reboot[/FONT][/COLOR]

---

