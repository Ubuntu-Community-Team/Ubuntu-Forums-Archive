---
title: "Upgrading from Breezy on AMD64"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by scapps on 2006-08-15
I am attempting to upgrade from Breezy to Dapper on an AMD64 pc.

I am using the following sources.list file to upgrade:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
##deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

##UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

I have executed:  sudo apt-get update and sudo apt-get dist-upgrade

when I run: apt-get install I get the following message:

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ia32-libs-kde: Depends: ia32-libs (>= 1.4ubuntu16) but 1.4ubuntu4 is installed
  ia32-libs-openoffice.org: Depends: ia32-libs (>= 1.4ubuntu17) but 1.4ubuntu4 is installed
E: Unmet dependencies. Try using -f.

when I run sudo apt-get -f install I get the following message:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.
2 not fully installed or removed.
Need to get 0B/3837kB of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 153662 files and directories currently installed.)
Preparing to replace ia32-libs 1.4ubuntu4 (using .../ia32-libs_1.4ubuntu20_amd64.deb) ...
dpkg-divert: rename involves overwriting `/usr/bin/ldd' with
  different file `/usr/bin/ldd.amd64', not allowed
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu20_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu20_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Not sure what else to try?  My system reboots back into Breezy.  I do not see an option to select the latest kernel 2.6.15 distributed with Dapper.  Any ideas?

](*,)

---

