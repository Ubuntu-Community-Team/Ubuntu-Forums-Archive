---
title: "problems trying to upgrade lucid 10.0.4 to next LTS"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by aironman on 2013-05-07
Hi everyone, it is my first time here in this forum. I am trying to upgrade this ubuntu system to the next LTS version and i am encountering some problems when i try  to upgrade.

cristina@cristina:~$ sudo apt-get -f install
Reading package lists ... done
Building dependency tree
Reading state information ... done
Correcting dependencies ... failed.
The following packages have unmet dependencies:
   libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
          Recommends: libc6-i686
   python-louis: Depends: liblouis0 (> = 1.7.0-2) but it is not installable
   ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver :: Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

If i try it with synaptic, the tool gives me 3 broken packages:

libc6, python-louis and ubuntu-minimal.

I cannot upgrade this packages using synaptic or doing a apt-get -f install and in the meanwhile i cannot upgrade the system. I cannot upgrade the system with a fresh install.


cristina@cristina:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

Thanx in advance

---

### Post by darkod on 2013-05-07
How about something like:
```
sudo apt-get install --reinstall libc6 libc-bin python-louis liblouis0
```

Also if you have any third party repositories it's best to disable them temporarily. And did you run also apt-get update first?

---

### Post by aironman on 2013-05-08
"How about something like:
 	Code:

 	
sudo apt-get install --reinstall libc6 libc-bin python-louis liblouis0 
Also if you have any third party repositories it's best to disable them temporarily. And did you run also apt-get update first?"


Hi darkod, thanks for the anwer, i have tried your proposal but unfortunately it does not work. also i have tried with this solution:

from 

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)
[h=2]Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS[/h] To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure. 

[LIST=1]
[*]Start System/Administration/Software Sources 
[*]On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close. 
[*]Press Alt-F2 and type update-manager -d 
[LIST=1]
[*]Click  the Check button to check for new updates.    If there are any updates  to install, use the Install Updates button to install them, and press  Check again after that is complete. 
[*]A message will appear informing you of the availability of the new release. Click Upgrade. 
[/LIST]
Follow the on-screen instructions.[http://ubuntuforums.org/newreply.php?p=12637573&noquote=1](http://ubuntuforums.org/newreply.php?p=12637573&noquote=1)
[/LIST]
 It gives me the same error, broken dependencie. Is not possible to upgrade from lucid to precise? or maybe i need to upgrade first to natty?

thanks in advance

---

### Post by darkod on 2013-05-08
This is not an issue with the upgrade itself. You have broken packages, and it's not letting the upgrade go forward because of that.

You have to solve the broken dependencies problem first.

Try removing all those packages with:
sudo apt-get remove --purge <packagename>

And you can try reinstalling them later.

---

### Post by s9032g@comcast.net on 2013-05-08
In the past I have read in this forum that you cannot jump up several versions in one step i.e. jump from 10.04 to 12.04 without the intervening releases (fully updated). A clean install my be your answer. More work, but it works.

---

### Post by ibjsb4 on 2013-05-08
> **s9032g@comcast.net said:**
> In the past I have read in this forum that you cannot jump up several versions in one step i.e. jump from 10.04 to 12.04 without the intervening releases (fully updated). A clean install my be your answer. More work, but it works.

[https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Desktops_10.04_LTS_to_12.04_LTS_.28Recommended.29](https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Desktops_10.04_LTS_to_12.04_LTS_.28Recommended.29)

---

### Post by fantab on 2013-05-08
The simplest way to upgrade is to do a clean install with the new version. It will be faster, simpler and hassle free. Back up your data first.

---

