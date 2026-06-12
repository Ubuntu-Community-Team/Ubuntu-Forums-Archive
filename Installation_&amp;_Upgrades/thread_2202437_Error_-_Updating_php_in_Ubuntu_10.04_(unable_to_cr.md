---
title: "Error - Updating php in Ubuntu 10.04 (unable to create `/sbin/start-stop-daemon.dpkg-"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by sunil6 on 2014-01-29
Hello Guys,

I have ubuntu 10.04 long ago LAMP has been installed which been hosted for php projects,
Today i am  updating php, i encountered with error which i searched in goole which i didn't found finally i'm posting for any resolution to this error.
I've been following these steps to upgrade my php from ssh Console
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php5-oldstable
sudo apt-get update
sudo apt-get install php5
The problem is in the step of (sudo apt-get install php5)
the output i will paste it for your reference
:
:
root@myserver:/var/www# sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libt1-5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg libapache2-mod-php5 libedit2 libltdl7 libonig2 libqdbm14 php5-cli php5-common php5-curl php5-gd php5-mcrypt php5-mysql psmisc
Suggested packages:
  php-pear
Recommended packages:
  php5-readline
The following NEW packages will be installed:
  libltdl7 libonig2 libqdbm14
The following packages will be upgraded:
  dpkg libapache2-mod-php5 libedit2 php5 php5-cli php5-common php5-curl php5-gd php5-mcrypt php5-mysql psmisc
11 upgraded, 3 newly installed, 0 to remove and 134 not upgraded.
Need to get 0B/8656kB of archives.
After this operation, 1778kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 25386 files and directories currently installed.)
Preparing to replace dpkg 1.15.5.6ubuntu4 (using .../dpkg_1.15.8.4ubuntu3.1~lucid+1_amd64.deb) ...
Unpacking replacement dpkg ...
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.8.4ubuntu3.1~lucid+1_amd64.deb (--unpack):
 unable to create `/sbin/start-stop-daemon.dpkg-new' (while processing `./sbin/start-stop-daemon'): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.15.8.4ubuntu3.1~lucid+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please resolve this error, if you have any other steps to upgrade php, please let me know

---

### Post by fantab on 2014-01-29
Ubuntu 10.04 has reached its [end-of-life]("https://wiki.ubuntu.com/Releases"). No more working repositories and no more updates/upgrades. 
You will need to install the latest supported version of Ubuntu. If you want to upgrade to 12.04 read this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by sunil6 on 2014-01-29
Atlease tell me how to solve the problem..

dpkg: error processing /var/cache/apt/archives/dpkg_1.15.8.4ubuntu3.1~lucid+1_amd64.deb (--unpack):
 unable to create `/sbin/start-stop-daemon.dpkg-new' (while processing `./sbin/start-stop-daemon'): Permission denied

---

### Post by SeijiSensei on 2014-01-29
> root@myserver:/var/www# sudo apt-get install php5

If you're already running with root privileges, don't use sudo.  Just run "apt-get install ...".

---

### Post by sunil6 on 2014-01-29
> **SeijiSensei said:**
> If you're already running with root privileges, don't use sudo.  Just run "apt-get install ...".

Have you seen the error i'm already in root, 
unable to create `/sbin/start-stop-daemon.dpkg-new' (while processing `./sbin/start-stop-daemon'): Permission denied

It's not giving sudo before command, Its unable to stop and start the new one..........

---

### Post by SeijiSensei on 2014-01-30
The point is that the root user does not have sudo privileges.  Only members of group sudo do.  By default that group includes only the user created at installation. So I don't know what happens exactly when you run sudo as the root user, but it's possible that you lose privileges as a result.

Did you trying running apt-get without sudo?  What happened?

---

