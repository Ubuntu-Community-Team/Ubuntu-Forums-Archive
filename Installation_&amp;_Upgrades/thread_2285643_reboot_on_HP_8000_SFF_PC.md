---
title: "reboot on HP 8000 SFF PC"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by donw35 on 2015-07-07
interesting issue with ubuntu 14.04 and Linux Mint 17.2, when either of these OS's are installed on this machine it will reboot, no error or log entry's, just shuts off and reboots. I tested this machine with Windows 7, Ubuntu 12.02 and Solaris 11 and its solid. The system would start rebooting as soon as 5 minutes regardless of what was running, nothing running or multiple apps. 

Specs,
E8400 CPU
4GB ram, I did change it out with no difference
built in Video
160 HD

Thanks for reading...

---

### Post by tgalati4 on 2015-07-08
It could be a graphics issue.  If the GPU locks up, then you normally won't get a system log entry, but check for errors anyway.  Open a terminal:

```
lspci | grep VGA
```

Then look at the X-session errors:

```
cd
more .xsession-errors
more /var/log/Xorg.0.log
```

Post anything that looks suspicious, which might look like:

```
tgalati4@Mint17 ~ $ grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.925] Initializing built-in extension MIT-SCREEN-SAVER
[ 88098.977] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[ 88099.028] (EE) intel(0): When reporting this, please include /sys/class/drm/card0/error and the full dmesg.

```

---

