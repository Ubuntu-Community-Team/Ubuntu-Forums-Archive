---
title: "Upgrade from 6.06 to 7.04"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by PintOfHarveys on 2007-09-17
I've installed 6.06 on a desktop PC and also a laptop. The desktop PC detected the available upgrade to 7.04 and is working fine.

However the laptop hasn't detected the available upgrade. Manually selecting the Update Manager (GUI version)  says the system is up to date. 

Am I missing some installation sources? What should they be?

The install from the 6.06 CD recognised the existing Windows XP installation and partitioned the disk accordingly and made it dual-boot. I tried a clean install from a 7.04 CD but it didn't recognise the WinXP or the 6.06 install and wanted to wipe the whole lot! I aborted that exercise.


Any suggestions on what to try?

Tony...

---

### Post by gautada on 2007-09-17
Seems a little strange does the laptop have a network connection?

---

### Post by PintOfHarveys on 2007-09-17
Internet connectivity is OK. 

"apt-get upgrade" returns a list of "http://'something'.ubuntu.com dapper" entries.

Over the last year, I'm sure that the regular 6.06 updates have been happening. 

Hence my original question - Am I missing some installation sources? What should they be? Does the laptop not know where to look for the upgrade to 7.04?

Tony...

---

### Post by gautada on 2007-09-18
Check System->Administration->Software Sources.  Make sure they are the same on the desktop and laptop.

---

### Post by PintOfHarveys on 2007-09-20
> **gautada said:**
> Check System->Administration->Software Sources.  Make sure they are the same on the desktop and laptop.

 /etc/apc/sources.list on the 7.04 machine is as follows.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe<br>
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe<br>

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted<br>
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted<br>

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe<br>
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe<br>

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse<br>
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse<br>

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse<br>

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main<br>

I've copied these over to the 6.06 machine and with a combination of Upgrade Manager and 'apt-get dist-upgrade', I seem to have managed to upgrade a whole load of applications and possibly even the kernel. System must be rebooted, it says, so I do. 

GRUB seems to have forgotten about the WinXP installation, and Ubuntu fails to boot anyway because it can't find /dev/hda6!

Ho hum,
Tony...

---

### Post by PintOfHarveys on 2007-09-20
> **PintOfHarveys said:**
> 

GRUB seems to have forgotten about the WinXP installation, and Ubuntu fails to boot anyway because it can't find /dev/hda6!


Rebooted from a live CD and re-enabled the partitions and everything boots OK, but as far as I can see I'm still running 6.06.

I think I'll wait till I get hold of a 7.10 install disk and re-install from scratch, as long as it recognises the WinXP partition.

Tony...

---

### Post by rsambuca on 2007-09-20
Whoa, whoa, whoa!!!

There is a very specific method of doing upgrades.  You have to go from Dapper to Edgy, and then to Feisty.  You will find the necessary info [here]("https://help.ubuntu.com/community/UpgradeNotes").

---

### Post by PintOfHarveys on 2007-09-24
Where were you a week ago? :-)

The first thing the instructions said was gksu "update-manager -c". I'd read and tried this before, and it didn't work (as in it didn't find any upgrades)

This time it told me, among other things, that an upgrade to 6.10 was available, so I tried installing the upgrade. It failed.

"Can't install 'unbuntu-desktop'", it said. followed by "Could not calculate the upgrade - an unresolvable problem occurred while calculating the upgrade."

Click Continue and the installer says 'restoring original system state', after which it's back at the beginning.


Looks like it's well and truly stuffed.

Tony...

---

### Post by Sef on 2007-09-24
Install by disk.  Either Live CD or alternate.

---

