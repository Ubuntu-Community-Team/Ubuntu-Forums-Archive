---
title: "[SOLVED] package error"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by chrismarsh1987 on 2008-11-10
booted up, still having problems with installing packages/upgrades and codecs, but now this has appeared and im totaly new to this and need step by step advice

An error occurred, please run package manager from the right click menu or apt-get in terminal to see what is wrong. The error message was “Error: openeing the cache (E:read error-read (5 error input/output error), E::the package lists or status file could not be parsed or opened.)” this usualy means that your installed packages have unmet dependancies

help anyone?

---

### Post by taurus on 2008-11-10
Is there any error message if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chrismarsh1987 on 2008-11-10
> **taurus said:**
> Is there any error message if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

message for sudo apt-get update is

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@andromeda:/var/cache/apt/archives# 


error message for sudo apt-get upgrade is

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libpam-runtime_1.0.1-4ubuntu5.2_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `python-dbus': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libpam-runtime_1.0.1-4ubuntu5.2_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@andromeda:/var/cache/apt/archives#

---

### Post by taurus on 2008-11-10
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line (or the line that has cdrom in it) to comment it out.  Then, save it and close gedit window.  Now, what happens if you run those two commands again?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chrismarsh1987 on 2008-11-10
> **taurus said:**
> Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line (or the line that has cdrom in it) to comment it out.  Then, save it and close gedit window.  Now, what happens if you run those two commands again?

```
sudo apt-get update
sudo apt-get upgrade
```

sorry can u explain that in more detail as it doesnt make sence to me sorry

---

### Post by chrismarsh1987 on 2008-11-10
> **taurus said:**
> Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line (or the line that has cdrom in it) to comment it out.  Then, save it and close gedit window.  Now, what happens if you run those two commands again?

```
sudo apt-get update
sudo apt-get upgrade
```

administrator@andromeda:~$ gksudo gedit /etc/apt/sources.list
administrator@andromeda:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]           
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release [65.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources       
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages [1256kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources [505kB]
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources [3113B]        
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages [8408B]    
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources [3113B]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources [505kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources [95.8kB]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources [1981kB]
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages [4542kB]       
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages [199kB]      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Fetched 9231kB in 18s (487kB/s)                                                
Reading package lists... Done
administrator@andromeda:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be upgraded:
  base-files capplets-data command-not-found command-not-found-data compiz
  compiz-core compiz-gnome compiz-plugins compiz-wrapper f-spot
  gdm-guest-session gedit gedit-common gnome-control-center gnome-panel
  gnome-panel-data gnome-pilot human-theme jockey-common jockey-gtk
  libasound2-plugins libdecoration0 libglib2.0-0 libglib2.0-data
  libgnome-pilot2 libgnome-window-settings1 libgphoto2-2 libgphoto2-port0
  libgtksourceview2.0-0 libgtksourceview2.0-common libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libtotem-plparser12 libvolume-id0 linux-headers-2.6.27-7
  linux-headers-2.6.27-7-generic linux-image-2.6.27-7-generic linux-libc-dev
  nvidia-96-modaliases pm-utils procps python-software-properties rhythmbox
  software-properties-gtk system-tools-backends totem totem-common
  totem-gstreamer totem-mozilla totem-plugins transmission-common
  transmission-gtk udev update-manager update-manager-core
  xserver-xorg-input-evdev xserver-xorg-input-vmmouse
61 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/51.5MB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libpam-runtime_1.0.1-4ubuntu5.2_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `python-dbus': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libpam-runtime_1.0.1-4ubuntu5.2_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
administrator@andromeda:~$

---

