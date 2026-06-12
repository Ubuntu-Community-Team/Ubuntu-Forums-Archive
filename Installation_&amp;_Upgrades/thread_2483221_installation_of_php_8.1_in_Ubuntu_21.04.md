---
title: "installation of php 8.1 in Ubuntu 21.04"
date: 2023-01-23
forum: Installation &amp; Upgrades
---

### Post by ginost7 on 2023-01-23
installation failed, an important package that cannot be installed is disturbing. Here are the commands: 

$ sudo apt install software-properties-common


# adding & installing php8 in ubuntu 21

#sudo add-apt-repository ppa:ondrej/php

$ sudo add-apt-repository ppa:ondrej/php # Press enter when prompted.

$ sudo apt update

sudo apt-get install php8.1

$ sudo apt install php8.1-common php8.1-cli -y


ERRORS are:  sudo apt install php8.1
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package php8.1
E: Couldn't find any package by glob 'php8.1'

---

### Post by Impavidus on 2023-01-23
Ubuntu 21.04 reached end of life one year ago.

---

### Post by ginost7 on 2023-01-24
gin0@gin0-Inspiron-5567:~$ sudo apt install software-properties-common
[sudo] password for gin0: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
software-properties-common is already the newest version (0.99.10.2).
The following package was automatically installed and is no longer required:
  libllvm11
Use 'sudo apt autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
gin0@gin0-Inspiron-5567:~$ sudo add-apt-repository ppa:ondrej/php
PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb [http://ppa.launchpad.net/ondrej/php/ubuntu/](http://ppa.launchpad.net/ondrej/php/ubuntu/) hirsute main'
Description:
Co-installable PHP versions: PHP 5.6, PHP 7.x and most requested extensions are included. Only Supported Versions of PHP ([http://php.net/supported-versions.php](http://php.net/supported-versions.php)) for Supported Ubuntu Releases ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)) are provided. Don't ask for end-of-life PHP versions or Ubuntu release, they won't be provided.

Debian oldstable and stable packages are provided as well: [https://deb.sury.org/#debian-dpa](https://deb.sury.org/#debian-dpa)

You can get more information about the packages at [https://deb.sury.org](https://deb.sury.org)

IMPORTANT: The <foo>-backports is now required on older Ubuntu releases.

BUGS&FEATURES: This PPA now has a issue tracker:
[https://deb.sury.org/#bug-reporting](https://deb.sury.org/#bug-reporting)

CAVEATS:
1. If you are using php-gearman, you need to add ppa:ondrej/pkg-gearman
2. If you are using apache2, you are advised to add ppa:ondrej/apache2
3. If you are using nginx, you are advised to add ppa:ondrej/nginx-mainline
   or ppa:ondrej/nginx

PLEASE READ: If you like my work and want to give me a little motivation, please consider donating regularly: [https://donate.sury.org/](https://donate.sury.org/)

WARNING: add-apt-repository is broken with non-UTF-8 locales, see
[https://github.com/oerdnj/deb.sury.org/issues/56](https://github.com/oerdnj/deb.sury.org/issues/56) for workaround:

# LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php
More info: [https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/ondrej-ubuntu-php-hirsute.list
Adding deb entry to /etc/apt/sources.list.d/ondrej-ubuntu-php-hirsute.list
Found existing deb-src entry in /etc/apt/sources.list.d/ondrej-ubuntu-php-hirsute.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/ondrej-ubuntu-php-hirsute.list
Adding key to /etc/apt/trusted.gpg.d/ondrej-ubuntu-php.gpg with fingerprint 14AA40EC0831756756D7F66C4F4EA0AAE5267A6C
Hit:1 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) focal InRelease
Hit:2 [http://ppa.launchpad.net/linuxuprising/java/ubuntu](http://ppa.launchpad.net/linuxuprising/java/ubuntu) hirsute InRelease
Hit:3 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) hirsute InRelease
Hit:4 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) hirsute InRelease
Hit:5 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease
Hit:6 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) hirsute InRelease  
Hit:7 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease  
Hit:8 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) hirsute-updates InRelease
Hit:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) hirsute-backports InRelease
Hit:10 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) hirsute-security InRelease
Hit:11 [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) hirsute InRelease
Reading package lists... Done

---

