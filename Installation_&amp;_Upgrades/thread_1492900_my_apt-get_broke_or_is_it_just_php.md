---
title: "my apt-get broke or is it just php?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by ulao on 2010-05-25
what could be going on here.

Sorry for the long log but figure something in there is a clue. Also can I install php without apache2, is apache no good for php?


> 
root@ubuntuspawn:~# sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet1 libnids1.21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5 php5-common
0 upgraded, 5 newly installed, 0 to remove and 213 not upgraded.
Need to get 4115kB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2.2-common apache2-mpm-prefork php5-common libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main apache2.2-common 2.2.3-3.2u
buntu2.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2.2-common 2.2.3-3.2ub
untu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2-mpm-prefork 2.2.3-3.
2ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5-common 5.2.1-0ubuntu1.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libapache2-mod-php5 5.2.1-0u
buntu1.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5 5.2.1-0ubuntu1.6
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-)
common_2.2.3-3.2ubuntu2.1_i386.deb  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mp](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mp)
m-prefork_2.2.3-3.2ubuntu2.1_i386.deb  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5)
.2.1-0ubuntu1.6_i386.deb  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mo](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mo)
d-php5_5.2.1-0ubuntu1.6_i386.deb  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0u](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0u)
buntu1.6_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis
sing?
root@ubuntuspawn:~# apt-get update
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntuspawn:~# sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet1 libnids1.21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5 php5-common
0 upgraded, 5 newly installed, 0 to remove and 213 not upgraded.
Need to get 4115kB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2.2-common apache2-mpm-prefork php5-common libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main apache2.2-common 2.2.3-3.2ubuntu2.1
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2.2-common 2.2.3-3.2ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2-mpm-prefork 2.2.3-3.2ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5-common 5.2.1-0ubuntu1.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libapache2-mod-php5 5.2.1-0ubuntu1.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5 5.2.1-0ubuntu1.6
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.3-3.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.3-3.2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.3-3.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.3-3.2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.6_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.6_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.6_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntuspawn:~# sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet1 libnids1.21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5-common
0 upgraded, 4 newly installed, 0 to remove and 213 not upgraded.
Need to get 4114kB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2.2-common apache2-mpm-prefork php5-common libapache2-mod-php5
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main apache2.2-common 2.2.3-3.2ubuntu2.1
  404 Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2.2-common 2.2.3-3.2ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main apache2-mpm-prefork 2.2.3-3.2ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5-common 5.2.1-0ubuntu1.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libapache2-mod-php5 5.2.1-0ubuntu1.6
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.3-3.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.3-3.2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.3-3.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.3-3.2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.6_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.6_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntuspawn:~#


---

### Post by ulao on 2010-05-25
--Ok I see my issue is the apt-get sources.  What sources can I use for 7.04 server. I find a lot of examples on the net but everything is 404?

---

### Post by maithili on 2010-06-22
If the error is "no MPM package installed" when you restart your apache, then go to system->administrator->synaptic packege manager->settings->repositories->select all in ubuntu software and updates and then close it.It will update all the missed packeages.Then you can install apache2 and its MPM packages

---

