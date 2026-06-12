---
title: "Completely Uninstall Plex Media Server"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by kid1000002000 on 2011-10-10
I sampled many of these programs, and now I want plex gone. Using synaptic, I uninstalled the plex media package, but anytime I resume from standby, I can see in the black/white command window (the one that shows when a pc is booting) that "plex-media-server" is starting or stopping. I want it gone; how would one go about doing this?

Thanks!

---

### Post by burningfly on 2012-12-06
If you still don't know how to do it, there is a solution here (I think)
[http://forums.plexapp.com/index.php/topic/31215-not-able-to-reinstall-plexmediaserver-on-ubuntu-how-to-completely-remove-pms/](http://forums.plexapp.com/index.php/topic/31215-not-able-to-reinstall-plexmediaserver-on-ubuntu-how-to-completely-remove-pms/)

Steps:
1)Run 
sudo apt-get purge plexmediaserver


2) Remove bulk of plex files
sudo rm -rf /var/lib/plexmediaserver


3) Remove plex user (very important!)
sudo userdel plex


4) Remove both /etc/init/plexmediaserver.conf and /etc/default/plexmediaserver
sudo rm /etc/init/plexmediaserver.conf
sudo rm /etc/default/plexmediaserver

---

### Post by howefield on 2012-12-06
Thanks for the info.

Old thread closed.

---

