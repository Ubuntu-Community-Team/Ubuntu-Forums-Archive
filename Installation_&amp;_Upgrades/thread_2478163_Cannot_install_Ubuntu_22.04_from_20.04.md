---
title: "Cannot install Ubuntu 22.04 from 20.04"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by Semn on 2022-08-18
Hi, using this procedure:


sudo apt update:
it:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
....
it:10 [http://ppa.launchpad.net/strukturag/libheif/ubuntu](http://ppa.launchpad.net/strukturag/libheif/ubuntu) focal InRelease      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it

sudo apt upgrade  :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


sudo apt dist-upgrade 

I get:

"Checking for a new Ubuntu release
Please install all available updates for your release before upgrading."




I can't find a solution online. 

Any ideas?
Thanks

---

### Post by SeijiSensei on 2022-08-18
Try "full-upgrade"

---

### Post by Semn on 2022-08-18
Got this:

sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by grahammechanical on 2022-08-18
The message is advice. It is sensible advice. If we run Software Updater the OS will be updated and at the end a dialog will appear. It has this message

> The software on this computer is up-to-date. However, Ubuntu 22.04.01 LTS is now available (you have 20.04) 

Underneath will be two buttons. Upgrade & OK. Click Upgrade if you want 22.04. Click OK if you want to continue using 20.04. For a few weeks Software Updater will give us the option to upgrade. 

Updating the system by running a APT command in the terminal will not give us an option. Only an advisory message. 

Regards

---

### Post by deadflowr on 2022-08-18
Look at what it shows that can be upgraded with the command
```
apt list --upgradable
```
It's possible the package listed as upgradeable cannot actually be upgraded in it's current state.
Perhaps there is a dependency that also needs to be upgraded too.

---

### Post by Semn on 2022-08-19
> **grahammechanical said:**
> The message is advice. It is sensible advice. If we run Software Updater the OS will be updated and at the end a dialog will appear. It has this message



Underneath will be two buttons. Upgrade & OK. Click Upgrade if you want 22.04. Click OK if you want to continue using 20.04. For a few weeks Software Updater will give us the option to upgrade. 

Updating the system by running a APT command in the terminal will not give us an option. Only an advisory message. 

Regards



Hi, I also found the way to upgrade via the icon "Software Upgrades", and when it checks for updates it finds the 22.04, but when I press "Upgrade", nothing happens. Absolutely nothing.

---

### Post by yancek on 2022-08-19
>  but when I press "Upgrade", nothing happens. 

Did you run the command below suggested by the system when you tried to upgrade?  If so, did you get the message below before or after you ran the command?  If you have not run this command, do that and look at the output as it may indicate what you need to do.

>  apt list --upgradable

---

### Post by Semn on 2022-08-24
> **yancek said:**
> Did you run the command below suggested by the system when you tried to upgrade?  If so, did you get the message below before or after you ran the command?  If you have not run this command, do that and look at the output as it may indicate what you need to do.

sudo] password for saem: 
Listing... Done
libheif1/focal 1.12.0-1~ppa1~ubuntu20.04.1 amd64 [upgradable from: 1.6.1-1build1]
opera-stable/stable 90.0.4480.54 amd64 [upgradable from: 89.0.4447.97]

---

