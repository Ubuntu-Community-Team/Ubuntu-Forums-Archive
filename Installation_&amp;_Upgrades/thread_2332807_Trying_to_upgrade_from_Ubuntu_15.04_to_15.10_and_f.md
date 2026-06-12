---
title: "Trying to upgrade from Ubuntu 15.04 to 15.10 and finally to 16.04 (says it updated)"
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by dingel on 2016-08-04
Hi All ,
Glad to join this amazing forum.
i have ubuntu 15.04 :


Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid

am trying to do : sudo do-release-upgrade -dit keeps telling me that my system is up to date :log is here [https://favad.blob.core.windows.net/test/screenlog.zip](https://favad.blob.core.windows.net/test/screenlog.zip)
i followed [http://ubuntuhandbook.org/index.php/2015/10/upgrade-ubuntu-15-04-to-ubuntu-15-10/](http://ubuntuhandbook.org/index.php/2015/10/upgrade-ubuntu-15-04-to-ubuntu-15-10/)

can someone please help me understand the issue ?
thank you all again.

---

### Post by grahammechanical on 2016-08-04
Do not use "do-release-upgrade -d" unless you want to upgrade to the present development version of Ubuntu (16.10). The -d switch = development version.

See the section Upgrading to development releases

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Now, here is the problem. Ubuntu 15.04 is way, way out of life and Ubuntu 15.10 has just recently become out of life. It is not so easy to upgrade from an out of life release especially if the next release is also out of life. It might be possible to go directly to 16.04 but some have had problems. You might be better off backing up your data and doing a fresh install of 16.04.

This book that you referenced says this
> 
2. After that, launch Software Updater via below command:

 sudo update-manager -d

Then it says this if it is the server edition that we are wanting to upgrade
> 
4. Finally upgrade Ubuntu Server via command:

 sudo do-release-upgrade -d

At this point I repeat, see the Ubuntu wiki page I linked to above and look under the section Upgrading to the development version.

This is how to do an upgrade from a end of life version of Ubuntu

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But you might try opening Software & Updates and changing the setting from Notify me of the next release of Ubuntu to Notify me of the next LTS release of Ubuntu and then update. You may get Update Manager offering an upgrade to 16.04.

Regards

---

### Post by dingel on 2016-08-05
Thanks,
the funny thing is that i have some more copies of the same distro and i managed to upgrade.
you think it worth a shot to canonical ?
thanks

---

### Post by kansasnoob on 2016-08-05
From the attached log it looks like you did upgrade to Wily (15.10) so what does it show when you run :

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Please post the output of those two commands and we'll see.

---

### Post by dingel on 2016-08-05
apt-get update :
 sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-backports/universe Translation-en
Reading package lists... Done
dist upgrade :
:/etc/apt$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by kansasnoob on 2016-08-05
So you're on Wily now, just one more step to getting Xenial. What's the output of:

```
cat /etc/update-manager/release-upgrades
```

---

