---
title: "Automount directory changed?"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by oliver-dolny on 2014-09-13
Hi, I just upgraded to Ubuntu 14.04 from 12.04 and was surprised that some of my skripts did not find their data anymore. It took me quite some time to find out, that hard disks which are not listed in fstab are not mounted to /media/... anymore, but to /media/username/... Is there a way to change back that behavior?

Thanks for your help!

---

### Post by Dennis N on 2014-09-13
Since 12.10, we use udisks2 to automount devices. It seems to be hard coded to use /media/<user>/<device> for automounting usb devices, and also for mounting devices from within the file manager. You could disable the automount and create your own mount points in a script: 

Xubuntu: 

Settings > Removable Drives and Media > uncheck the boxes "Mount Removable Drives..." and "Mount Removable Media..."

---

### Post by oliver-dolny on 2014-09-13
Thanks for the quick answer. Then it is probably best to use the -noauto option in fstab.

---

