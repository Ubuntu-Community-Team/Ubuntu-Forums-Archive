---
title: "auto-upgrade not working"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dcdano2007 on 2010-05-10
Greetings:  I am currently running Ubuntu 9.10.  I have upgraded twice via the 'update manager' from previous versions.  However, the new version 10.04 will not auto-upgrade.  I don't even get the option to select the upgrade when running update manager.  I do get the following error msg when running update manager however:

W: GPG error: [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C95104E509BAC46D

I believe this is due to the remnants of an old Samsung printer driver.  Ive tried to delete the driver via 
sudo /opt/Samsung/mfp/uninstall/uninstall.sh
but I still get the error message anyway.  I am working on a Toshiba Portege Laptop.  Any thoughts?

---

### Post by markthecarp on 2010-05-10
> **dcdano2007 said:**
> Greetings:  I am currently running Ubuntu 9.10.  I have upgraded twice via the 'update manager' from previous versions.  However, the new version 10.04 will not auto-upgrade.  I don't even get the option to select the upgrade when running update manager.  I do get the following error msg when running update manager however:

W: GPG error: [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C95104E509BAC46D

I believe this is due to the remnants of an old Samsung printer driver.  Ive tried to delete the driver via 
sudo /opt/Samsung/mfp/uninstall/uninstall.sh
but I still get the error message anyway.  I am working on a Toshiba Portege Laptop.  Any thoughts?

You will need to disable that repository and key. Your post indicates only the key is offending; however I bet that if you only disable (comment out) the key you'll just get another error.

This involves editing files or use the gui tools to disable all third party repositories...Need help with that?

I'd disable (comment out) the possibly offending repos then run another "sudo apt-get update && sudo apt-get (dist-)upgrade" The upgrade first, then dist-upgrade. 

-mark

---

### Post by dcdano2007 on 2010-05-10
thanks for the help/info.....

Yes I will need some help with this...I am amateur at best with Ubuntu...
-DANO-

---

### Post by dcdano2007 on 2010-05-10
I went into Synaptic Package Manager....settings.....repositories....other software and unclicked the uwmichigan line.   Reloaded synaptic package manager - no errors.  Next went to update manager and ran it.   No error messages.  BUT, no button for auto upgrade displayed either....as if there is no new software to be upgraded to....

Any thoughts?

---

### Post by narendraD on 2010-05-10
I would suggest you don't do an upgrade at all and instead do a fresh install instead. You mention you have upgraded twice already. While that not a reason for anything to break or fail, I would recommend a fresh install. 
Backup all your data and settings from /home and list all installed applications and then do a fresh install. The forums are rife with posts of failed upgrades or upgrades that needed more than normal effort to get right.

A fresh install would be better also because you will get a new filesystem in ext4 and other benefits.

---

