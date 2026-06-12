---
title: "After upgrade for 16.04 to 18.04 no video resolutions opting in settings"
date: 2019-06-01
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-06-01
I just did a release upgrade from 16,.04 LTS to 18.04 LTS. It went far smother than any of my previous upgrade except for won thin.

When I restarted in 18.04 it started in low resolution 640xx480 and when the login screen came up it's still 640x480 and when I login it stays 640x480. After logging in and going to settings no resolutions are shown. 

I looked over the Internet and found a lot of detailed instructions to add specific resolutions, but no way to completely reset the resolutions.
I this happened because during the upgrade the old Nvidia driver I was using was deleted and nouveau was loaded in its place. 
```
# lspci |grep VGA  00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
```
I then removed and remnants of nvidia 
```
#sudo apt-get purge nvidia*
```
That worked after a reboot although there are configuration problems with some of the desktops.

---

### Post by rsteinmetz70112 on 2019-06-01
I've now completed the upgrade but uncovered a problem with the upgrade process.

When a system that has the samba winbind package is upgraded the necessary packages  libnss-winbind and libpam-winbind are not installed.

---

