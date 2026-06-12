---
title: "Cant Install Updates"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by vwlockboy on 2012-06-11
I'm new to Ubuntu and am running 12.04 64 bit.  I was doing ok until I tried my latest updates.

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:

libbamf3-0: Depends: libc6 (>= 2.2.5) but 2.15-0ubuntu10 is installed
            Depends: libdbus-glib-1-2 (>= 0.88) but 0.98-1ubuntu1 is installed
            Depends: libglib2.0-0 (>= 2.28.0) but 2.32.1-0ubuntu2 is installed
            Depends: bamfdaemon (= 0.2.118-0ubuntu0.1) but 0.2.114-0ubuntu1 is installed

After I try apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bamfdaemon libbamf0
The following packages will be upgraded:
  bamfdaemon libbamf0
2 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
1 not fully installed or removed.
Need to get 0 B/130 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing description
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing maintainer
dpkg: error: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

Sorry I'm a newbie and lost, any help is appreciated.

---

### Post by vwlockboy on 2012-06-11
james@james-System-Product-Name:/var/lib/dpkg/info$ sudo apt-get remove bamfdaemon libbamf0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ginn : Depends: libbamf0 (>= 0.2.20) but it is not going to be installed
 libbamf3-0 : Depends: bamfdaemon (= 0.2.118-0ubuntu0.1)
 libqtbamf1 : Depends: bamfdaemon
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

my latest effort and then

james@james-System-Product-Name:/var/lib/dpkg/info$ sudo apt-get -f install bamfdaemon libbamf0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bamfdaemon libbamf0
2 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
1 not fully installed or removed.
Need to get 0 B/130 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing description
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing maintainer
dpkg: error: parsing file '/var/lib/dpkg/available' near line 11276 package 'watch':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by cybercity@localhost on 2012-06-18
> sudo apt-get -f install bamfdaemon libbamf0hi, remove package name after -f just launch apt-get install -f or apt-get install --fix-missing

and then try 
sudo dpkg -configure -a

---

