---
title: "Failed to download package files"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by LitlWillie on 2016-12-19
My installation is Ubuntu 16.04 LTS an upgrade from 12.04 LTS

On a check for updates I got the following error message

**Failed to download package files**

**Check your Internet connection.**

The details are:

Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_i386.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_i386.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_i386.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_i386.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/u/unattended-upgrades/unattended-upgrades_0.90ubuntu0.1_all.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/u/unattended-upgrades/unattended-upgrades_0.90ubuntu0.1_all.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-common_1.18.4-0ubuntu0.1_all.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-common_1.18.4-0ubuntu0.1_all.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-legacy_1.18.4-0ubuntu0.1_i386.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-legacy_1.18.4-0ubuntu0.1_i386.deb) 404  Not Found [IP: 64.50.233.100 80]
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.18.4-0ubuntu0.1_i386.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.18.4-0ubuntu0.1_i386.deb) 404  Not Found [IP: 64.50.233.100 80]

Thanks in advance for your help.

---

### Post by bearlake on 2016-12-19
You need to comment out those lines as it's not supported in xenial.

Usually in your Repositories and Other Software.

---

### Post by ian-weisser on 2016-12-19
The 404s are accurate.
Look at the version numbers

Example xserver-common.
Current 16.04 is 1.18.4-0ubuntu0.2 in xenial-updates 
You are trying to install 1.18.4-0ubuntu0.1, an older version, which has been replaced by 0.2

The simple solution is to update your package database. Make sure your mirror works, and that the database files really download (no errors).
```
sudo apt update
```

0.2 replaced 0.1, according to the changelog, on 01 November - have you had this problem for six weeks?

Once you are sure you have a good database update, then try upgrading again.

---

