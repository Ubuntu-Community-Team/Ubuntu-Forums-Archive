---
title: "installing only the programs i want"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by ydnar on 2007-04-07
i'm planning on ditching the microsoft route for good and wanted to more or less do an ubuntu setup from the ground-up using the server install of feisty.

basically i only want firefox, wifi-radar (not nm), multimedia codecs, no openoffice, etc.

to do this, once i've completed the server install, is "sudo apt-get install gnome gdm" all i'd need to run at first? are there any guides or alternatives on building ubuntu using this method? thanks a lot in advance for helping this noob out.

---

### Post by aysiu on 2007-04-07
I think you should start with this: ```
sudo apt-get update && sudo apt-get install firefox openoffice.org gconf-editor gnome-applets gnome-icon-theme gnome-menus gnome-panel gnome-session gnome-system-tools gnome-themes gnome-utils gtk2-engines gdm xorg gksu synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` The rest you can install with Synaptic.

---

