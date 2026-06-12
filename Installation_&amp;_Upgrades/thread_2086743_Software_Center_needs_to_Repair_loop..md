---
title: "Software Center needs to Repair loop."
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by NCXA on 2012-11-21
Dear Experts. 

When Running the Ubuntu Software center I get a message that it needs to repair which loops and fails. 
My system : 
```
gs2@gs2-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```
I tried to run the following : 
```
gs2@gs2-desktop:~$ sudo apt-get clean
gs2@gs2-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gs2@gs2-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 convirt : Depends: xen-utils
E: Unmet dependencies. Try using -f.
gs2@gs2-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cups-pk-helper appmenu-gtk libaudiofile-dev g++-4.4
  openoffice.org-l10n-en-gb libdirectfb-extra libdirectfb-1.2-9 appmenu-qt
  gir1.2-gconf-2.0 linux-headers-2.6.32-28 appmenu-gtk3 python2.6-dev
  libesd0-dev libfreetype6-dev openoffice.org-l10n-common libkadm5clnt-mit7
  libaudio-dev libkadm5srv-mit7 linux-headers-2.6.32-28-generic libkdb5-4
  libdirectfb-dev libjpeg62-dev gir1.2-panelapplet-4.0 libaa1-dev libsysfs-dev
  libstdc++6-4.4-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  convirt
The following packages will be upgraded:
  convirt
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 2,185 kB of archives.
After this operation, 7,840 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://il.archive.ubuntu.com/ubuntu/ precise/universe convirt all 2.0.1-6 [2,185 kB]
Fetched 2,185 kB in 7s (274 kB/s)                                              
dpkg: dependency problems prevent configuration of convirt:
 convirt depends on xen-utils; however:
  Package xen-utils is not installed.
dpkg: error processing convirt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 convirt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help is appreciated . 

Thanks,
NCXA

---

### Post by zvacet on 2012-11-22
```
sudo dpkg --configure -a
```

---

### Post by NCXA on 2012-11-22
Thanks for the reply,
this is what I'm getting : 
```
gs2@gs2-desktop:~$ sudo dpkg --configure -a
[sudo] password for gs2: 
dpkg: dependency problems prevent configuration of convirt:
 convirt depends on xen-utils; however:
  Package xen-utils is not installed.
dpkg: error processing convirt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 convirt
gs2@gs2-desktop:~$ 
```

---

### Post by zvacet on 2012-11-22
```
sudo apt-get install xen-utils convirt
```

---

### Post by NCXA on 2012-11-22
still no go :S
```
gs2@gs2-desktop:~$ sudo apt-get install xen-utils convirt
[sudo] password for gs2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xen-utils-4.1' instead of 'xen-utils'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 xen-utils-4.1 : Depends: libxen-4.1 (>= 4.1.2) but it is not going to be installed
                 Depends: xen-utils-common (>= 3.4.2-4) but it is not going to be installed
                 Recommends: xen-hypervisor-4.1
                 Recommends: qemu-keymaps but it is not going to be installed
                 Recommends: qemu-utils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by NCXA on 2012-11-22
Oh Got it now ! 
added the dependencies !

---

