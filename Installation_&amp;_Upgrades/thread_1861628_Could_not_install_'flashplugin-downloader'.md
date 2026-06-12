---
title: "Could not install 'flashplugin-downloader'"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by PCCARVER on 2011-10-15
Just upgrade 11.04 to 11.10 and received the following message...

Could not install 'flashplugin-downloader'

The upgrade will continue but the 'flashplugin-downloader' package may not be in a working state.

subprocess installed post-installation script returned error exit status 1

i have since researched the release notes and found...

Users upgrading may encounter error messages from the installation of  the new version of flashplugin-installer, due to some user connections  (e.g. wifi, 3G) becoming unavailable during the upgrade process. It is  recommended to proceed with upgrades while connected to a wired network  to avoid this type of issue. ([859373]("https://bugs.launchpad.net/bugs/859373")) 

Once I hardwire my network connection, what command(s) would I issue to restart the flashplugin-installer? 

Thanks for Ubuntu and everyone's support, it has given new life to my Sony Viao PCG-TR2AP as Windows XP was strangling it!

---

### Post by oldos2er on 2011-10-15
Try ```
sudo apt-get update && sudo apt-get install flashplugin-downloader
```

---

### Post by lsward on 2011-10-15
I had the same issue and the terminal command above took care of the problem.  Thanks for the help.

---

### Post by PCCARVER on 2011-10-16
This worked perfectly! As a side note, although using wifi during the initial upgrade caused the failed install, restarting the flashplugin-installer with only the wifi connection completed succesfully. Thanks!

---

### Post by megamasha on 2011-11-16
I had a message that, when it said there was update available for this package, when it came to try to update it, it claimed the package was not found on my computer or any configured software source.

This same command fixed that too.

---

