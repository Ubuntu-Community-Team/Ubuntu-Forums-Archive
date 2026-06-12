---
title: "[Intel wireless] any news on Intel 4965 problems?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by kakyoism on 2008-10-30
Hi, I read about this [http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810")

Anyone know if there's gonna be a solution soon?

thx!

System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.)
Cannot reactivate Intel 3945/4965 wireless if booting with killswitch enabled

On laptops with Intel 3945 or Intel 4965 wireless chipsets and a killswitch for the wireless antenna, starting the system with the killswitch enabled (i.e., with wireless disabled) will prevent re-enabling the wireless by toggling the killswitch. As a workaround, users should boot the system with the killswitch disabled. A future kernel update is expected to address this issue.

---

### Post by oimon on 2008-10-31
Seems to be this bug here:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970/](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970/)
looks like a fix will be available soon as an update.

---

