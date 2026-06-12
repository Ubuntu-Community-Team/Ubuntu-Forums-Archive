---
title: "Error when installing Updates on Hardy"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by hempar on 2008-06-18
Today i got 16 updates for Ubuntu Hardy and i try to Install Updates i got error message which i attach with my post. It won't insatll any updates or i cannot open Synaptic Package Manager either.

---

### Post by Pumalite on 2008-06-18
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
( one at the time)
Post outputs.

---

### Post by hempar on 2008-06-18
Thank you for your quick responce Pumalite. My all Updates has been installed using your information.

---

### Post by Pumalite on 2008-06-18
You are welcome. Good luck.

---

### Post by Spondicious on 2008-06-18
Have the sameproblem - I just tried the suggested sudo commands in the above post and this is what I got - Same error message at the end


spondicious@Spondicious:~$ sudo dpkg --configure -a
[sudo] password for spondicious: 
spondicious@Spondicious:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
spondicious@Spondicious:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://wicd.longren.org](http://wicd.longren.org) feisty Release.gpg 
Ign [http://wicd.longren.org](http://wicd.longren.org) feisty/extras Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Get:1 [http://wicd.longren.org](http://wicd.longren.org) feisty Release [29.1kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://wicd.longren.org](http://wicd.longren.org) feisty/extras Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Fetched 1B in 2s (0B/s)  
Reading package lists... Done
spondicious@Spondicious:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic
  linux-ubuntu-modules-2.6.24-19-generic
The following packages will be upgraded:
  app-install-data evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins file firefox firefox-3.0
  firefox-3.0-gnome-support firefox-gnome-support gnome-app-install
  gnome-applets gnome-applets-data hal-info klibc-utils libcamel1.2-11
  libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libgdata-google1.2-1
  libgdata1.2-1 libklibc libmagic1 libpolkit-gnome0 libsmbclient
  libtracker-gtk0 libtrackerclient0 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev linux-restricted-modules-common
  linux-restricted-modules-generic notification-daemon
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-style-human openoffice.org-writer
  openssl-blacklist policykit-gnome python-uno samba-common smbclient tracker
  tracker-search-tool ttf-opensymbol xulrunner-1.9 xulrunner-1.9-dom-inspector
  xulrunner-1.9-gnome-support
67 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
spondicious@Spondicious:~$

---

### Post by avtolle on 2008-06-18
Your problem is most likely that Synaptic or Update Manager is open. Close all instances of package managers out, wait until the gray cogwheel no longer appears in the panel, and give it another go.

---

### Post by Spondicious on 2008-06-18
I tried it again and I think perhaps the problem was that I had not been connected long enough to the internet for the packages to have been downloaded to be ready to do the upgrade.

I kept trying and eventually the upgrade did its stuff..




:) By the way I just love Ubuntu and I will be doing a podcast about my experiences with using Ubuntu and using programs available. It will be at typicalubuntu.com. I have just put up a couple of blog posts so far. Could be interesting for other newbies.

---

