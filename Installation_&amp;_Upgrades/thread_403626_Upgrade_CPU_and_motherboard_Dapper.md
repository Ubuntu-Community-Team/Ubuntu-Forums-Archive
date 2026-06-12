---
title: "Upgrade CPU and motherboard Dapper"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2007-04-07
I have an installation of Dapper LTS I like and would like to keep.  Unfortunately its running on a slow AMD Athlon XP processor which makes it borderline for videos.  If I installed a new motherboard and CPU (Intel) would I have to reinstall Dapper?  I plan to reuse the video card and I have new memory so total cost would be minimal.  Drives are SCSI.  Would it be just as simple as installing new parts, keeping exiting SCSI drives with Dapper  and booting up?   New CPU would have hyper-threading.
Thanks for the help.

---

### Post by bulldog on 2007-04-07
Boot in recovery mode and type in console```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Choose the desired options if available or choose the default.
Reboot and see how it goes.

---

