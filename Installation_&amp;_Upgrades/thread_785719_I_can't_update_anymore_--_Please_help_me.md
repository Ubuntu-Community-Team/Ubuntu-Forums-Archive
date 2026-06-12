---
title: "I can't update anymore -- Please help me"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Prisma on 2008-05-07
Can someone please help me. 

I have Ubuntu 7.10 and I haven't install anything in particular. Two weeks ago I received some updates in my update manager. i proceed to apply the update.
But from that day all that the update manager does is to download the updates but it does not install them. Then it reload itself and all the updates are still in the list. 

Please guys help me out I am puzzled about this. :confused:

---

### Post by tamoneya on 2008-05-07
try updating through terminal.  If any of the following commands fails post the output here```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Prisma on 2008-05-07
It does not work. I don't understand why. 


```
Get:1 http://mirror.switch.ch gutsy Release.gpg [191B]
Get:2 http://ch.archive.ubuntu.com feisty-backports Release.gpg [191B]       
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                 
Ign http://archive.canonical.com gutsy/partner Translation-en_US            
Get:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US
Hit http://archive.canonical.com gutsy Release 
Get:5 http://archive.canonical.com feisty-commercial Release [5999B]           
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.canonical.com feisty-commercial/main Packages     
Ign http://ch.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://mirror.switch.ch gutsy/main Translation-en_US
Ign http://ch.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://mirror.switch.ch gutsy/restricted Translation-en_US
Ign http://ch.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://ch.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Ign http://mirror.switch.ch gutsy/universe Translation-en_US
Hit http://ch.archive.ubuntu.com feisty-backports Release
Ign http://mirror.switch.ch gutsy/multiverse Translation-en_US
Get:6 http://mirror.switch.ch gutsy-updates Release.gpg [191B]
Hit http://ch.archive.ubuntu.com feisty-backports/main Packages
Ign http://mirror.switch.ch gutsy-updates/main Translation-en_US
Hit http://ch.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://ch.archive.ubuntu.com feisty-backports/universe Packages
Hit http://ch.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://ch.archive.ubuntu.com feisty-backports/main Sources
Hit http://ch.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://ch.archive.ubuntu.com feisty-backports/universe Sources
Hit http://ch.archive.ubuntu.com feisty-backports/multiverse Sources
Ign http://mirror.switch.ch gutsy-updates/restricted Translation-en_US
Ign http://mirror.switch.ch gutsy-updates/universe Translation-en_US
Ign http://mirror.switch.ch gutsy-updates/multiverse Translation-en_US
Get:7 http://mirror.switch.ch gutsy-security Release.gpg [191B]
Ign http://mirror.switch.ch gutsy-security/main Translation-en_US
Ign http://mirror.switch.ch gutsy-security/restricted Translation-en_US
Ign http://mirror.switch.ch gutsy-security/universe Translation-en_US
Ign http://mirror.switch.ch gutsy-security/multiverse Translation-en_US        
Get:8 http://mirror.switch.ch gutsy-backports Release.gpg [191B]               
Ign http://mirror.switch.ch gutsy-backports/main Translation-en_US             
Ign http://mirror.switch.ch gutsy-backports/restricted Translation-en_US       
Ign http://mirror.switch.ch gutsy-backports/universe Translation-en_US         
Ign http://mirror.switch.ch gutsy-backports/multiverse Translation-en_US       
Hit http://mirror.switch.ch gutsy Release                                      
Hit http://mirror.switch.ch gutsy-updates Release                              
Hit http://mirror.switch.ch gutsy-security Release                             
Hit http://mirror.switch.ch gutsy-backports Release                            
Hit http://mirror.switch.ch gutsy/main Packages                                
Hit http://mirror.switch.ch gutsy/restricted Packages                          
Hit http://mirror.switch.ch gutsy/main Sources                                 
Hit http://mirror.switch.ch gutsy/restricted Sources                           
Hit http://mirror.switch.ch gutsy/universe Packages                            
Hit http://mirror.switch.ch gutsy/universe Sources                             
Hit http://mirror.switch.ch gutsy/multiverse Packages                          
Hit http://mirror.switch.ch gutsy/multiverse Sources                           
Get:9 http://mirror.switch.ch gutsy-updates Release [58.5kB]                   
Get:10 http://mirror.switch.ch gutsy-security Release [51.2kB]                 
Hit http://mirror.switch.ch gutsy-backports/main Packages                      
Hit http://mirror.switch.ch gutsy-backports/restricted Packages                
Hit http://mirror.switch.ch gutsy-backports/universe Packages                  
Hit http://mirror.switch.ch gutsy-backports/multiverse Packages                
Hit http://mirror.switch.ch gutsy-updates/main Packages                        
Hit http://mirror.switch.ch gutsy-updates/restricted Packages                  
Hit http://mirror.switch.ch gutsy-updates/main Sources                         
Hit http://mirror.switch.ch gutsy-updates/restricted Sources                   
Hit http://mirror.switch.ch gutsy-updates/universe Packages                    
Hit http://mirror.switch.ch gutsy-updates/multiverse Packages                  
Hit http://mirror.switch.ch gutsy-security/main Packages                       
Hit http://mirror.switch.ch gutsy-security/restricted Packages                 
Hit http://mirror.switch.ch gutsy-security/main Sources                        
Hit http://mirror.switch.ch gutsy-security/restricted Sources                  
Hit http://mirror.switch.ch gutsy-security/universe Packages                   
Hit http://mirror.switch.ch gutsy-security/universe Sources                    
Hit http://mirror.switch.ch gutsy-security/multiverse Packages                 
Hit http://mirror.switch.ch gutsy-security/multiverse Sources                  
Fetched 116kB in 9s (12.7kB/s)                                                 
Reading package lists... Done
edgar@EdgarPC:~$ 

