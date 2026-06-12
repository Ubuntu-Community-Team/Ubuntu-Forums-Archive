---
title: "Upgrade from Ubuntu 14 to Ubuntu 16 failed at restart."
date: 2016-09-29
forum: Installation &amp; Upgrades
---

### Post by molosser on 2016-09-29
Hi,

I have a clean empty vps and the only way to get Ubuntu 16 is by installing Ubuntu 14 template and then upgrading to Ubuntu 16. Unfortunately, the upgrade always fail at the last stage when I need to restart the server. There's no indication of any error during the upgrade, it's just that when I input ```
y
``` in the end of the process to restart, the upgrade fail:

```
Failed to start reboot.target: Connection timed out
See system logs and 'systemctl status reboot.target' for details.
```

Here are the steps:

```
apt-get update && apt-get -y dist-upgrade
reboot
apt-get install --install-recommends linux-generic-lts-xenial`
reboot
```

Status before upgrading:

```
Operating System: Ubuntu 14.04.5 LTS
Kernel: Linux 4.4.0-36-generic
Architecture: x86_64
```

Then I ran:

```
do-release-upgrade
```

Any help is much appreciated.


Regards.



Edit:

After the failed reboot, the vps is completely frozen. Manual reboot from SolusVM doesn't work, terminal (port 22 and port 1022) doesn't work, selecting ```
N
``` before restart and restart manually ```
reboot -f
``` also doesn't work.

---

### Post by molosser on 2016-10-07
Any help?

---

