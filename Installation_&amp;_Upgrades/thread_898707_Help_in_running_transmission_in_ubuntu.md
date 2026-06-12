---
title: "Help in running transmission in ubuntu"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2008-08-23
Can someone please help me in setting up transmission in ubuntu.
I am running 8.0.4 and whenever i type 'transmission', i get Seg fault


$ transmission
Segmentation fault
$ which transmission
/usr/bin/transmission

I have tried download 'transmission' and curl source and compile it locally, I still have the same error.

Thank you for any help.

---

### Post by kaivalagi on 2008-08-23
> **yinglcs2 said:**
> Can someone please help me in setting up transmission in ubuntu.
I am running 8.0.4 and whenever i type 'transmission', i get Seg fault


$ transmission
Segmentation fault
$ which transmission
/usr/bin/transmission

I have tried download 'transmission' and curl source and compile it locally, I still have the same error.

Thank you for any help.

I assume you've tried removing, clearing the cache, and re-adding it i.e.

```
sudo apt-get remove transmission && sudo apt-get autoclean && sudo apt-get install transmission
```

That's all I can suggest as that error isn't really that helpful :(

---

### Post by yinglcs2 on 2008-08-23
> **kaivalagi said:**
> I assume you've tried removing, clearing the cache, and re-adding it i.e.

```
sudo apt-get remove transmission && sudo apt-get autoclean && sudo apt-get install transmission
```

That's all I can suggest as that error isn't really that helpful :(

Thanks. I did what you suggested. Same error:

```

$ sudo apt-get remove transmission && sudo apt-get autoclean && sudo apt-get install transmission
[sudo] password for scheung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libdns32 linux-headers-2.6.24-16-generic
  transmission-cli linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  transmission
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.5kB disk space will be freed.
Do you want to continue [Y/n]? Y 
(Reading database ... 218872 files and directories currently installed.)
Removing transmission ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del gnome-do 0.5.99.0-0~hardy~ppa1 [129kB]
Del firefox-3.0 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [1064kB]
Del gnome-do 0.5.97.1-0~hardy~ppa1 [126kB]
Del qbittorrent 1.1.1-0ubuntu1 [1359kB]
Del firefox-dom-inspector 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [8974B]
Del xulrunner-1.9 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2 [7749kB]
Del firefox-3.0-dom-inspector 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [65.8kB]
Del firefox 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [65.9kB]
Del firefox-gnome-support 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [65.8kB]
Del firefox-3.0-gnome-support 3.0.1+build1+nobinonly-0ubuntu0.8.04.2 [25.7kB]
Del xulrunner-1.9-gnome-support 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2 [38.5kB]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libdns32 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  transmission
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/912B of archives.
After this operation, 20.5kB of additional disk space will be used.
Selecting previously deselected package transmission.
(Reading database ... 218872 files and directories currently installed.)
Unpacking transmission (from .../transmission_1.22-1ubuntu1~hardy1_all.deb) ...
Setting up transmission (1.22-1ubuntu1~hardy1) ...
scheung:tests $ transmission
Segmentation fault
scheung:tests $ 


```

---

### Post by kaivalagi on 2008-08-23
> **yinglcs2 said:**
> Thanks. I did what you suggested. Same error:


One thing that's strange:

```
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libdns32 linux-headers-2.6.24-16-generic
  transmission-cli linux-headers-2.6.24-16
```

I thought "transmission-cli" was supposed to be part of the transmission meta package...but the above would suggest that it is orphaned somehow, maybe other required parts are missing?

Try extending the previous command to:

```
sudo apt-get remove transmission transmission-cli transmission-gtk transmission-common && sudo apt-get autoclean && sudo apt-get install transmission transmission-cli transmission-gtk transmission-common
```

...worth a shot...

[COLOR="Blue"]edit: I left in the simulate options (-s)...whoops :oops:
Copy and paste the command above again now that it's fixed :)[/COLOR]

---

### Post by yinglcs2 on 2008-08-23
Thanks.

I tried again. Still does not work:

```

$ sudo apt-get -s remove transmission transmission-cli transmission-gtk transmission-common && sudo apt-get autoclean && sudo apt-get -s install transmission transmission-cli transmission-gtk transmission-common
[sudo] password for scheung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzzip-0-13 xserver-xorg-video-amd libdns32 libtorrent-rasterbar0
  openoffice.org-base-core libboost-filesystem1.34.1
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  transmission transmission-cli transmission-common transmission-gtk
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv transmission [1.22-1ubuntu1~hardy1]
Remv transmission-cli [1.22-1ubuntu1~hardy1]
Remv transmission-gtk [1.22-1ubuntu1~hardy1]
Remv transmission-common [1.22-1ubuntu1~hardy1]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
transmission is already the newest version.
transmission-cli is already the newest version.
transmission-cli set to manually installed.
transmission-gtk is already the newest version.
transmission-gtk set to manually installed.
transmission-common is already the newest version.
transmission-common set to manually installed.
The following packages were automatically installed and are no longer required:
  libzzip-0-13 xserver-xorg-video-amd libdns32 libtorrent-rasterbar0
  openoffice.org-base-core libboost-filesystem1.34.1
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scheung:tests $ transmission
Segmentation fault


```

---

### Post by kaivalagi on 2008-08-23
> **yinglcs2 said:**
> Thanks.

I tried again. Still does not work:

```

$ sudo apt-get -s remove transmission transmission-cli transmission-gtk transmission-common && sudo apt-get autoclean && sudo apt-get -s install transmission transmission-cli transmission-gtk transmission-common
[sudo] password for scheung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzzip-0-13 xserver-xorg-video-amd libdns32 libtorrent-rasterbar0
  openoffice.org-base-core libboost-filesystem1.34.1
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  transmission transmission-cli transmission-common transmission-gtk
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv transmission [1.22-1ubuntu1~hardy1]
Remv transmission-cli [1.22-1ubuntu1~hardy1]
Remv transmission-gtk [1.22-1ubuntu1~hardy1]
Remv transmission-common [1.22-1ubuntu1~hardy1]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
transmission is already the newest version.
transmission-cli is already the newest version.
transmission-cli set to manually installed.
transmission-gtk is already the newest version.
transmission-gtk set to manually installed.
transmission-common is already the newest version.
transmission-common set to manually installed.
The following packages were automatically installed and are no longer required:
  libzzip-0-13 xserver-xorg-video-amd libdns32 libtorrent-rasterbar0
  openoffice.org-base-core libboost-filesystem1.34.1
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scheung:tests $ transmission
Segmentation fault


```

Apologies, I left in the -s options, see above

---

