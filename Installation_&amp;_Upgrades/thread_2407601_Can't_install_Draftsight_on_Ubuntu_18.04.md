---
title: "Can't install Draftsight on Ubuntu 18.04"
date: 2018-12-06
forum: Installation &amp; Upgrades
---

### Post by bsnider on 2018-12-06
Hi I have been trying to install the latest version of Draftsight (Download for Ubuntu) on my new setup with Ubuntu 18.04.  I got the following error messages in Terminal when trying the following:  

bruce@bruce:~/Downloads$ sudo dpkg -i draftSight.deb
(Reading database ... 174397 files and directories currently installed.)
Preparing to unpack draftSight.deb ...
access control disabled, clients can connect from any host
/var/lib/dpkg/tmp.ci/ShowLicense: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
access control enabled, only authorized clients can connect
dpkg: error processing archive draftSight.deb (--install):
 new draftsight package pre-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 draftSight.deb

I would appreciate any suggestions you might provide about this !!!  Thanks !!!

---

### Post by Holger_Gehrke on 2018-12-06
I'd try```
sudo apt install ~/Downloads/draftSight.deb
``` apt will try to download and install dependencies of a package before the package itself, dpkg doesn't do that.
If that doesn't work, please post whatever messages it shows.

Holger

---

### Post by bsnider on 2018-12-06
Hello Holger, 

Thank you very much for your help  !!! Unfortunately, it did not work.  Here are the messages that came up:  

sudo apt install ~/Downloads/draftSight.deb
[sudo] password for bruce: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'draftsight' instead of '/home/bruce/Downloads/draftSight.deb'
The following NEW packages will be installed:
  draftsight
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 0 B/622 MB of archives.
After this operation, 1,711 MB of additional disk space will be used.
Get:1 /home/bruce/Downloads/draftSight.deb draftsight amd64 2018.3.0.4215 [622 MB]
(Reading database ... 174397 files and directories currently installed.)
Preparing to unpack .../bruce/Downloads/draftSight.deb ...
access control disabled, clients can connect from any host
/var/lib/dpkg/tmp.ci/ShowLicense: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
access control enabled, only authorized clients can connect
dpkg: error processing archive /home/bruce/Downloads/draftSight.deb (--unpack):
 new draftsight package pre-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 /home/bruce/Downloads/draftSight.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Well, I would be happy to hear any other suggestions !!  thanks again.

---

### Post by Holger_Gehrke on 2018-12-09
Check whether the library libgtk-x11-2.0.so.0 is actually available on your system ('locate libgtk-x11-2.0.so.0'). On my system it is (three times,actually; 32 bit version, 64 bit version and once as part of a snap ...) and was installed as part of the package 'libgtk2.0-0'. If it doesn't exist you could install that package using 'sudo apt install libgtk2.0-0'. If it does exist and the installation script of Draftsight doesn't recognize or find it, then I'm out of ideas for the moment ...

Holger

---

### Post by bsnider on 2018-12-12
Thank you Holger.   As you suggested, I ran 'locate libgtk-x11-2.0.so.0' and found that I had that located in several spots, many of them were for this GIMP program I have installed.  

I'm not sure why, but this time I ran "sudo apt install ~/Downloads/draftSight.deb" again and this time the installation worked!!  

Since earlier, I installed the program called Freecad, and this installed some different background software, maybe that helped.

---

