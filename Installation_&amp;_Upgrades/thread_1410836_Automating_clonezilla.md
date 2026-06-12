---
title: "Automating clonezilla"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by J V on 2010-02-19
I am trying to set up clonezilla on pxe so that it will start up and show the drones in the workplace a list of images, they choose the one named after the model of computer, and image it.

Which means all clonezilla settings but image need to be set and it should automatically choose default settings at 1024x768 when grub pops up...

I have looked for command-line options, scripts to run, etc... so far this is what I have...

```
#!/bin/bash
. /opt/drbl/sbin/drbl-conf-functions
. /opt/drbl/sbin/ocs-functions
. /etc/ocs/ocs-live.conf

ocs_live_run=`ocs-live-restore`
ocs_live_extra_param=`-p reboot -r hda`
ocs_live_keymap=`NONE`
ocs_live_batch="no"
ocs_lang="en_US.UTF-8"
ocs_daemonon=`samba`

```Admittedly, I dont have a clue here... Nothing in the documentation.

I don´t need the bash for selecting the image, but you might as well add that seeing as theres almost no info online for people who want a pxe server...

---

### Post by J V on 2010-02-20
bump please?

---

### Post by J V on 2010-02-21
No-one used clonezilla in pxe? :/

---

