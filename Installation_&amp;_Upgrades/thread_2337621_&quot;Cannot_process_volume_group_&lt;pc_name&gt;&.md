---
title: "&quot;Cannot process volume group &lt;pc name&gt;&quot; after upgrading 14.04 to 16.04"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by mandavi2 on 2016-09-20
After upgrading from 14.04 to 16.04 the boot process got stuck. Hitting CTRL + ALT + F2 revealed the message "A start job is running for Hold until boot process finishes up (Xmin Xs/no limit)".

I read that this is most likey caused by plymouth / video driver so I did the following: 
In rescue mode I activated the network and typed in the shell:
"sudo apt-get remove plymouth xserver-xorg-video-intel" and rebooted.

Now before I even get to unlock my encypted disc I get the message:

lvmedad is not active yet, using direct activation during sysinit
Volume group "laptop-hp" not found
Cannot process volume group laptop-hp

Since I still have the old kernel version, choosing that I do get to unlock the encrypted disc and after a while of booting the screen turns black. CTRL + ALT + F2 askes me to login. But no grafical login.

---

