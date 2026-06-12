---
title: "Errors with package installation, dpkg, Error 1"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by erikschneider21 on 2008-06-12
Heya, I'm new to Ubuntu/Linux (have only been using it the past few days, but I am learning extremely quickly) and I'm also new to these forums, so I hope this is the right spot for my problem:

Whenever I use sudo apt-get install (or Synaptic) to try and get some software, I get an Error 1 and something to do with dpkg and dependencies, which it lists:

From command line attempts:
 linux-image-2.6.24-18-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

From Synaptic:
E: linux-image-2.6.24-18-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

I have attempted to reinstall the above packages, because I've read forums of people having similar problems, but I get the very same error when I try to do reinstall them! It seems circular. The same forums I read lead me to believe it was because the package manager froze while updating and I had to reboot.

I'm pretty sure it's because these are some pretty important components of the OS. I really don't want to have to reinstall though, because I'm on a Macbook Pro that I have invested tons of time getting to work. (My setup is a dual-boot XP x64 and Ubuntu Hardy amd64, without Mac OS, and it was an incredible pain to get [drivers, bootloader & tables] working properly having reformatted maybe ten times in the last couple of days)

Any help would be greatly appreciated.

Thanks,

Erik

---

### Post by Pumalite on 2008-06-12
Try:
sudo apt-get update
sudo apt-get dist-upgrade
Post the output.

---

