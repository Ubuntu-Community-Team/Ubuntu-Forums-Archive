---
title: "upgrade using install cd as repo"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Brunellus on 2005-10-15
Quick one.

Will someone who has fresh installed breezy please post the contents of their ```
/etc/apt/sources.list
``` file?  

My dist-upgrade went pear-shaped, and I'm going to to try to upgrade using the CD.  I can't start X, so I'm going to have to do it from the commandline.  I therefore need to know how the ```
deb cdrom
``` line looks so I can edit it appropriately.

---

### Post by SilentCacophony on 2005-10-15
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

*Note* - I've had mixed results just adding the line like that. There is an apt utility to add it for you, that you can use as well:

**sudo apt-cdrom add**

EDIT - I should add that it will prompt you to enter the disc after that, then write in the line to sources.list.

---

### Post by solatis on 2005-10-15
and if you use it from iso, like me, use

mount -o loop -t iso9660 /downloads/breezy.iso /mnt/iso
apt-cdrom -d/mnt/iso add

---

### Post by pavan on 2005-10-15
solatis: After mounting the iso image I believe this should be added to sources.list. 

deb file:/mnt/iso breezy main restricted

The apt-cdrom method did not work for me.

Pavan

---

