---
title: "Minimum Compiz with Minimal CD?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by LaneLester on 2010-12-18
I have several partitions on my first drive that I use for *buntu distros. I enjoy trying out the newest releases while maintaining an install I can count on.

One combo I've learned to enjoy is a **Minimal CD** (mini.iso) install followed by a script that installs just the stuff I want. I just became enthusiastic about **Cairo Dock**, after finding the Natty dock too simplistic... at least for now. Here's my install script for a Maverick with Cairo:
```
#!/bin/sh
# After the base system is installed, set root pw, log in and use nano to uncomment repositories.
# Execute this script.
# Install nvidia-current after reboot.
# Copy over working xorg.conf (/mnt/arc/ZipLinux/MinimalCD/).
apt-get update
apt-get install xorg xterm gdm openbox compiz cairo-dock conky menu chromium-browser firefox filezilla checkgmail emelfm2 bluefish gedit evince alarm-clock galculator gnucash geeqie feh gimp alsa-base alsaplayer-text totem bleachbit alsa-utils alsamixergui ia32-libs cups foomatic-db foomatic-db-gutenprint system-config-printer-gnome samba zip unzip xfburn synaptic --no-install-recommends
service gdm start
```

I had to add **compiz** to get fancy Cairo Dock behavior, and I'm wondering if I could eliminate either or both of **gdm** and **openbox**, or do I need them **both**?

---

