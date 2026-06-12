---
title: "Upgarde to 12.04 - Broken keyring"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Nargren on 2012-05-12
Hey everyone!

I've upgraded  2 weeks ago to 12.04 and during the upgrade (not clean install, I said "It should work to just update") I have received a keyring error or something (that I wisely ignored and said "I'll deal with it later).

Now the following things are broken:
-Software center doesn't load/work
-Update manager returns an error
```
E: ubuntu-keyring: subprocess installed post-installation script returned error exit status 127
E: apt: dependency problems - leaving unconfigured
```It downloads the packages, but doesn't install.

I was trying 

```
sudo apt-get -f install
```and then
```
sudo apt-get update
```But this happens after running the install command:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-debtagshw software-center-aptdaemon-plugins gir1.2-gudev-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
18 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-keyring (2011.11.21) ...
Warning: gnupg does not seem to be installed.
Warning: apt-key requires gnupg for most operations.

/usr/bin/apt-key: 132: /usr/bin/apt-key: gpg: not found
/usr/bin/apt-key: 132: /usr/bin/apt-key: gpg: not found
dpkg: error processing ubuntu-keyring (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of apt:
 apt depends on ubuntu-keyring; however:
  Package ubuntu-keyring is not configured yet.
dpkg: error processing apt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on apt; however:
  Package apt is not configured yet.
 ubuntu-minimal depends on ubuntu-keyring; however:
  Package ubuntu-keyring is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on apt; however:
  Package apt is not configured yet.
dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.
dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
 software-properties-gtk depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of landscape-client-ui-install:
 landscape-client-ui-install depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing landscape-client-ui-install (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on apturl; however:
  Package apturl is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.43+bzr805-0ubuntu1); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.43+bzr805-0ubuntu1); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-aptdaemon.pkcompat:
 python-aptdaemon.pkcompat depends on python-aptdaemon (= 0.43+bzr805-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-installer:
 ubuntuone-installer depends on python-aptdaemon; however:
  Package python-aptdaemon is not configured yet.
 ubuntuone-installer depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing ubuntuone-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-common:
 ubuntuone-control-panel-common depends on ubuntuone-installer (>= 2.99.91); however:
  Package ubuntuone-installer is not configured yet.
dpkg: error processing ubuntuone-control-panel-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-qt:
 ubuntuone-control-panel-qt depends on ubuntuone-control-panel-common (= 3.0.0-0ubuntu1); however:
  Package ubuntuone-control-panel-common is not configured yet.
dpkg: error processing ubuntuone-control-panel-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-control-panel-gtk:No apport report written because MaxReports has already been reached

 ubuntuone-control-panel-gtk depends on ubuntuone-control-panel-qt (= 3.0.0-0ubuntu1); however:
  Package ubuntuone-control-panel-qt is not configured yet.
dpkg: error processing ubuntuone-control-panel-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 ubuntu-keyring
 apt
 ubuntu-minimal
 unattended-upgrades
 python-software-properties
 python-aptdaemon
 python-aptdaemon.gtk3widgets
 software-properties-gtk
 apturl
 landscape-client-ui-install
 nautilus-share
 python-aptdaemon.gtkwidgets
 python-aptdaemon-gtk
 python-aptdaemon.pkcompat
 ubuntuone-installer
 ubuntuone-control-panel-common
 ubuntuone-control-panel-qt
 ubuntuone-control-panel-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Nothing is fixed, update manager cannot install any updates or anything.
Any ideas on what could be done? perhaps something quicker than reinstalling?

Thanks, 
Nargren

---

### Post by cmont899 on 2012-05-12
Try running the following:

```

sudo apt-get clean all
sudo apt-get update 
```

---

### Post by Nargren on 2012-05-12
Sorry, error still there
```
E: ubuntu-keyring: subprocess installed post-installation script returned error exit status 127
E: apt: dependency problems - leaving unconfigured
```
Packages downloaded again, but installations is interrupted.

---

### Post by cmont899 on 2012-05-12
try:

```
sudo dpkg-reconfigure ubuntu-keyring
```

---

### Post by Nargren on 2012-05-12
I think I tried this before,
 ```
/usr/sbin/dpkg-reconfigure: ubuntu-keyring is broken or not fully installed.
```
I think I also tried force re-installing it, but no success there either

---

### Post by cmont899 on 2012-05-12
i got another:

```
sudo apt-get install --fix-broken
```

---

### Post by Nargren on 2012-05-12
Ye this one was the one I tried to fix the broken thing:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-debtagshw software-center-aptdaemon-plugins gir1.2-gudev-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
18 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```
I did use autoremove, but problem still existed afterwards as well.

---

### Post by cmont899 on 2012-05-12
another apt or dpkg process is already running. You should be able to find the processes with:

```
ps aux | grep 'apt\|dpkg'
```

the processes can them be killed, or a reboot should shoot them

```
kill <process id>
```

---

### Post by Nargren on 2012-05-12
This problem exists for 2 weeks or so by now. I've done quite a few reboots and tried to kill the applications, but it was no help.
Could I delete and reinstall the ubuntu keyring? The issue seems to be with that

---

### Post by cmont899 on 2012-05-12
Let's try again:

```
sudo aptitude reinstall ubuntu-keyring
```

---

### Post by drknot on 2012-05-12
Shoot me if you need to.  THe error log says gpg missing, everything else appears to my untutored eye to depend on key ring  ?install gpg and see if it fixes your issue (might need a sudo dpkg --configure -a after - apt should let you know)  Ducks, runs and hides

---

### Post by Nargren on 2012-05-13
Hey,

unfortunately aptitude isn't installed and cant install it either, because of the error message returned (basically I cannot install anything) I tried to reinstall the keyring with
```
sudo apt-get install --reintall ubuntu-keyring
```but the same errors were returned as before. I was wondering if I can totally remove the keyring with apt-get remove and the simply install it? I was trying to do this, but there was an extra safety message asking me to type like "i am sure to delete this" or whatever.

---

### Post by Nargren on 2012-05-13
So at the moment after trying to "solve" the problem with synaptic package manager

[LIST]
[*]aptitude doesn't work
[*]apt-get doesn't work
[*]synaptic package manager loads, but cannot install anything (because of the error messages, see first post)
[*]update manager doesn't work
[*]recovery mode fix broken pacages doesn't work
[/LIST]
To sum it up, I cannot install any packagaes, any way at all...

Any ideas besides backing up my home folder and going through the hassle of reformatting the partition and making a clean install?

Edit:
Synaptic package manager shows this warning when started:

```
W: Unable to read /etc/apt/preferences.d/ - DirectoryExists (2: No such file or directory)
```And this error when trying to install anything:
```
E: The method driver /usr/lib/apt/methods/http could not be found.
E: Unable to lock the download directory.
```
Thanks

---

### Post by Nargren on 2012-05-13
Reinstalled my whole system.

---

### Post by Jelks on 2013-01-29
Im getting this message, please help bc its annoying. I reistalled twice and i keep getting this screen shot about my keyring. [IMG]http://i1337.photobucket.com/albums/o677/Marcellus_j/help_zps14c53800.png[/IMG]:(

---

