---
title: "update manager not working"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by gamepro1023 on 2008-11-03
I live on a college campus and the only internet that I have access to is a wireless network. I tried upgrading to 8.10 last night and was right in the middle of the download when the wi-fi network stopped working and my download was cut off in the middle. When I re-established my connection with the network and went back into my update manager to try to download it again, the new version was not even an option to pick, even when I refreshed the update manager. Any ideas on how I could get it back (or just upgrade in general) would be good. I'm trying to avoid having to do a clean install, and just update

---

### Post by ChrisShUK on 2008-11-03
Have you tried this,
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
:)

---

### Post by cdtech on 2008-11-03
If you had any packages that were interrupted or failed to install, you could use:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
to reconfigure the already downloaded portions and this should get you back to the portions that were not upgraded.

Hope this helps ya....

---

