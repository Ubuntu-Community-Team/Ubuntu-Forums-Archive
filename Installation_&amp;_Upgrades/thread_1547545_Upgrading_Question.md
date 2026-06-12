---
title: "Upgrading Question"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by BlazeFire247 on 2010-08-06
I have a question when upgrading with Wubi:

When 10.10 gets released, I plan to upgrade, but I'm using Wubi. Is it safe to upgrade using this method:

> Network upgrade for Ubuntu desktops (Recommended)

You can easily upgrade over the network with the following procedure.   
Start System/Administration/Update Manager.  
Click the Check button to check for new updates.  
If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.  
A message will appear informing you of the availability of the new release. 
 
Click Upgrade.  
Follow the on-screen instructions. 

This is from the [Ubuntu website]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade").

---

### Post by lemming465 on 2010-08-07
> **BlazeFire247 said:**
> When 10.10 gets released, I plan to upgrade, but I'm using Wubi.

It should be fine; I've done it in the past.  I like to test with a live CD before doing upgrades, personally, just in case of any video or other regressions.

WUBI installs result in an ordinary Linux kernel running against and ordinary ext3 or ext4 filesystem, and the upgrade runs against those.  The fact that there is an extra layer of NTFS filesystem between the loopback mounted ext4 root and the actual hard drive shouldn't matter to the upgrade.

---

### Post by bcbc on 2010-08-07
Just back up the your root.disk before the upgrade. If it fails copy it back over. This isn't a bad idea anyway as there's no way to undo an upgrade and if you decide you prefer 10.04 after the fact you can't go back.

The other thing you can do is watch the forums for any issues before deciding to upgrade. 

Some wubi installs have other virtual disks e.g. a  usr.disk or home.disk. If you have these, you'd need to back these up too.

---

