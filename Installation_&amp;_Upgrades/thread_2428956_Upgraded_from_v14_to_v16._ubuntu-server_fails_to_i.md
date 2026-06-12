---
title: "Upgraded from v14 to v16. ubuntu-server fails to install due to open-vm-tools problem"
date: 2019-10-11
forum: Installation &amp; Upgrades
---

### Post by drinktea2 on 2019-10-11
After running an upgrade from v14 to v16, there was an error about open-vm-tools and ubuntu-server failing to upgrade at the end. It looks like ubuntu-server depends on open-vm-tools and the problem is with open-vm-tools:
"udevadm trigger is not permitted while udev is unconfigured."


I rebooted and tried manually upgrading but they fail to install.

Example output:

open-vm-tools is already the newest version (2:10.2.0-3~ubuntu0.16.04.1).
Setting up open-vm-tools (2:10.2.0-3~ubuntu0.16.04.1) ...
udevadm trigger is not permitted while udev is unconfigured.
dpkg: error processing package open-vm-tools (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-server:
ubuntu-server depends on open-vm-tools; however:
Package open-vm-tools is not configured yet.



I've tried completely removing open-vm-tools:

sudo apt-get remove open-vm-tools
rm -r /etc/vmware-tools


and also installing open-vm-tools manually:

sudo apt-get install open-vm-tools


But it always fails with this udevadm trigger is not permitted while udev is unconfigured. message.


Would you have any ideas on a fix for this?

---

### Post by Bashing-om on 2019-10-11
drinktea2; Hello - Welcome to the forum.

> 
Would you have any ideas on a fix for this?


Try:
```

sudo dpkg --configure --pending
sudo apt-get -f install

```

now what shows:
```

sudo dpkg --audit

```

[INDENT]maybe Yes
[INDENT][INDENT]might be not so yes
[/INDENT][/INDENT][/INDENT]

---

