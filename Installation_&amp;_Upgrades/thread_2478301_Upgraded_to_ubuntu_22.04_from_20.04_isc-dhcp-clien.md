---
title: "Upgraded to ubuntu 22.04 from 20.04 isc-dhcp-client isc-dhcp-common held back"
date: 2022-08-22
forum: Installation &amp; Upgrades
---

### Post by richtera on 2022-08-22
It's keeping two packages back and I don't know why or whether I should worry about it

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  isc-dhcp-client isc-dhcp-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Thanks
Andy

---

### Post by deadflowr on 2022-08-22
Try it with full-upgrade
```
sudo apt full-upgrade
```

---

### Post by &amp;KyT$0P# on 2022-08-22
Those are phased updates.  As long as you have at least version [4.4.1-2.3ubuntu2]("https://packages.ubuntu.com/jammy/isc-dhcp-client") of those packages installed, this is normal and nothing to worry about.

You can check all this by looking at output from running
```
apt-cache policy isc-dhcp-client isc-dhcp-common
```

---

### Post by sussexlad on 2022-08-23
Just for the record I have a similar issue affecting 4 packages

Calculating upgrade... Done
The following packages have been kept back:
  fprintd isc-dhcp-client isc-dhcp-common libpam-fprintd
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.

---

