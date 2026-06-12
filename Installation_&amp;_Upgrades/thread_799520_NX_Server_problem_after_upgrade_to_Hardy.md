---
title: "NX Server problem after upgrade to Hardy"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by TheR on 2008-05-19
After upgrade to Hardy (which looks quite smooth) I tried to start NX Client, but got this message:

Cannot find the KDE environment. Please contact your system Administrator. 

Hardy, kubuntu, x86-64. I have also upgraded nxserver package to last version with no difference. Any suggestions?

by
TheR

---

### Post by TheR on 2008-05-21
I had to manually update /usr/NX/etc/node.conf file. Change line

CommandStartKDE="/usr/bin/dbus-launch --exit-with-session startkde"

to 

CommandStartKDE="startkde"


by
TheR

---

### Post by ccrockett on 2008-06-05
It seems that dbus-launch is not installed by default under Hardy. So do the following:

sudo apt-get install dbus-x11

then it should work without changing the nx config file

---

