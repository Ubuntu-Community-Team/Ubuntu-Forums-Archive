---
title: "Problem after running upgrade kernel"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by satimis on 2013-12-16
Hi all,

Ubuntu 12.04 64bit

Just having run upgrade kernel and 2 addition packages (pls see attached files).  Computer can't be booted.

Warning:
The system is running in low graphic mode .......

I'm now compelled booting previous kernel.  On googling I found many similar problems (old threads) with many suggestions.  I hesitate which shall I follow.  Please help

TIA

Rgds
satimis

---

### Post by Bashing-om on 2013-12-18
satimis; Hello again;

See if this helps;
Run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
With the expectation that "dist-upgrade" will install the current kernel images.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by satimis on 2013-12-18
Hi all,

Thanks for your advice.

I suppose the problem orignated from Ubuntu, the previous packages for update and upgrade.  I have 2 PCs, a daily working PC and a spare PC, both running Ubuntu desktop 12.04, 64bit.  Both got problem after running update and upgrade previously.  I have been spending nearly a week trying to fix the problem witout result.

On the spare PC I have another HD, a spare HD, with Ubuntu 10.04 (LTS) installed several years back.  The OS has been upgraded regularily.  Yesterday I booted this HD.  On running update and upgrade with apt-get;

$ sudo apt-get update && sudo apt-get upgrade```

.......
Building dependency tree      
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic nvidia-current
  nvidia-settings
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up colord (0.1.16-2ubuntu0.1) ...
dpkg: error processing colord (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 colord
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I ran
$ sudo aptitude update && sudo aptitude upgrade

It went through without complaint.  After reboot it works without problem.  The kernel "is 3.2.0-57-generic x86_64" (see attached screenshot").  It clarifies the doubt on hardware problem.


Now I'm prepared to wipe out the Ubuntu OS on both PCs.  On the spare PC I'll install Debian 7.2 as host and download/install VirtualBox, the latest version.  On the working PC I'll install Ubuntu 12.04.3 as host and install VirtualBox download on Ubuntu repo.  Otherwise I don't know whether I can finally fix the existing problem on both PCs.  Neither I can forecast how many days I'll further spend for sorting out the problem. 

The only remaining problem is to find enough space for storing about 500G data including the VM images on both PCs.  I'll sorted out this problem later.  

Anyway, lot of thanks for your help.

Rgds
satims

---

### Post by satimis on 2013-12-19
Hi all,

After copying all data to the spare HD I made a last check on user accounts to see whether there are data which I haven't copied.  I can't remember exactly how many users have been created in the past because this box was built >5 year ago.

On -> System Settings -> User Accounts
I found the user-satimis was locked.  After unlocking it the menu bars, top and side, come back.  I have rebooted the PC several times including shutdown making sure it works.

It is quite strange to me running update and upgrade will cause locking the administrator's account.

Rgds
satimis

---

