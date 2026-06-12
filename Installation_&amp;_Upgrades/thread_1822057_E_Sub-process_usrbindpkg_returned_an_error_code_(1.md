---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by Dr. Awesome on 2011-08-10
So I'm trying to download 'rar' right? Every time I do this it comes up with this error code.


chris@Chris-E-4000:~$ sudo apt-get install rar
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdelibs5-plugins : Depends: kdelibs5-data (= 4:4.6.2-0ubuntu4) but it is not going to be installed
 kdoctools : Depends: kdelibs5-data (= 4:4.6.2-0ubuntu4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have tried 'apt-get -f install', so don't think that's going to work :/ I've also tried 'sudo dpkg --configure --pending' which still does nothing.

Also, after the latest of my attempts, I noticed the ' kdelibs5-plugins : Depends: kdelibs5-data etc...' so I tried 'sudo apt-get -f install kdelibs5-data' and STILL came up with the error.

chris@Chris-E-4000:~$ sudo apt-get -f install kdelibs5-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  kdelibs5-data
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
9 not fully installed or removed.
Need to get 0 B/2,194 kB of archives.
After this operation, 10.6 MB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 178222 files and directories currently installed.)
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.6.2-0ubuntu4_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.6.2-0ubuntu4_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_4%3a4.6.2-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

If anyone can help explain how to fix this, or even what's wrong (I'm more or less a "noob" at Ubuntu) I would GREATLY appreciate it.

---

### Post by beew on 2011-08-10
Seems like there may be a problem with kdelibs5-data in the repo. Try this and see if it works. Open Synaptic, go to Settings > repositories > updates and check the box Natty proposed (it has a more updated version of the package kdelibs5-data) and then reload and install rar.

But just out of curiosity, what do you need rar for? It is a shareware that you have to register within 40 days. You can use p7zip for archiving with high compression ratio.

---

### Post by Dr. Awesome on 2011-08-10
Thanks for the suggestion, unfortunately I still get the error for p7zip. When I went to Settings, the option for repositories wasn't allowed...

---

### Post by Dr. Awesome on 2011-08-13
Problem fixed. Just took a couple turn-offs/turn-ons.

---