### Post by erikschneider21 on 2008-06-13
```
erik@computer:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2) hardy/main Translation-en_CA
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2) hardy/restricted Translation-en_CA
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_CA               
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_CA                      
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://security.ubuntu.com hardy-security Release.gpg [191B]             
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA     
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA 
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Get:3 http://security.ubuntu.com hardy-security Release [58.5kB]               
Hit http://ca.archive.ubuntu.com hardy Release.gpg                             
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA                  
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA       
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA         
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA       
Get:4 http://ca.archive.ubuntu.com hardy-updates Release.gpg [191B]       
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA     
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ppa.launchpad.net hardy/main Sources                           
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA 
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy Release       
Hit http://ppa.launchpad.net hardy/main Packages                               
Get:5 http://ca.archive.ubuntu.com hardy-updates Release [58.5kB]          
Hit http://ppa.launchpad.net hardy/main Sources                                
Get:6 http://security.ubuntu.com hardy-security/restricted Packages [6022B]    
Get:7 http://security.ubuntu.com hardy-security/main Packages [22.9kB]         
Get:8 http://security.ubuntu.com hardy-security/multiverse Packages [3457B]
Get:9 http://security.ubuntu.com hardy-security/universe Packages [13.0kB]
Hit http://ca.archive.ubuntu.com hardy/main Packages                      
Hit http://ca.archive.ubuntu.com hardy/restricted Packages                 
Hit http://ca.archive.ubuntu.com hardy/main Sources                        
Hit http://ca.archive.ubuntu.com hardy/restricted Sources                  
Hit http://ca.archive.ubuntu.com hardy/universe Packages                   
Hit http://ca.archive.ubuntu.com hardy/universe Sources                    
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages                 
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources                  
Get:10 http://ca.archive.ubuntu.com hardy-updates/main Packages [207kB]    
Get:11 http://ca.archive.ubuntu.com hardy-updates/restricted Packages [6022B]
Get:12 http://ca.archive.ubuntu.com hardy-updates/main Sources [69.6kB]
Get:13 http://ca.archive.ubuntu.com hardy-updates/restricted Sources [906B]
Get:14 http://ca.archive.ubuntu.com hardy-updates/universe Packages [40.4kB]
Get:15 http://ca.archive.ubuntu.com hardy-updates/universe Sources [7036B]
Get:16 http://ca.archive.ubuntu.com hardy-updates/multiverse Packages [7696B]
Get:17 http://ca.archive.ubuntu.com hardy-updates/multiverse Sources [1433B]
Fetched 503kB in 3s (138kB/s)                             
Reading package lists... Done
erik@computer:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  deskbar-applet openssl-blacklist xserver-xorg-core
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 11.1MB of archives.
After this operation, 4211kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com hardy-security/main openssl-blacklist 0.3.3+0.4-0ubuntu0.8.04.1 [6333kB]
Get:2 http://ca.archive.ubuntu.com hardy-updates/main deskbar-applet 2.22.2.1-0ubuntu1 [344kB]
Get:3 http://security.ubuntu.com hardy-security/main xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9.2 [4424kB]
Fetched 11.1MB in 21s (527kB/s)                                                                                           
(Reading database ... 114982 files and directories currently installed.)
Preparing to replace openssl-blacklist 0.1-0ubuntu0.8.04.4 (using .../openssl-blacklist_0.3.3+0.4-0ubuntu0.8.04.1_all.deb) ...
Unpacking replacement openssl-blacklist ...
Preparing to replace deskbar-applet 2.22.1-0ubuntu1 (using .../deskbar-applet_2.22.2.1-0ubuntu1_amd64.deb) ...
Unpacking replacement deskbar-applet ...
Preparing to replace xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9 (using .../xserver-xorg-core_2%3a1.4.1~git20080131-1ubuntu9.2_amd64.deb) ...
Unpacking replacement xserver-xorg-core ...
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up openssl-blacklist (0.3.3+0.4-0ubuntu0.8.04.1) ...
Setting up deskbar-applet (2.22.2.1-0ubuntu1) ...

Setting up xserver-xorg-core (2:1.4.1~git20080131-1ubuntu9.2) ...
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:|

---

### Post by Pumalite on 2008-06-13
Post:
uname -a

---

### Post by eljaco on 2008-06-13
I'm having a similar problem and was wondering if it was related:

```
jaco@Mickey:~$ sudo apt-get update; sudo apt-get dist-upgrade; uname -a
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy/universe Translation-en_US
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://archive.canonical.com hardy Release
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://archive.canonical.com hardy/partner Sources
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Hit http://packages.medibuntu.org hardy/free Packages
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Ign http://ppa.launchpad.net hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://archive.canonical.com hardy/partner Packages
Hit http://us.archive.ubuntu.com hardy-backports Release
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://ppa.launchpad.net hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Fetched 1B in 0s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Linux Mickey 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux
jaco@Mickey:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jaco@Mickey:~$ sudo !!
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-1-0:
 libgdl-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 python-gnome2-extras depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.0-cil:
 libgnome2.0-cil depends on libgnome-vfs2.0-cil (>= 2.20.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 libgnome2.0-cil depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-3 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on libgweather1; however:
  Package libgweather1 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser10:
 libtotem-plparser10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-gnomevfs:
 gstreamer0.10-gnomevfs depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gstreamer0.10-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-perl:
 libgnome2-perl depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome2-perl depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome2-perl depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome2-perl depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-9 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.22.2); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 2.22.2); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 2.22.2); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgoffice-0-6:
 libgoffice-0-6 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgoffice-0-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgoffice-0-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libebook1.2-9 (>= 2.21.92); however:
  Package libebook1.2-9 is not configured yet.
 python-gnome2-desktop depends on libecal1.2-7 (>= 2.21.92); however:
  Package libecal1.2-7 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser10 (>= 2.21.92); however:
  Package libtotem-plparser10 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-vfs-perl:
 libgnome2-vfs-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-vfs-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeel2-2:
 libeel2-2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libeel2-2 depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 libeel2-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libeel2-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libeel2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libeel2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-gecko:
 epiphany-gecko depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 epiphany-gecko depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 epiphany-gecko depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 epiphany-gecko depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 epiphany-gecko depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing epiphany-gecko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-8 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on python-gnome2 (>= 2.12.4-1); however:
  Package python-gnome2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-gnome-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgsf-gnome-1-114:
 libgsf-gnome-1-114 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgsf-gnome-1-114 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslab0:
 libslab0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libslab0 depends on libeel2-2 (>= 2.21.90); however:
  Package libeel2-2 is not configured yet.
 libslab0 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libslab0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libslab0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libslab0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libslab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center
 libgnomevfs2-extra
 libgnomevfs2-0
 nautilus
 libgtkhtml3.14-19
 xulrunner-1.9-gnome-support
 libedata-book1.2-2
 libedata-cal1.2-6
 libgnome-vfs2.0-cil
 libgnome2-0
 policykit-gnome
 libgdl-1-0
 python-gnome2-extras
 libbonoboui2-0
 python-gnome2
 libgnome2.0-cil
 libgweather1
 libexchange-storage1.2-3
 gnome-panel
 libgnomeui-0
 libtotem-plparser10
 gstreamer0.10-gnomevfs
 libgnome-window-settings1
 libgnome2-perl
 libecal1.2-7
 libebook1.2-9
 evolution-data-server
 libpanel-applet2-0
 libgoffice-0-6
 firefox-3.0-gnome-support
 libgnome-desktop-2
 gtkhtml3.14
 python-gnome2-desktop
 libgnome2-vfs-perl
 libeel2-2
 epiphany-gecko
 libedataserverui1.2-8
 deskbar-applet
 libcamel1.2-11
 libgdl-gnome-1-0
 libgsf-gnome-1-114
 libslab0
 firefox-gnome-support
 liblpint-bonobo0