```

---

### Post by Prisma on 2008-05-07
I am just trying to apply updates, I dont want to upgrade to 8.04 yet. :(

---

### Post by tamoneya on 2008-05-07
you dont have to upgrade to hardy dont worry.  This is just the output of the first command.  What happens when you run ```
sudo apt-get upgrade
```

---

### Post by Prisma on 2008-05-07
```
edgar@EdgarPC:~$ sudo apt-get upgrade
[sudo] password for edgar:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-utils avahi-autoipd avahi-daemon ca-certificates cupsys cupsys-bsd
  cupsys-client cupsys-common firefox firefox-gnome-support kdelibs-data
  kdelibs4c2a libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-howl0 libavahi-compat-libdnssd1 libavahi-core5
  libavahi-glib1 libavahi-qt3-1 libcupsimage2 libcupsys2 libhsqldb-java libpq5
  network-manager-gnome openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno ttf-opensymbol
  update-manager update-manager-core
46 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111MB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 30846 package `bluez-utils':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)
edgar@EdgarPC:~$ 


```

---

### Post by tamoneya on 2008-05-07
try these lines of code in terminal```
sudo dpkg --config -a
sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Prisma on 2008-05-07
Thank you for your help. I tried all of those commands but it gives me the same error message I posted before. :confused:

---

### Post by tamoneya on 2008-05-07
it seems like you have both gusty sources as well as feisty sources.  That could cause problems.  Look in /etc/apt/source.list and put a "#" before any line that mentions feisty.  Then try update and upgrade again.

---

### Post by Prisma on 2008-05-07
I put the # at the lines that you suggested. Nothing has changed.  :confused:


```
edgar@EdgarPC:~$ sudo sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-utils avahi-autoipd avahi-daemon ca-certificates cupsys cupsys-bsd
  cupsys-client cupsys-common firefox firefox-gnome-support kdelibs-data
  kdelibs4c2a libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-howl0 libavahi-compat-libdnssd1 libavahi-core5
  libavahi-glib1 libavahi-qt3-1 libcupsimage2 libcupsys2 libhsqldb-java libpq5
  network-manager-gnome openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno ttf-opensymbol
  update-manager update-manager-core
46 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111MB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 30846 package `bluez-utils':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)
edgar@EdgarPC:~$ 


```

---

### Post by Prisma on 2008-05-10
thank you to all the forum members who have help me so far. 

Can somebody redirect me to a place where I will be able to find the solution to my problem?

Problem:  I can't install anything in my pc. Neither with the update manager nor with the package manager, 
I can't delete programs as well. 

I haven't install anything. No new programs. :confused:

Thank you very much guys in advance.

---

### Post by DieB on 2008-05-10
As far as i assume the problem comes with following package bluez-utils.

So i would assume you uninstall that with:

sudo aptitude remove bluez-util

and after that redo the steps noted above.

---

### Post by Prisma on 2008-05-10
thank you Dieb

here is what happen when i tried to delete that pakage

