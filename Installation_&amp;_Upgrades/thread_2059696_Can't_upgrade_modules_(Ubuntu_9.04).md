---
title: "Can't upgrade modules (Ubuntu 9.04)"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by cpiguy on 2012-09-18
Hi,

I just took over a Ubuntu 9.04 server and can't seem to install php5-curl.

When I run 

   ```
apt-get install php5-curl
```I get the following

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 libcurl3 php5-cli php5-common php5-mysql
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libcurl3 php5-curl
The following packages will be upgraded:
  libapache2-mod-php5 php5-cli php5-common php5-mysql
4 upgraded, 2 newly installed, 0 to remove and 45 not upgraded.
Need to get 5654kB of archives.
After this operation, 565kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  php5-cli php5-mysql libapache2-mod-php5 php5-common libcurl3 php5-curl
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com jaunty-updates/main php5-cli 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com jaunty-security/main php5-cli 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com jaunty-security/main php5-mysql 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com jaunty-security/main libapache2-mod-php5 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com jaunty-security/main php5-common 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com jaunty-security/main libcurl3 7.18.2-8ubuntu4.1
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com jaunty-security/main php5-curl 5.2.6.dfsg.1-3ubuntu4.6
  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.6.dfsg.1-3ubuntu4.6_i386.deb  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.2.6.dfsg.1-3ubuntu4.6_i386.deb  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.6.dfsg.1-3ubuntu4.6_i386.deb  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu4.6_i386.deb  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-8ubuntu4.1_i386.deb  404 Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6.dfsg.1-3ubuntu4.6_i386.deb  404 Not Found [IP: 91.189.92.184 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
When I run the 

```

apt-get update

apt-get dist-upgrade

```I get a bunch of error messages like above.

I read somewhere that I should point the source-list to a more current version.

Not sure where source-list is OR what I should update it to so I can get php5-curl installed.

Appreciate any information you can give me.

---

### Post by ajgreeny on 2012-09-18
9.04 even as the server edition is way out of date and no longer supported.

There are EOL repositories, but it would be a great deal more sensible and easier to start again and download a newer version of ubuntu to install.

See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for info about the use of EOL repos.

---

