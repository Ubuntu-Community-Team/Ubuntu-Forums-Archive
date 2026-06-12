---
title: "Is GNOME Slow or........."
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by sqlpython on 2008-09-02
Just installed Ubuntu 8.04 lts. I usually would install Kubuntu but I had mislabeled the disk and thought aw, what the heck. :) I hadn't used GNOME in some time ( a year or more). I usually use KDE or xFCE.
 The install went fine except on the liveCD the Broadcom Wifi installed right from the Hardware Tool and downloaded the firmware. Once the HD install was done the tool would not work and I ended up doing a  wget to b43-fwcutter and then a b43-fwcutter -w to install the driver. Go figure.. huh?

 Anyhow, I don't ever remember GNOME doing so much Greying Out and Calculating/Freezing while I waited for simple Mouse clicks in apps. Firefox and Nautilus were prime offenders. Using an Inspiron dual amd64 2gb mem 256mb video.
 Can anyone shed some light on the Slow GNOME reactions?

****I posted this with an Ubuntu prefix also. So feel free to to move combined or delete. Sorry, I wasn't sure as to best response***

---

### Post by Catalyst2Death on 2008-09-02
Gnome enables desktop effects by default, and it may be giving you trouble if you don't have a hardware accelerated driver installed...

System>Preferences>Appearance Desktop effects tab, if you want to change the settings.

---

