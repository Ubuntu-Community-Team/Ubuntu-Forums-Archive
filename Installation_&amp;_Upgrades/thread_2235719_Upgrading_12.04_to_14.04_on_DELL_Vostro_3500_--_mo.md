---
title: "Upgrading 12.04 to 14.04 on DELL Vostro 3500 -- more grief"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-22
I had my secretary prepare 14.04 64-bit live CD.  Everything ran fine and looked fine running from Live CD.  Did the installation as "upgrade" everything seemed to go smoothly except for message at the end stating that some packages could not be reinstalled.

Rebooted and GRUB screen came up correctly.  Win XP loaded and ran correctly.  Rebooted and loaded Ubuntu.  Screen came up wrong resolution and locked up on login.  Rebooted and went to recovery screen.  Low-graphics option would not work.  Tried clean and nothing neeed to be cleaned.  Ran dpkg and found I had no internet.  Ran internet from recovery screen.  Ran dpkg again and it decided to reload numerous programs and then seemed to be trying differnt kernel configurations and then screen went blank, but disk still showing activity.

What do I do next?

John

---

### Post by cigtoxdoc on 2014-07-22
After looking at blank, black screen for over 20 minutes, shut off PC and rebooted.  Camed up minus some software and with nouveau drivers.  Installed nVidia 331.38 driver and rebooted.  We may be back in action.

John

---

### Post by Bucky Ball on 2014-07-22
And ... ? ;)

---

### Post by cigtoxdoc on 2014-07-22
I have spent over an hour (and still not done) adding mission critcal software (synaptic, evolution, skype, konqueror) and getting paths and file permissions correct.  I have all my scientific data, letters, speadsheets in separate partitions on the SSD, so I can reload OS and applications software w/o having to worry about wiping out data (also backed up off-site).

John

---

### Post by cigtoxdoc on 2014-07-22
This upgrade wipes out so many of your settings and files, you might as well start with a brand new PC.  For example, it has killed all printer and scanner drivers and settings, ikt has killed file permissions, and has setyup a new directory under my /media/ that was not there before and duplicated files from the two other directories under /media.  I am in two hours from getting a stable system and it looks like another two before I am back to where I was.

John

---

