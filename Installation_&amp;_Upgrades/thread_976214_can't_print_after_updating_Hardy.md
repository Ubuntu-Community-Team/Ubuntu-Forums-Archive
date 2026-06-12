---
title: "can't print after updating Hardy"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by karls0 on 2008-11-09
Hi,
today I updated my Hardy-installation, but kept kernel 2.6.24-19 because of VMware-server (i don't have the time to care about recompiling VMware server at the moment). After the update I was not able to print to my local parallel-printer (HP LaserJet1200). Print jobs were hlted after some 20 seconds. The ipp-info for the job showed a permission problem for /dev/lp0. /var/log/messages showed 
```
Nov  9 10:26:08 schuh-tv2 kernel: [  190.220727] audit(1226222768.763:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw
" name="/dev/tty" pid=6174 profile="/usr/sbin/cupsd" namespace="default"
```
As a quick help I just did a 
```
chmod 666 /dev/lp0
```
which helped to print.

Since I am not a LINUX-guru, I am uncertain if this is OK, or if it implies the possibility of other problems:confused:

Regards
Karl

---

### Post by karls0 on 2008-11-09
After reboot gain no printing. I looked into /dev
```
root@schuh-tv2:~# ls -l /dev/lp*
crw-rw---- 1 root lp 6, 0 2008-11-09 17:19 /dev/lp0
```

So my chmod is gone. This time I looked into the CUPS-settings more closely. In the security-tab I see "systemgroup: lpadmin" and in the filter-tab I see "group: lpadmin" :confused: Should I change these settings to lp, since the device has group lp set?

tia
Karl

---

### Post by karls0 on 2008-11-15
Hi again,
```
In the security-tab I see "systemgroup: lpadmin" and in the filter-tab I see "group: lpadmin"  Should I change these settings to lp, since the device has group lp set?
```
I tried this in the Systemsettings - but it didn't work too :(

Any help:confused:

Karl

---

