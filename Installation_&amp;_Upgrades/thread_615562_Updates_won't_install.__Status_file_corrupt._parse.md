---
title: "Updates won't install.  Status file corrupt. parse error"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by ejs7597 on 2007-11-17
When I try to run the updates, it errors out while trying to install gnome-panel.  
If I try to run 
sudo apt-get install -f
I get the following error message.

dpkg: parse error, in file `/var/lib/dpkg/status' near line 8180 package `gnome-panel':
 field name `M' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

  I read in another post to edit the status file with gedit, but when I try to open that file, it says it is a binary file and won't open it.  kwrite will open it, with the same warning, but I can't modify it or save it.  Is there a way to make the status file rebuild itself, or what is the proper way to edit the file?

---

