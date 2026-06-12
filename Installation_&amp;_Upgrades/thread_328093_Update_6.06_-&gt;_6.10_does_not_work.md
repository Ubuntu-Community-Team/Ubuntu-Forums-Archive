---
title: "Update 6.06 -&gt; 6.10 does not work"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by amsch on 2006-12-30
I tried to upgrade my Kubuntu Installation from 6.06 to 6.10 but I get the following error:

xx@neo:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-core: Depends: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 is installed
E: Unmet dependencies. Try using -f.
xxx@neo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  x11-common xserver-xorg
The following packages will be upgraded:
  x11-common xserver-xorg
2 upgraded, 0 newly installed, 0 to remove and 822 not upgraded.
40 not fully installed or removed.
Need to get 0B/460kB of archives.
After unpacking 664kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing xserver-xorg (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
xxx@neo:~$ Errors were encountered while processing:
 xserver-xorg


I used "Upgrading from 6.06 LTS" instructions from [http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php)

Can anybody help me please? How can I reinstall this - I fI use Adept Package Manger I get the same error and Im now afraid to reboot my PC since X wont work (I guess?)

---

### Post by taurus on 2006-12-30
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by amsch on 2006-12-30
I have solved the problem now - I had to force remove of xorg server and now the update worked!

---

