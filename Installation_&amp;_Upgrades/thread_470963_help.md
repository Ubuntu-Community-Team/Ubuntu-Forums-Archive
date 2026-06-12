---
title: "help"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by sunflower on 2007-06-11
OK... here's what I get when I click on the update icon.
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Someone asked me to do 'sudo apt-get update && sudo apt-get upgrade' so i did here's what i get...


marie@Sunflower:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
The following packages have been kept back:
linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
app-install-data-commercial apport apport-gtk capplets-data firefox
firefox-gnome-support gimp gimp-data gimp-python gnome-control-center
gnome-panel gnome-panel-data hwdb-client-common hwdb-client-gnome
libfreetype6 libgimp2.0 libgnome-window-settings1 libmetacity0 libnspr4
libnss3 libpanel-applet2-0 libslab0 libsmbclient linux-generic
linux-restricted-modules-common metacity metacity-common python
python-apport python-gdbm python-minimal python-problem-report python2.5
python2.5-minimal rdesktop samba-common smbclient tzdata unattended-upgrades
update-manager update-manager-core vim-common vim-tiny
43 upgraded, 0 newly installed, 9 to remove and 3 not upgraded.
9 not fully installed or removed.
Need to get 0B/35.9MB of archives.
After unpacking 9110kB disk space will be freed.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
subprocess post-removal script returned error exit status 139
Removing libcairomm-1.0-1 ...
Segmentation fault (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
subprocess post-removal script returned error exit status 139
Removing libdebconfclient0 ...
Segmentation fault (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
subprocess post-removal script returned error exit status 139
Removing libdebian-installer4 ...
Segmentation fault (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
subprocess post-removal script returned error exit status 139
Removing libdiscover1 ...
Segmentation fault (core dumped)
dpkg: error processing libdiscover1 (--remove):
subprocess post-removal script returned error exit status 139
Removing libfuse2 ...
Segmentation fault (core dumped)
dpkg: error processing libfuse2 (--remove):
subprocess post-removal script returned error exit status 139
Removing libglibmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
subprocess post-removal script returned error exit status 139
Removing libntfs9 ...
Segmentation fault (core dumped)
dpkg: error processing libntfs9 (--remove):
subprocess post-removal script returned error exit status 139
Removing xfsprogs ...
Segmentation fault (core dumped)
dpkg: error processing xfsprogs (--remove):
subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
libgtkmm-2.4-1c2a
libcairomm-1.0-1
libdebconfclient0
libdebian-installer4
libdiscover1
libfuse2
libglibmm-2.4-1c2a
libntfs9
xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm new to all this... please help me fix this problem!

---

### Post by taurus on 2007-06-11
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by sunflower on 2007-06-11
marie@Sunflower:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 46 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libcairomm-1.0-1 ...
Segmentation fault (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebconfclient0 ...
Segmentation fault (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebian-installer4 ...
Segmentation fault (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdiscover1 ...
Segmentation fault (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libfuse2 ...
Segmentation fault (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libglibmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libntfs9 ...
Segmentation fault (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 139
Removing xfsprogs ...
Segmentation fault (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)
marie@Sunflower:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
marie@Sunflower:~$

---

### Post by Chemroydal Tissue on 2007-06-18
I'm getting the same error message, but only for the package: gnome-btdownload. Any ideas?

---

### Post by sunflower on 2007-06-18
you've got 5 cups of ubuntu... i've got one. I haven't received any help :( and i don't know what to do... 
I also get this message when i do add/remove......

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I don't know what /etc/apt/sources.list is.. i don't know what to do.... 
I need heeeeeeeeeeeeelp!!!

---

### Post by sunflower on 2007-06-18
OK 
results for [COLOR="Red"]cat /etc/apt/sources.list[/COLOR] 

marie@Sunflower:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
marie@Sunflower:~$

What to do now?

---

