---
title: "Server - Edgy - Need upgrade assistance"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by prrawls on 2008-06-18
Well I tried to do a;

sudo aptitude update 

Today and it looks like all the edgy repositories have been taken offline.   A not so gentle hint I guess that I need to upgrade my server installation to the newest distro.

I would like this upgrade to go as smoothly as humanly possible so if anyone could please direct me to a updated process for making this happen I would very grateful.

Thank you! :)

---

### Post by avtolle on 2008-06-18
FWIW, I used the procedure found at [https://help.ubuntu.com/community/FeistyUpgrades#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf](https://help.ubuntu.com/community/FeistyUpgrades#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf) to begin the upgrade from 6.10 to 7.04, then followed a similar procedure to eventually get to 8.04 server. While it took a long time, it went smoothly.

EDIT: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) is the starting point, and I apologize for not posting this above. Basically, I clicked on the link for 6.10 to 7.04, and got the above link; then, once that was completed, clicked on the link for 7.04 to 7.10, went to that page, and.... well, you get the picture.

Otherwise, as I think you know, you could d/l the iso for 8.04 server, and do a fresh install which may or may not go smoothly. I thought the sequential upgrade was a better choice for me, but YMMV. Good luck.

---

### Post by prrawls on 2008-06-18
Well since none of my respositories are working I can get the update manager installed :(

I get this on trying to install;

sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  python-apt python-central python-gnupginterface python-support
The following NEW packages will be installed:
  python-apt python-central python-gnupginterface python-support
  update-manager-core
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 233kB of archives.
After unpacking 1229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  python-central python-apt python-support python-gnupginterface
  update-manager-core
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main python-central 0.5.6ubuntu2
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main python-apt 0.6.19ubuntu9.1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main python-support 0.5.3ubuntu1
  404 Not Found [IP: 91.189.88.31 80]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main python-gnupginterface 0.3.2-9 [23.7kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main update-manager-core 0.56~edgy5
  404 Not Found [IP: 91.189.88.31 80]
Fetched 23.7kB in 15s (1542B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-central/python-central_0.5.6ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-central/python-central_0.5.6ubuntu2_all.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9.1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.5.3ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.5.3ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~edgy5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~edgy5_all.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This is the kind of thing that I was worried about.  Thanks again for the assistance.

---

### Post by Sef on 2008-06-18
> Otherwise, as I think you know, you could d/l the iso for 8.04 server, and do a fresh install which may or may not go smoothly. I thought the sequential upgrade was a better choice for me, but YMMV. Good luck.

A clean install is less problematic than an upgrade.  Upgrades have more problems than a clean install.

> This is the kind of thing that I was worried about. Thanks again for the assistance. 

Do a clean install.  You will have to set things up again as to how you had them, but Hardy Heron will be supported as a server for 5 years.

---

### Post by avtolle on 2008-06-18
Sorry that you ran into the problems you posted. It likely went better for me as I did the upgrade very soon after 8.04 was released. 

Sef is right with his advice, and, given where you are at, it seems a fresh install is your easiest option right now. Good luck.

---

### Post by prrawls on 2008-06-18
> **Sef said:**
> A clean install is less problematic than an upgrade.  Upgrades have more problems than a clean install.



Do a clean install.  You will have to set things up again as to how you had them, but Hardy Heron will be supported as a server for 5 years.

The only reason I prob won't do a clean install is that the machine is a VM - easy for me to roll back if things go south on me.  

Plus the knowing how to for me anyway is always a better option.

If anyine out there could let me know which repositories I should point at would be very helpful to get through the upgrade process.

Thanks again folks.

---

### Post by avtolle on 2008-06-18
Just a thought, and I know that this is NOT a method that is "approved". Edit your /etc/apt/sources.list by replacing every occurrence of edgy with feisty. Then, after that is done, run```
sudo apt-get update
``` and, if no errors occur, do```
sudo apt-get upgrade
```to get upgraded. Once this is done, then I'd do the suggested method to move from feisty to gutsy. This is at your own risk, as always, and I've not done it myself, but have read posts from others for whom it has worked.

---

### Post by avtolle on 2008-06-18
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual) for some other information on upgrading "manually" that may be of some help to you.

---

