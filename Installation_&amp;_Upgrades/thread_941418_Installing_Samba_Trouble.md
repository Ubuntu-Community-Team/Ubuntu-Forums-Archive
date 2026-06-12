---
title: "Installing Samba Trouble"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by jaie on 2008-10-08
I have removed samba from my pc using:

sudo apt-get remove --purge samba

To completely remove it I deleted the /etc/samba directory to make sure all the config files were gone.

Upon reinstallation using this command:

sudo apt-get install samba

I get the following error:

Setting up samba (3.0.22-1ubuntu3.8 ) ...
* Starting Samba daemons...  [[COLOR="DarkRed"]fail[/COLOR]]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
  subprocess post-installation script returned error exit status 1
Errors were encouted while processing:
  samba


Can anybody help me to get samba installed again.

---

