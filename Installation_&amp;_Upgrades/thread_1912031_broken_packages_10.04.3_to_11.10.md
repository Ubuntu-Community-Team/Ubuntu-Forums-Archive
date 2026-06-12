---
title: "broken packages 10.04.3 to 11.10"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by sbinkerd1 on 2012-01-19
I tried to upgrade to 11.10 and ran into some issues. 
I can boot to a point where it loads apache and then it stops. I can ssh into the box, and get to my web pages so it is partially booted.

when I try to apt-get update or apt-get -f install I get 14 packages that will not install or update because of dependencies.

here is the errors and list of packages.
I have been at this for 4 days. Any help is appreciated.

```
$ sudo apt-get -f install 
[sudo] password for scottbob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
14 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up udev (173-0ubuntu4.1) ...
udev start/running, process 15333
info: unrecognized option '--convert-db'
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.
dpkg: error processing bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:
 libsane depends on udev (>= 0.88-1); however:
  Package udev is not configured yet.
dpkg: error processing libsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing colord (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymNo apport report written because the error message indicates its a followup error from a previous failure.
                               No apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   outh depends on udev (>= 166-0ubuntu4); however:
  Package udev is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udisks:
 udisks depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdu0:
 libgdu0 depends on udisks (>= 1.0.0~); however:
  Package udisks is not configured yet.
 libgdu0 depends on udisks (<< 1.1.0); however:
  Package udisks is not configured yet.
dpkg: error processing libgdu0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lvm2:
 lvm2 depends on dmsetup (>> 2:1.02.47); however:
  Package dmsetup is not configured yet.
dpkg: error processing lvm2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.8.2-2ubuntu28); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-x11:
 plymouth-x11 depends on plymouth (= 0.8.2-2ubuntu28); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing xsane (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 udev
 bluez
 dmsetup
 libsane
 colord
 plymouth
 alsa-utils
 bluez-gstreamer
 udisks
 libgdu0
 lvm2
 plymouth-label
 plymouth-x11
 xsane
N: Ignoring 'old' in directory '/etc/apt/sources.list.d/' as it is not a regular file
N: Ignoring 'old' in directory '/etc/apt/sources.list.d/' as it is not a regular file
N: Ignoring 'old' in directory '/etc/apt/sources.list.d/' as it is not a regular file
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by raja.genupula on 2012-01-20
try these commands in terminal one by one 
```
sudo dpkg --configure -a
sudo apt-get install -f
```

All the best.

---

### Post by sbinkerd1 on 2012-01-20
yeah, been there. done that.
all the normal apt-get update, upgrade, dist-upgrade, install, remove and install, purge and install... nothing works.

It is like a catch 22. I can't install these ackages because they have dependencies, but it will not install the dependant packages for unknown reasons.

---

### Post by drmrgd on 2012-01-20
The problem is with udev.  Since the configure script is breaking, it's breaking the whole process downstream.  A quick search shows that there is a bug listed that matches your problem with a workaround toward the end of the thread.  You could try that to see if it helps:  

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/745011]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/745011")

---

### Post by sbinkerd1 on 2012-01-20
Yep. tried that fix also. still no go.
I did a sudo aptitude full-upgrade and that cleaned up 4 broken packages. still have 10 that are dead including the udev

---

### Post by raja.genupula on 2012-01-20
ok is it possible to get the required version from the synaptic , i mean what ever the version ,some dependencies are asking . If we  get them from synaptic we can fix some them .

try this .

---

### Post by sbinkerd1 on 2012-01-20
Ok. got it figured out.

I rm'd the '--convert-db' line in /var/lib/dpkg/info/udev.postinst according to info found on another thread. this allowed the broken packages to be fixed.

still couldn't boot into the desktop until I renamed the xorg.conf to xorg.conf.old. Then did startx. It got into a desktop. YAY! still was odd looking and didn't get a login. it just went to the desktop.

I rebooted and was able to get my login. I had to reinstall a few packages that were removed during my round and round with this upgrade from hell, but now everything is working... Now to figure out this new odd desktop environment.

thanks for the suggestions!

---

