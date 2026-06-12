---
title: "dpkg &amp; automatic packets reinstallation after a crash disk"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by ublo on 2008-08-31
Hi,

Following a crash disk :(, I rebuild my pc with backup of sources & packets plus /home.
Unfortunately, the restore of my packets didn't works. If 1,2 Gb were downloaded, none of my favorite free softwares are installed ! :(:(

Here is the procedure,I've followed :

1-backups
* backup of /home
* backup of /etc/apt/sources.list,
* dpkg --get-selections "*" > MyPackets.txt
2-Restore
* copy of my /home
* add lines of sources not created by the system in sources.list
* sudo dpkg --set-selections < MyPackets.txt && sudo apt-get dselect-upgrade
* sudo apt-get update

an idea ?

@+

---

