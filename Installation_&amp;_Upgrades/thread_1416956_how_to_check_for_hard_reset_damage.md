---
title: "how to check for hard reset damage"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by sdcoats on 2010-02-26
I feel a little awkward in this Control Panel: first time user. I installed the latest version of Ubuntu yesterday. All went smooth until I got to installing printer drivers. The setup went online and my system froze...everything froze. I had to do a hard reset. The printer installation went smooth the second time. So far this is the only problem I've had. No details needed. What I was wondering is if there's any way to check if the hard reset did any damage.

---

### Post by tgalati4 on 2010-02-26
Hard reset damage is automatically checked on the next reboot.  Similar to scandisk under windows.  You can always open a terminal:

sudo fsck /dev/sda5

This presumes that your ubuntu installation is on partition sda5.  To discover your partitions:

sudo fdisk -l

---

### Post by sdcoats on 2010-03-01
Thanks! ;) It does sound similar to windows. I did the install on a non shared drive. If there was some corruption I'd expect the messages to be more instructive than windows too, right? At this stage I'm not inclined to use sudo commands until I learn some more about how things work in restricted areas.

---

### Post by rnerwein on 2010-03-01
> **tgalati4 said:**
> Hard reset damage is automatically checked on the next reboot.  Similar to scandisk under windows.  You can always open a terminal:

sudo fsck /dev/sda5

This presumes that your ubuntu installation is on partition sda5.  To discover your partitions:

sudo fdisk -l
hi
sorry but think it's not so healthy to run a fsck on a life pratition.
so - do an umount ( if it's not the / file system - then you have to use a life CD )
on the other way it's true - a fsck is always run at boot when the "clear bit" on the file system isn't set and after a hard rest it isn't set.
but don't be worry. if the system comes up with no problem every thing seems ok.

ciao

---

