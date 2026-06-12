---
title: "Problems upgrading"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by mussassa on 2017-01-23
Hello
I am having problems upgrading from ubuntu 14.04 to ubuntu 16.04.  I click the upgrade button, then I authenticate, but after that nothing happens.

---

### Post by reese1379 on 2017-01-23
> **mussassa said:**
> Hello
I am having problems upgrading from ubuntu 14.04 to ubuntu 16.04.  I click the upgrade button, then I authenticate, but after that nothing happens.

Upgrades can be problematical, best do a fresh install of 16.04 and copy over your personal files. Do you mind telling us what desktop you are using and where exactly this 'upgrade button' resides?

---

### Post by mussassa on 2017-01-23
> **reese1379 said:**
> Upgrades can be problematical, best do a fresh install of 16.04 and copy over your personal files. Do you mind telling us what desktop you are using and where exactly this 'upgrade button' resides?
Hi
I used to upgrade with no problem with the previous versions.  I am using a Lenovo laptop.  The upgrade button appears automatically, but I also get it from menu/Administration/Software Updater , it scans for updates and tells me that is up to date and gives me the option to upgrade to 16.04 LTS.

---

### Post by RobGoss on 2017-01-23
I strongly recommend doing a fresh installation as many of us would advise it will save you a lot of time. Make a backup of anything important and do a fresh installation and move forward.

Best of luck

---

### Post by ian-weisser on 2017-01-23
If you wish to upgrade to 16.04, then open a terminal and try the following command:
```
do-release-upgrade
```
If it fails, then please show us the complete output.

It is wise to completely uninstall all PPA and other non-Ubuntu software, and to disable those non-Ubuntu sources, before starting the process. If you uninstalled any standard applications or desktop metapackages, reinstall them. Try to return your system to as close to stock condition as possible. And, always, backup your data to prevent an unforseen minor frustration or bug from erasing years of your work and life. These lessons have been learned very painfully by others - prevention is very cheap, data recovery is very expensive.

WARNING: The do-release-upgrade command cannot be cancelled nor undone after the system has completed downloading the new packages. Make sure you want to commit, have plenty of time, and are using a reliable power supply.

---

### Post by mussassa on 2017-01-24
> **ian-weisser said:**
> If you wish to upgrade to 16.04, then open a terminal and try the following command:
```
do-release-upgrade
```
If it fails, then please show us the complete output.

It is wise to completely uninstall all PPA and other non-Ubuntu software, and to disable those non-Ubuntu sources, before starting the process. If you uninstalled any standard applications or desktop metapackages, reinstall them. Try to return your system to as close to stock condition as possible. And, always, backup your data to prevent an unforseen minor frustration or bug from erasing years of your work and life. These lessons have been learned very painfully by others - prevention is very cheap, data recovery is very expensive.

WARNING: The do-release-upgrade command cannot be cancelled nor undone after the system has completed downloading the new packages. Make sure you want to commit, have plenty of time, and are using a reliable power supply.
Thanks,it worked.

---

### Post by raja.genupula on 2017-01-24
+1 for terminal approach and always please mark your threads as solved once you got it fixed. 

This will save some time for us to look at other posts.

Thank you.

---