```

Thanks!

---

### Post by zvacet on 2008-06-13
```
sudo dpkg --configure -a
```

---

### Post by eljaco on 2008-06-13
I did that with no avail - the output is in my previous reply.

---

### Post by mdweezer on 2008-06-13
Same issue here...

> 
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-image-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any progress?

---

### Post by avtolle on 2008-06-13
A wild shot in the dark; if you have a separate /boot partition, is it full?

---

### Post by zvacet on 2008-06-14
@ **eljaco**

```
sudo dpkg --configure gnome-settings-daemon
```

```
sudo dpkg --configure libgnomevfs2-common
```

```
sudo dpkg --configure -a
```

@ **erikschneider**

```
sudo dpkg --configure linux-image-2.6.24-18-generic
```

```
sudo dpkg --configure -a
```

---

### Post by eljaco on 2008-06-14
zvacet: I tried doing what you suggested, but it boiled down to some gconf error. This is my terminal output:
```
jaco@Mickey:~$ sudo dpkg --configure gnome-settings-daemon
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-settings-daemon depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-settings-daemon depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-settings-daemon depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-settings-daemon depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-settings-daemon
jaco@Mickey:~$ sudo dpkg --configure libgnome2-0
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome2-0
jaco@Mickey:~$ sudo dpkg --configure libgnomevfs2-0
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomevfs2-0
jaco@Mickey:~$ sudo dpkg --configure libgnomevfs2-common
Setting up libgnomevfs2-common (1:2.22.0-2ubuntu1) ...

(gconftool-2:6740): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:6740): GConf-WARNING **: Failed to load source "xml:readwrite:/var/lib/gconf/defaults": Failed: Couldn't locate backend module for `xml:readwrite:/var/lib/gconf/defaults'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing libgnomevfs2-common (--configure):
 subprocess post-installation script returned error exit status 250
Errors were encountered while processing:
 libgnomevfs2-common
jaco@Mickey:~$
```

Does anyone know where I can get /usr/lib/libgconf2-4/2/libgconfbackend-xml.so ?

---

### Post by erikschneider21 on 2008-06-16
Sorry... I don't have internet at home right now and I've been kinda busy.

> **Pumalite said:**
> Post:
uname -a

```
Linux computer 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```


[QUOTE=zvacet]
@ **erikschneider**

```
sudo dpkg --configure linux-image-2.6.24-18-generic
```

```
sudo dpkg --configure -a
```[/QUOTE]

```
erik@computer:~$ sudo dpkg --configure linux-image-2.6.24-18-generic
[sudo] password for erik: 
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
```

```
erik@computer-go:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
```

](*,)

---

### Post by iaculallad on 2008-06-16
Try this in your terminal:

```
sudo apt-get install util-linux
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by erikschneider21 on 2008-06-16
> **iaculallad said:**
> Try this in your terminal:

```
sudo apt-get install util-linux
sudo apt-get update && sudo apt-get upgrade
```

Same error with same dependencies listed.

---

### Post by PmDematagoda on 2008-06-16
Post the output of:-
```
ls /sbin
```

---

### Post by erikschneider21 on 2008-06-20
I thought I had posted it. I guess it didn't go through.

Anyhow, I took the coward's way out and formatted. I had to get stuff done and this was just not working.

/harakiri computer.

I thank you all for your help. I really appreciate it.

Erik

---

### Post by SoundFriend on 2008-06-20
I've had similar problems upgrading the kernel a number of times since installing Hardy.

During upgrades, a colour text/graphics windows opens, and you then select how to update the /boot/grub/menu.lst file.  I have been selecting "3 way merge" which has (always) failed to work, returning error code 1.  Selecting "Install Package Maintainers Version" should work, but in fact I selected the default (Leave original file) and then edited menu.lst manually to the new kernel id which worked.

So, why does the select window default to leave menu.lst unmodified, and why doesn't 3 way merge (experimental) get fixed? :)

SF

---

