---
title: "cURL Module not install. Ubuntu 18.10 PHP 7.2.10"
date: 2018-12-10
forum: Installation &amp; Upgrades
---

### Post by mustafa-taheri on 2018-12-10
[COLOR=#242729][FONT=Arial]I am struggling with an issue of how can I install cURL module in Ubuntu 18.10. While upgrading from 17.10 to 18.10 cURL was removed/deleted. Now when I try to execute the command[/FONT][/COLOR]
sudo apt-get install php7.2-curl
[COLOR=#242729][FONT=Arial]gives the ERROR[/FONT][/COLOR]
```
The following packages have unmet dependencies:php7.2-curl : Depends: libcurl4 (>= 7.44.0) but it is not going to be installed E: Unable to correct problems, you have held broken packages.
```
[COLOR=#242729][FONT=Arial]OR[/FONT][/COLOR]
sudo apt-get install curl
[COLOR=#242729][FONT=Arial]gives the ERROR[/FONT][/COLOR]
```
The following packages have unmet dependencies: curl : Depends: libcurl4 (= 7.61.0-1ubuntu2.2) but it is not going to be installed E: Unable to correct problems, you have held broken packages.Output of apt-cache policy php7.2-curl curl libcur14
```

```
php7.2-curl:
  Installed: (none)
  Candidate: 7.2.13-1+ubuntu18.10.1+deb.sury.org+1
  Version table:
     7.2.13-1+ubuntu18.10.1+deb.sury.org+1 500
        500 http://ppa.launchpad.net/ondrej/php/ubuntu cosmic/main amd64 Packages
     7.2.10-0ubuntu1 500
        500 http://in.archive.ubuntu.com/ubuntu cosmic/main amd64 Packages
     7.2.7-1+ubuntu17.10.1+deb.sury.org+1 -1
        100 /var/lib/dpkg/status
curl:
  Installed: (none)
  Candidate: 7.61.0-1ubuntu2.2
  Version table:
     7.61.0-1ubuntu2.2 500
        500 http://in.archive.ubuntu.com/ubuntu cosmic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu cosmic-security/main amd64 Packages
     7.61.0-1ubuntu2 500
        500 http://in.archive.ubuntu.com/ubuntu cosmic/main amd64 Packages
N: Unable to locate package libcur14

```

Output of /etc/apt/sources.list.d/

```
creators@creators:/etc/apt/sources.list.d$ ls
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
mongodb-org-4.0.list
mongodb-org-4.0.list.distUpgrade
mongodb-org-4.0.list.save
noobslab-ubuntu-apps-artful.list
noobslab-ubuntu-apps-artful.list.save
ondrej-ubuntu-apache2-artful.list
ondrej-ubuntu-apache2-artful.list.distUpgrade
ondrej-ubuntu-apache2-artful.list.save
ondrej-ubuntu-mysql-5_6-artful.list
ondrej-ubuntu-mysql-5_6-artful.list.distUpgrade
ondrej-ubuntu-mysql-5_6-artful.list.save
ondrej-ubuntu-php-artful.list
ondrej-ubuntu-php-artful.list.distUpgrade
ondrej-ubuntu-php-artful.list.save
ondrej-ubuntu-php-cosmic.list
ondrej-ubuntu-php-cosmic.list.save
skype-stable.list
skype-stable.list.distUpgrade
skype-stable.list.save
teamviewer.list
teamviewer.list.distUpgrade
teamviewer.list.save
webupd8team-ubuntu-java-artful.list
webupd8team-ubuntu-java-artful.list.distUpgrade
webupd8team-ubuntu-java-artful.list.save

```

Please help

---

