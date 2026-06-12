---
title: "So my grub suddenly stopped prompting me for the HD/root password on my Docked monito"
date: 2024-09-16
forum: Installation &amp; Upgrades
---

### Post by nariub on 2024-09-16
So my grub suddenly stopped prompting me for the HD/root password on my Docked monitors in 22.04 after a recent update


After I enter the HD encryption password, it continues the boot and brings me to the gnome login fine.. but this is the specific reason I had declined to install 24.04 on my new laptop..


It is annoying that the 'feature' caught up to me without the upgrade. Might I ask how to get the previous behavior back where it display the grub prompt for HD password on the external monitors and not solely on the laptop's built-in monitor (the laptop is closed and in a docking station by the way)
  
  
Reasonably sure one of these recent updates changed the behavior of my system.


--  snip of less /var/log/apt/history.log --


Start-Date: 2024-09-13  08:01:18
Commandline: /usr/bin/unattended-upgrade
Upgrade: linux-libc-dev:amd64 (5.15.0-119.129, 5.15.0-121.131)
End-Date: 2024-09-13  08:01:19


Start-Date: 2024-09-13  08:01:23
Commandline: /usr/bin/unattended-upgrade
Upgrade: linux-tools-common:amd64 (5.15.0-119.129, 5.15.0-121.131)
End-Date: 2024-09-13  08:01:24


Start-Date: 2024-09-13  14:11:07
Commandline: aptdaemon role='role-commit-packages' sender=':1.126'
Upgrade: python3-distupgrade:amd64 (1:22.04.19, 1:22.04.20), language-pack-en-ba
se:amd64 (1:22.04+20240212, 1:22.04+20240902), apt:amd64 (2.4.12, 2.4.13), googl
e-chrome-stable:amd64 (128.0.6613.119-1, 128.0.6613.137-1), libapt-pkg6.0:amd64 
(2.4.12, 2.4.13), ubuntu-drivers-common:amd64 (1:0.9.6.2~0.22.04.6, 1:0.9.6.2~0.
22.04.7), ubuntu-release-upgrader-gtk:amd64 (1:22.04.19, 1:22.04.20), language-pack-en:amd64 (1:22.04+20240212, 1:22.04+20240902), language-pack-gnome-en-base:amd64 (1:22.04+20240212, 1:22.04+20240902), python-apt-common:amd64 (2.4.0ubuntu3, 2.4.0ubuntu4), base-files:amd64 (12ubuntu4.6, 12ubuntu4.7), python3-apt:amd64 (2.4.0ubuntu3, 2.4.0ubuntu4), language-pack-gnome-en:amd64 (1:22.04+20240212, 1:22.04+20240902), apt-utils:amd64 (2.4.12, 2.4.13), ubuntu-release-upgrader-core:amd64 (1:22.04.19, 1:22.04.20), shim-signed:amd64 (1.51.3+15.7-0ubuntu1, 1.51.4+15.8-0ubuntu1)
End-Date: 2024-09-13  14:11:37


Start-Date: 2024-09-16  12:48:55
Commandline: /usr/bin/unattended-upgrade
Upgrade: python3.10:amd64 (3.10.12-1~22.04.5, 3.10.12-1~22.04.6), libpython3.10-minimal:amd64 (3.10.12-1~22.04.5, 3.10.12-1~22.04.6), libpython3.10-stdlib:amd64 (3.10.12-1~22.04.5, 3.10.12-1~22.04.6), libpython3.10:amd64 (3.10.12-1~22.04.5, 3.10.12-1~22.04.6), python3.10-minimal:amd64 (3.10.12-1~22.04.5, 3.10.12-1~22.04.6)
End-Date: 2024-09-16  12:48:58


Start-Date: 2024-09-16  12:49:01
Commandline: /usr/bin/unattended-upgrade
Upgrade: libcurl4:amd64 (7.81.0-1ubuntu1.17, 7.81.0-1ubuntu1.18), libcurl4:i386 (7.81.0-1ubuntu1.17, 7.81.0-1ubuntu1.18)
End-Date: 2024-09-16  12:49:02


Start-Date: 2024-09-16  12:49:05
Commandline: /usr/bin/unattended-upgrade
Upgrade: libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.17, 7.81.0-1ubuntu1.18), libcurl3-gnutls:i386 (7.81.0-1ubuntu1.17, 7.81.0-1ubuntu1.18)
End-Date: 2024-09-16  12:49:05
-- end snip --

---

### Post by nariub on 2024-09-17
And today the behavior reverts.. disregard

---

