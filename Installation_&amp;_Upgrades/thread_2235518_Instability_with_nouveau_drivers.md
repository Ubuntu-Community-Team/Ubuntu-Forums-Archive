---
title: "Instability with nouveau drivers"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-21
I thought that I had my secretary's PC stable after doing the HWE upgrade over the weekend.  Not so.  Video display is locking-up randomly at login or thereafter.  I have used latest version of Boot-Repair CD-ROM, and it "fixed" problem for a while.  Then I tried dpkg-reconfigure xserver-xorg -phigh.  That is gotten things to point where my sectretary can work.  There is no xorg.conf file.  No nVidia drivers are loaded.  When I look at /var/log/Xorg.0.log (copy attached), I see error messages:

5.860 (EE) Failed to load module "nvidia" (module does not exist, 0)

5.863 (EE)  Failed to load module "nv" (module does not exist, 0)

How does one correct these problems?

Thank you,

John

---

### Post by sp40140 on 2014-07-22
Have you tried to install Prop Nvidia drivers? Any reason for not using those?

---