```
edgar@EdgarPC:~$ sudo aptitude remove bluez-util
[sudo] password for edgar:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find package "bluez-util".  However, the following
packages contain "bluez-util" in their name:
  bluez-utils 
The following packages are unused and will be REMOVED:
  libaudacious5 libcrypt-ssleay-perl libglib1.2 libgnome-speech7 libgtk1.2 
  libgtk1.2-common libgtk2-trayicon-perl libntfs-3g12 libopal-2.2 librsync1 
  libsphinx2g0 libxine1-gnome libxml-libxml-common-perl libxml-libxml-perl 
  libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl 
  libxmmsclient-glib1 libxmmsclient2 python-setuptools sphinx2-hmm-6k 
The following packages have been automatically kept back:
  apt apt-utils kdelibs-data kdelibs4c2a libavahi-compat-howl0 
  libavahi-compat-libdnssd1 libavahi-qt3-1 libpq5 
The following packages have been kept back:
  avahi-autoipd avahi-daemon ca-certificates cupsys cupsys-bsd 
  cupsys-client cupsys-common firefox firefox-gnome-support 
  gstreamer0.10-esd gstreamer0.10-plugins-good libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core5 libavahi-glib1 
  libcupsimage2 libcupsys2 libhsqldb-java libspeex1 network-manager-gnome 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-filter-mobiledev 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python-uno 
  ttf-opensymbol update-manager update-manager-core vorbis-tools 
0 packages upgraded, 0 newly installed, 21 to remove and 50 not upgraded.
Need to get 0B of archives. After unpacking 40.1MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/available' near line 30846 package `bluez-utils':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 30846 package `bluez-utils':
 `Depends' field, missing package name, or garbage where package name expected
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
edgar@EdgarPC:~$ 


```

---

### Post by Prisma on 2008-05-10
I don't understand what the problem is. maybe some update I did before screwed up my system? :(

---

### Post by DieB on 2008-05-10
I'm sorry, had an typo in the post before, but atleast it did break before deleting.

please type following in terminal:

gedit /var/lib/dpkg/available

go to the preferences, check "show line numbers" (or somethin similar - i'm not running an english locale) and after that, go to line 30846 and let us know what it writes about bluez-utils

---

### Post by Prisma on 2008-05-10
```
Package: bluez-utils
Priority: optional
Section: admin
Installed-Size: 1272
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 3.19-0ubuntu3
Replaces: bluez-sdp (<= 1.5-2), bluez-pan
Depends: libasound2 (>> 1.0.14), libbluetooth2 (>= 3.12), libc6 (>= 2.6-1), libdbus-1-3 (>= 1.1.1), libglib2.0-0 (>= 2.14.0), libgstreamer-plugins-base0.10-0 (>= 0.10.14), libgstreamer0.10-0 (>= 0.10.14), libusb-0.1-4 (>= 2:0.1.12),  (>= 2.6.29), module-init-tools, makedev (<< 3.3.8.2-0) | udev, lsb-base (>= 3.0-3), dbus
Recommends: bluez-gnome
Suggests: bluez-firmware
Conflicts: bluez-sdp (<= 1.5-2), bluez-pan
Size: 471294
Description: Bluetooth tools and daemons
 This package contains tools and system daemons for using Bluetooth devices.
```


line: 30846

> Depends: libasound2 (>> 1.0.14), libbluetooth2 (>= 3.12), libc6 (>= 2.6-1), libdbus-1-3 (>= 1.1.1), libglib2.0-0 (>= 2.14.0), libgstreamer-plugins-base0.10-0 (>= 0.10.14), libgstreamer0.10-0 (>= 0.10.14), libusb-0.1-4 (>= 2:0.1.12),  (>= 2.6.29), module-init-tools, makedev (<< 3.3.8.2-0) | udev, lsb-base (>= 3.0-3), dbus

---

### Post by DieB on 2008-05-10
okay 

open the file again (this time with root rights)

sudo gedit ....

get to the line again.

Do you see following part:

...libusb-0.1-4 (>= 2:0.1.12), (>= 2.6.29), module-....

and take out the orphaned version specification, the one in brackets between the commas with no package name.

Save and start upgrade:

sudo apt-get upgrade

hope that helps

---

### Post by Prisma on 2008-05-10
> **DieB said:**
> okay 

open the file again (this time with root rights)

sudo gedit ....

get to the line again.

Do you see following part:

...libusb-0.1-4 (>= 2:0.1.12), (>= 2.6.29), module-....

and take out the orphaned version specification, the one in brackets between the commas with no package name.

Save and start upgrade:

sudo apt-get upgrade

hope that helps

I am sorry I don't understand. which part i should delete?

---

### Post by DieB on 2008-05-10
as u might have seen there is always a name of a package and in brackets () the version.
And there is one without package name:

(>= 2.6.29)

take it out and watch out to keep syntax okay, so delete the comma too

---

### Post by Prisma on 2008-05-10
IT WORKED!!!! 

Thank you. DieB you are the man!! \\:D/

---

