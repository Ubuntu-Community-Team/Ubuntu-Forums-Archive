---
title: "Install Server version then add Gnome?"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by calelettus on 2009-12-17
I have a box I want to use for simple file storage/server use and have two 1T drives i'd like to use in a RAID1 configuration. I do need to use the box as a workstation once in a while and for that I'd like the gnome desktop installed. 

Rather than install Ubuntu **then** do the RAID configuration it seems like it would be easier for me to install the server version because it includes the RAID configuration option during install (where the desktop version does not) **then **apt-get the gnome desktop.

Can anyone confirm this would be the best way for me to proceed?

Thanks!

---

### Post by lewisforlife on 2009-12-17
Yes, install the server edition first to get the raid up and running, and I have heard Samba is a lot easier to get working from the initial server install, then do a:

```
sudo apt-get install ubuntu-desktop
```

to install Gnome.

---

