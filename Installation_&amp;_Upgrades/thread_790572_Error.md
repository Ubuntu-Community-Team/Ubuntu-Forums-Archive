---
title: "Error???"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by darkblade8801 on 2008-05-11
so i am getting rdy to run the update manager and i came across the error that reads the following: 

pkg/tmp.ci'
E: /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu4~8.04.0mt1_i386.deb: failed to delete `/var/lib/dpkg/tmp.ci'
E: /var/cache/apt/archives/compiz-fusion-plugins-main_0.7.4-0ubuntu5_i386.deb: failed to delete `/var/lib/dpkg/tmp.ci'



can someone pls help with a few thing first i would like to know what the error is talking about and what i can do to fix i am pretty new to the ubuntu OS so any help would be gratefull. thx

---

### Post by Thirtysixway on 2008-05-11
Try restarting your computer, and make sure you run as sudo or root.

---

### Post by bapoumba on 2008-05-11
> **darkblade8801 said:**
> so i am getting rdy to run the update manager and i came across the error that reads the following: 

pkg/tmp.ci'
E: /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu4~8.04.0mt1_i386.deb: failed to delete `/var/lib/dpkg/tmp.ci'
E: /var/cache/apt/archives/compiz-fusion-plugins-main_0.7.4-0ubuntu5_i386.deb: failed to delete `/var/lib/dpkg/tmp.ci'



can someone pls help with a few thing first i would like to know what the error is talking about and what i can do to fix i am pretty new to the ubuntu OS so any help would be gratefull. thx
Could you please post the complete error message to :
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Is this with hardy ?

---

### Post by pro003 on 2008-05-11
it looks like you lost your internet connection...or did you have it in the first place...?

---

