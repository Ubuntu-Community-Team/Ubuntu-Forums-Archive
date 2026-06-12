---
title: "Bluetooth devices not found after 7.04 upgrade"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by ramon_nsi on 2007-06-27
After upgrading to Feisty, I was getting no bluetooth devices listed by hcitool... hciconfig would show blank bluetooth IDs, yet lsusb showed the bluetooth devices were being detected. A hciconfig hci<x> reset would fix the problem temporarily, however upon further investigation I realised that the bluetooth service had changed from /usr/sbin/sdpd in v6.xx to /usr/sbin/hcid in v7.04 which ultimately appeared to be the root cause of my problem.

After the upgrade, when running hcitool, i would get -

root@lbot:~# hcitool dev
Devices:
root@lbot:~#

Checking the running services, no hcid was found... in /etc/init.d I found two Bluetooth services, namely ‘bluetooth’ & ‘bluetooth.dpkg-dist’… the ‘bluetooth’ service was attempting to run /usr/sbin/sdpd, which is no longer present in 7.04… the ‘bluetooth.dpkg-dist’ is the correct service, hence I just copied it over the existing /etc/init.d/bluetooth, and restarted the service (e.g. /etc/init.d/bluetooth restart)… ps -eaf then showed hcid running, and hcitool began to work -

root@lbot:~# hcitool dev
Devices:
        hci0    00:11:67:5F:80:8A
        hci1    00:11:67:5F:7F:C5
root@lbot:~#

---

