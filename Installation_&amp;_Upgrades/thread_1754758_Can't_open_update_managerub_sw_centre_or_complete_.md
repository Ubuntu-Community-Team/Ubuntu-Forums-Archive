---
title: "Can't open update manager/ub sw centre or complete synaptic/apt-get package installs"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by thewinchester on 2011-05-10
Ok, this is doing my head in. I can't run update manager, use ubuntu  software centre or successfully complete actions using synaptic package  manager or apt-get at command line.

I've done some searching through the forums, and [trying the various solutions in this thread]("http://ubuntuforums.org/showthread.php?t=1577315") delivered no results

Here's what I'm getting from terminal, any assistance to diagnose and correct appreciated:

```
root@grill:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ubuntuone-client : Depends: python-ubuntuone-client (= 1.6.2-0ubuntu1) but 1.6.1-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
root@grill:~# apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gwibber gwibber-service language-selector-common language-selector-gnome
  python-ubuntuone-client python-ubuntuone-storageprotocol usb-creator-common
  usb-creator-gtk
Suggested packages:
  gwibber-themes gwibber-service-flickr gwibber-service-digg
  gwibber-service-buzz gwibber-service-statusnet gwibber-service-foursquare
  gwibber-service-friendfeed gwibber-service-pingfm gwibber-service-qaiku
The following packages will be REMOVED:
  libavdevice52 libavfilter1
The following packages will be upgraded:
  gwibber gwibber-service language-selector-common language-selector-gnome
  python-ubuntuone-client python-ubuntuone-storageprotocol usb-creator-common
  usb-creator-gtk
8 upgraded, 0 newly installed, 2 to remove and 26 not upgraded.
27 not fully installed or removed.
Need to get 0 B/952 kB of archives.
After this operation, 283 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155731 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.33 (using .../language-selector-gnome_0.34_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/language-selector-gnome_0.34_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace language-selector-common 0.33 (using .../language-selector-common_0.34_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/language-selector-common_0.34_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace gwibber 3.0.0.1-0ubuntu2 (using .../gwibber_3.0.0.1-0ubuntu3_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/gwibber_3.0.0.1-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace gwibber-service 3.0.0.1-0ubuntu2 (using .../gwibber-service_3.0.0.1-0ubuntu3_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/gwibber-service_3.0.0.1-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace gwibber-service-facebook 3.0.0.1-0ubuntu2 (using .../gwibber-service-facebook_3.0.0.1-0ubuntu2_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/gwibber-service-facebook_3.0.0.1-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace gwibber-service-identica 3.0.0.1-0ubuntu2 (using .../gwibber-service-identica_3.0.0.1-0ubuntu2_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/gwibber-service-identica_3.0.0.1-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace gwibber-service-twitter 3.0.0.1-0ubuntu2 (using .../gwibber-service-twitter_3.0.0.1-0ubuntu2_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/gwibber-service-twitter_3.0.0.1-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing  to replace python-ubuntuone-storageprotocol 1.6.0-0ubuntu1 (using  .../python-ubuntuone-storageprotocol_1.6.1-0ubuntu1_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/python-ubuntuone-storageprotocol_1.6.1-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace python-ubuntuone-client 1.6.1-0ubuntu3 (using .../python-ubuntuone-client_1.6.2-0ubuntu1_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/python-ubuntuone-client_1.6.2-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace usb-creator-gtk 0.2.28 (using .../usb-creator-gtk_0.2.28.3_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/usb-creator-gtk_0.2.28.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace usb-creator-common 0.2.28 (using .../usb-creator-common_0.2.28.3_all.deb) ...
Segmentation fault
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/usb-creator-common_0.2.28.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/language-selector-gnome_0.34_all.deb
 /var/cache/apt/archives/language-selector-common_0.34_all.deb
 /var/cache/apt/archives/gwibber_3.0.0.1-0ubuntu3_all.deb
 /var/cache/apt/archives/gwibber-service_3.0.0.1-0ubuntu3_all.deb
 /var/cache/apt/archives/gwibber-service-facebook_3.0.0.1-0ubuntu2_all.deb
 /var/cache/apt/archives/gwibber-service-identica_3.0.0.1-0ubuntu2_all.deb
 /var/cache/apt/archives/gwibber-service-twitter_3.0.0.1-0ubuntu2_all.deb
 /var/cache/apt/archives/python-ubuntuone-storageprotocol_1.6.1-0ubuntu1_all.deb
 /var/cache/apt/archives/python-ubuntuone-client_1.6.2-0ubuntu1_all.deb
 /var/cache/apt/archives/usb-creator-gtk_0.2.28.3_all.deb
 /var/cache/apt/archives/usb-creator-common_0.2.28.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@grill:~# 

```

---

### Post by zvacet on 2011-05-11
Suggested command is

```
sudo apt-get -f install
```

or

```
apt-get -f install
```

if you are already root.

---

