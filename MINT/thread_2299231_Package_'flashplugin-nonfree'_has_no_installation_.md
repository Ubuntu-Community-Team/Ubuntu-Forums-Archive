---
title: "Package 'flashplugin-nonfree' has no installation candidate"
date: 2015-10-16
forum: MINT
---

### Post by parker-hugh on 2015-10-16
Hi,

Linux Mint 17.2 Cinnamon installed on Vostro 1520 laptop. Default browser is Firefox.

I realise that Firefox no longer supports flash and I do have chromium that I can use, but I prefer to use Firefox to watch YouTube (mainly because of my bookmarks and very important flash block which lets me control when a video plays when I have multiple tabs open). 

So I thought I could just run sudo apt-get install flashplugin-nonfree and that would fix it, but I get an error message and can't progress any further....

```
hugh@DELL-VOSTRO-MINT ~ $ sudo apt-get install flashplugin-nonfree
[sudo] password for hugh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is a virtual package provided by:
  adobe-flashplugin 1:20151013.1-0trusty1
  flashplugin-installer:i386 11.2.202.540ubuntu0.14.04.2
  flashplugin-installer 11.2.202.540ubuntu0.14.04.2
You should explicitly select one to install.

E: Package 'flashplugin-nonfree' has no installation candidate
hugh@DELL-VOSTRO-MINT ~ $ 
```
Is there any way I can update flash so i can continue to use Firefox to watch YouTube?

BBC iPlayer seems to be unaffected.

Any help would be appreciated

---

### Post by Frogs Hair on 2015-10-16
Try the following . ```
sudo apt-get install flashplugin-installer
``` If you want to use Pepperflash: ```
sudo apt-get install pepperflashplugin-nonfree
```

---

### Post by parker-hugh on 2015-10-17
> **Frogs Hair said:**
> Try the following . ```
sudo apt-get install flashplugin-installer
``` If you want to use Pepperflash: ```
sudo apt-get install pepperflashplugin-nonfree
```
Thanks for the reply to my post, I tried running the command suggested, but there was an error at the end...
```
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get install flashplugin-installer
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED
  adobe-flash-properties-gtk adobe-flashplugin
The following NEW packages will be installed
  flashplugin-installer
0 to upgrade, 1 to newly install, 2 to remove and 0 not to upgrade.
Need to get 6,838 B of archives.
After this operation, 37.4 MB disk space will be freed.
Do you want to continue? [Y/n] 

Err http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse flashplugin-installer amd64 11.2.202.521ubuntu0.14.04.1
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/multiverse flashplugin-installer amd64 11.2.202.521ubuntu0.14.04.1
  404  Not Found [IP: 91.189.91.13 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.521ubuntu0.14.04.1_amd64.deb  404  Not Found [IP: 91.189.91.13 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
hugh@SONY-VAIO-UBUNTU:~$
``` 
I'm afraid I don't know what I can do to resolve this error.

I checked my version of flash...

Flash Player version for Linux should be 11.2.202.540
my installed version of Flash is only at 11.2.202.521 

I also tried running the other command but message states I already have the current version installed...
```
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get install pepperflashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pepperflashplugin-nonfree is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 55 not to upgrade.
hugh@SONY-VAIO-UBUNTU:~$
``` 

Is pepperflashplugin only used by chrome and chromium,  but not used by Firefox?

Any suggestions on how to upgrade flash in Firefox would be much appreciated.

---

### Post by deadflowr on 2015-10-17
You currently have 55 packages that you can upgrade.
What happens after you run
```
sudo apt-get update && sudo apt-get upgrade
```
?
After the system is up-to-date does the flashplugin-installer version match correctly?

---

### Post by parker-hugh on 2015-10-17
> **deadflowr said:**
> You currently have 55 packages that you can upgrade.
What happens after you run
```
sudo apt-get update && sudo apt-get upgrade
```
?
After the system is up-to-date does the flashplugin-installer version match correctly?
thanks again for reply, I ran the code and this is the output ....
```
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get update
Hit http://download.virtualbox.org trusty InRelease
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Hit http://download.virtualbox.org trusty/contrib amd64 Packages               
Get:2 http://gb.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://download.virtualbox.org trusty/contrib i386 Packages                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:3 http://gb.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:4 http://gb.archive.ubuntu.com trusty-updates/main Sources [239 kB]        
Get:5 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:6 http://ppa.launchpad.net trusty Release [11.9 kB]                        
Get:7 http://ppa.launchpad.net trusty/main amd64 Packages [575 B]              
Get:8 http://ppa.launchpad.net trusty/main i386 Packages [575 B]               
Ign http://download.virtualbox.org trusty/contrib Translation-en_GB            
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:9 http://security.ubuntu.com trusty-security/main Sources [97.6 kB]        
Ign http://download.virtualbox.org trusty/contrib Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:10 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B]
Get:11 http://gb.archive.ubuntu.com trusty-updates/universe Sources [140 kB]   
Get:12 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B]
Get:13 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [631 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:14 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B] 
Get:15 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:16 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Get:17 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB] 
Get:18 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B] 
Get:19 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:20 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [611 kB]
Get:21 http://security.ubuntu.com trusty-security/main amd64 Packages [351 kB]
Get:22 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:23 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Get:24 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:25 http://gb.archive.ubuntu.com trusty-backports/main Sources [5,860 B]    
Get:26 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:27 http://gb.archive.ubuntu.com trusty-backports/universe Sources [29.7 kB]
Get:28 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:29 http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages [6,288 B]
Get:30 http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:31 http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages [35.5 kB]
Get:32 http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:33 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [6,293 B]
Get:34 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:35 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [35.5 kB]
Get:36 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://gb.archive.ubuntu.com trusty Release                                
Hit http://gb.archive.ubuntu.com trusty/main Sources      
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Hit http://gb.archive.ubuntu.com trusty/universe Sources                    
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                  
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages                 
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages          
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages            
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages          
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages                 
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages           
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages             
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages           
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB             
Hit http://gb.archive.ubuntu.com trusty/main Translation-en                    
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en          
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en                
Get:37 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:38 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:39 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:40 http://security.ubuntu.com trusty-security/main i386 Packages [334 kB]  
Get:41 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:42 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:43 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Fetched 3,750 kB in 14s (267 kB/s)                                             
Reading package lists... Done
hugh@SONY-VAIO-UBUNTU:~$ 
```

```
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin chromium-browser
  chromium-browser-l10n chromium-codecs-ffmpeg-extra dkms firefox
  firefox-locale-en gir1.2-gdkpixbuf-2.0 gir1.2-gudev-1.0 libcgmanager0
  libegl1-mesa libegl1-mesa-drivers libgbm1 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgles2-mesa libgudev-1.0-0 libhunspell-1.3-0 libopenvg1-mesa
  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 libpam-systemd
  libspice-server1 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0
  libudev1 libwayland-egl1-mesa libxatracker2 linux-libc-dev
  oxideqt-codecs-extra python3-distupgrade python3-software-properties
  python3-update-manager software-properties-common software-properties-gtk
  systemd-services thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udev update-manager
  update-manager-core
52 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
Need to get 181 MB of archives.
After this operation, 468 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libcgmanager0 amd64 0.24-0ubuntu7.5 [28.9 kB]
Get:2 http://archive.canonical.com/ubuntu/ trusty/partner adobe-flash-properties-gtk amd64 1:20151013.1-0trusty1 [113 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main udev amd64 204-5ubuntu20.15 [735 kB]
Get:4 http://archive.canonical.com/ubuntu/ trusty/partner adobe-flashplugin amd64 1:20151013.1-0trusty1 [10.1 MB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 amd64 204-5ubuntu20.15 [33.4 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.15 [25.5 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.15 [197 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.15 [9,900 B]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.15 [26.9 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/universe chromium-browser-l10n all 45.0.2454.101-0ubuntu0.14.04.1.1099 [3,504 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgdk-pixbuf2.0-0 amd64 2.30.7-0ubuntu1.2 [160 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgdk-pixbuf2.0-common all 2.30.7-0ubuntu1.2 [8,826 B]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/universe chromium-browser amd64 45.0.2454.101-0ubuntu0.14.04.1.1099 [54.3 MB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/universe chromium-codecs-ffmpeg-extra amd64 45.0.2454.101-0ubuntu0.14.04.1.1099 [860 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-dri amd64 10.1.3-0ubuntu0.5 [4,742 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgbm1 amd64 10.1.3-0ubuntu0.5 [19.1 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx amd64 10.1.3-0ubuntu0.5 [113 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgles2-mesa amd64 10.1.3-0ubuntu0.5 [12.5 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libwayland-egl1-mesa amd64 10.1.3-0ubuntu0.5 [6,482 B]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa-drivers amd64 10.1.3-0ubuntu0.5 [1,993 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa amd64 10.1.3-0ubuntu0.5 [20.6 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libopenvg1-mesa amd64 10.1.3-0ubuntu0.5 [12.9 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa amd64 10.1.3-0ubuntu0.5 [59.1 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgudev-1.0-0 amd64 1:204-5ubuntu20.15 [14.1 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libhunspell-1.3-0 amd64 1.3.2-6ubuntu2.1 [108 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libspice-server1 amd64 0.12.4-0nocelt2ubuntu1.2 [322 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxatracker2 amd64 10.1.3-0ubuntu0.5 [143 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 amd64 204-5ubuntu20.15 [49.7 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main ubuntu-release-upgrader-gtk all 1:0.220.8 [9,318 B]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main ubuntu-release-upgrader-core all 1:0.220.8 [23.1 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-distupgrade all 1:0.220.8 [104 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main update-manager all 1:0.196.14 [544 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main update-manager-core all 1:0.196.14 [5,270 B]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-update-manager all 1:0.196.14 [31.6 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04.5 [65.4 kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox amd64 41.0.2+build2-0ubuntu0.14.04.1 [41.5 MB]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox-locale-en amd64 41.0.2+build2-0ubuntu0.14.04.1 [667 kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gdkpixbuf-2.0 amd64 2.30.7-0ubuntu1.2 [7,964 B]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gudev-1.0 amd64 1:204-5ubuntu20.15 [5,488 B]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-65.106 [773 kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main software-properties-common all 0.92.37.5 [9,370 B]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main software-properties-gtk all 0.92.37.5 [46.8 kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-software-properties all 0.92.37.5 [19.1 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [349 kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [32.8 MB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-gnome-support amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [8,536 B]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en-gb all 1:38.3.0+build1-0ubuntu0.14.04.1 [9,984 B]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en-us all 1:38.3.0+build1-0ubuntu0.14.04.1 [9,986 B]
Get:49 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqt-qmlplugin amd64 1.9.5-0ubuntu0.14.04.1 [178 kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqtquick0 amd64 1.9.5-0ubuntu0.14.04.1 [256 kB]
Get:51 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqtcore0 amd64 1.9.5-0ubuntu0.14.04.1 [25.0 MB]
Get:52 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main oxideqt-codecs-extra amd64 1.9.5-0ubuntu0.14.04.1 [866 kB]
Fetched 181 MB in 2min 14s (1,345 kB/s)                                        
Extract templates from packages: 100%
(Reading database ... 371057 files and directories currently installed.)
Preparing to unpack .../libcgmanager0_0.24-0ubuntu7.5_amd64.deb ...
Unpacking libcgmanager0:amd64 (0.24-0ubuntu7.5) over (0.24-0ubuntu7.3) ...
Preparing to unpack .../udev_204-5ubuntu20.15_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../libudev1_204-5ubuntu20.15_amd64.deb ...
Unpacking libudev1:amd64 (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.15_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.15_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.15_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.15_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../chromium-browser-l10n_45.0.2454.101-0ubuntu0.14.04.1.1099_all.deb ...
Unpacking chromium-browser-l10n (45.0.2454.101-0ubuntu0.14.04.1.1099) over (45.0.2454.85-0ubuntu0.14.04.1.1097) ...
Preparing to unpack .../libgdk-pixbuf2.0-0_2.30.7-0ubuntu1.2_amd64.deb ...
Unpacking libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1.2) over (2.30.7-0ubuntu1.1) ...
Preparing to unpack .../libgdk-pixbuf2.0-common_2.30.7-0ubuntu1.2_all.deb ...
Unpacking libgdk-pixbuf2.0-common (2.30.7-0ubuntu1.2) over (2.30.7-0ubuntu1.1) ...
Preparing to unpack .../chromium-browser_45.0.2454.101-0ubuntu0.14.04.1.1099_amd64.deb ...
Unpacking chromium-browser (45.0.2454.101-0ubuntu0.14.04.1.1099) over (45.0.2454.85-0ubuntu0.14.04.1.1097) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_45.0.2454.101-0ubuntu0.14.04.1.1099_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (45.0.2454.101-0ubuntu0.14.04.1.1099) over (45.0.2454.85-0ubuntu0.14.04.1.1097) ...
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libgbm1_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libgbm1:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libgles2-mesa_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libgles2-mesa:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libwayland-egl1-mesa_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libegl1-mesa-drivers_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libglapi-mesa:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libopenvg1-mesa_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libegl1-mesa_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libegl1-mesa:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libgudev-1.0-0_1%3a204-5ubuntu20.15_amd64.deb ...
Unpacking libgudev-1.0-0:amd64 (1:204-5ubuntu20.15) over (1:204-5ubuntu20.14) ...
Preparing to unpack .../libhunspell-1.3-0_1.3.2-6ubuntu2.1_amd64.deb ...
Unpacking libhunspell-1.3-0:amd64 (1.3.2-6ubuntu2.1) over (1.3.2-6ubuntu2) ...
Preparing to unpack .../libspice-server1_0.12.4-0nocelt2ubuntu1.2_amd64.deb ...
Unpacking libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.2) over (0.12.4-0nocelt2ubuntu1.1) ...
Preparing to unpack .../libxatracker2_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libxatracker2:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.15_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.15) over (204-5ubuntu20.14) ...
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a0.220.8_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:0.220.8) over (1:0.220.7) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a0.220.8_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:0.220.8) over (1:0.220.7) ...
Preparing to unpack .../python3-distupgrade_1%3a0.220.8_all.deb ...
Unpacking python3-distupgrade (1:0.220.8) over (1:0.220.7) ...
Preparing to unpack .../update-manager_1%3a0.196.14_all.deb ...
Unpacking update-manager (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../update-manager-core_1%3a0.196.14_all.deb ...
Unpacking update-manager-core (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../python3-update-manager_1%3a0.196.14_all.deb ...
Unpacking python3-update-manager (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20151013.1-0trusty1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20151013.1-0trusty1) over (1:20150921.1-0trusty1) ...
Preparing to unpack .../adobe-flashplugin_1%3a20151013.1-0trusty1_amd64.deb ...
Unpacking adobe-flashplugin (1:20151013.1-0trusty1) over (1:20150921.1-0trusty1) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.5) over (2.2.0.3-1.1ubuntu5.14.04.2) ...
Preparing to unpack .../firefox_41.0.2+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox (41.0.2+build2-0ubuntu0.14.04.1) over (41.0+build3-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-en_41.0.2+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox-locale-en (41.0.2+build2-0ubuntu0.14.04.1) over (41.0+build3-0ubuntu0.14.04.1) ...
Preparing to unpack .../gir1.2-gdkpixbuf-2.0_2.30.7-0ubuntu1.2_amd64.deb ...
Unpacking gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.2) over (2.30.7-0ubuntu1.1) ...
Preparing to unpack .../gir1.2-gudev-1.0_1%3a204-5ubuntu20.15_amd64.deb ...
Unpacking gir1.2-gudev-1.0 (1:204-5ubuntu20.15) over (1:204-5ubuntu20.14) ...
Preparing to unpack .../linux-libc-dev_3.13.0-65.106_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-65.106) over (3.13.0-63.103) ...
Preparing to unpack .../software-properties-common_0.92.37.5_all.deb ...
Unpacking software-properties-common (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../software-properties-gtk_0.92.37.5_all.deb ...
Unpacking software-properties-gtk (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../python3-software-properties_0.92.37.5_all.deb ...
Unpacking python3-software-properties (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../thunderbird-locale-en_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-locale-en-gb_1%3a38.3.0+build1-0ubuntu0.14.04.1_all.deb ...
Unpacking thunderbird-locale-en-gb (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.3.0+build1-0ubuntu0.14.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtquick0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtcore0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../oxideqt-codecs-extra_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.13-1) ...

(gtk-update-icon-cache-3.0:5105): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Setting up libcgmanager0:amd64 (0.24-0ubuntu7.5) ...
Setting up libudev1:amd64 (204-5ubuntu20.15) ...
Setting up udev (204-5ubuntu20.15) ...
udev stop/waiting
udev start/running, process 5179
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.15) ...
Setting up systemd-services (204-5ubuntu20.15) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.15) ...
systemd-logind start/running, process 5248
Setting up libsystemd-login0:amd64 (204-5ubuntu20.15) ...
Setting up libgdk-pixbuf2.0-common (2.30.7-0ubuntu1.2) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1.2) ...
Setting up chromium-codecs-ffmpeg-extra (45.0.2454.101-0ubuntu0.14.04.1.1099) ...
Setting up chromium-browser (45.0.2454.101-0ubuntu0.14.04.1.1099) ...
Setting up chromium-browser-l10n (45.0.2454.101-0ubuntu0.14.04.1.1099) ...
Setting up libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libgbm1:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libglapi-mesa:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libgles2-mesa:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libegl1-mesa:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libgudev-1.0-0:amd64 (1:204-5ubuntu20.15) ...
Setting up libhunspell-1.3-0:amd64 (1.3.2-6ubuntu2.1) ...
Setting up libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.2) ...
Setting up libxatracker2:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.15) ...
Setting up adobe-flashplugin (1:20151013.1-0trusty1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20151013.1-0trusty1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Setting up firefox (41.0.2+build2-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (41.0.2+build2-0ubuntu0.14.04.1) ...
Setting up gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.2) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.15) ...
Setting up linux-libc-dev:amd64 (3.13.0-65.106) ...
Setting up python3-software-properties (0.92.37.5) ...
Setting up software-properties-common (0.92.37.5) ...
Setting up software-properties-gtk (0.92.37.5) ...
Setting up thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-locale-en (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en-gb (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en-us (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up oxideqt-codecs-extra:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up python3-update-manager (1:0.196.14) ...
Setting up python3-distupgrade (1:0.220.8) ...
Setting up ubuntu-release-upgrader-core (1:0.220.8) ...
Setting up update-manager-core (1:0.196.14) ...
Setting up ubuntu-release-upgrader-gtk (1:0.220.8) ...
Setting up update-manager (1:0.196.14) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get install fluxgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglade2-0 python-appindicator python-glade2 python-support
Suggested packages:
  python-gtk2-doc
The following NEW packages will be installed
  fluxgui libglade2-0 python-appindicator python-glade2 python-support
0 to upgrade, 5 to newly install, 0 to remove and 3 not to upgrade.
Need to get 432 kB of archives.
After this operation, 1,245 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/kilian/f.lux/ubuntu/ trusty/main fluxgui all 1.1.8 [345 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libglade2-0 amd64 1:2.6.4-2 [44.6 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe python-support all 1.0.15 [26.7 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python-appindicator amd64 12.10.1+13.10.20130920-0ubuntu4.1 [7,694 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty/main python-glade2 amd64 2.24.0-3ubuntu3 [8,744 B]
Fetched 432 kB in 0s (686 kB/s)          
Selecting previously unselected package libglade2-0:amd64.
(Reading database ... 371052 files and directories currently installed.)
Preparing to unpack .../libglade2-0_1%3a2.6.4-2_amd64.deb ...
Unpacking libglade2-0:amd64 (1:2.6.4-2) ...
Selecting previously unselected package python-support.
Preparing to unpack .../python-support_1.0.15_all.deb ...
Unpacking python-support (1.0.15) ...
Selecting previously unselected package python-appindicator.
Preparing to unpack .../python-appindicator_12.10.1+13.10.20130920-0ubuntu4.1_amd64.deb ...
Unpacking python-appindicator (12.10.1+13.10.20130920-0ubuntu4.1) ...
Selecting previously unselected package python-glade2.
Preparing to unpack .../python-glade2_2.24.0-3ubuntu3_amd64.deb ...
Unpacking python-glade2 (2.24.0-3ubuntu3) ...
Selecting previously unselected package fluxgui.
Preparing to unpack .../archives/fluxgui_1.1.8_all.deb ...
Unpacking fluxgui (1.1.8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up libglade2-0:amd64 (1:2.6.4-2) ...
Setting up python-support (1.0.15) ...
Setting up python-appindicator (12.10.1+13.10.20130920-0ubuntu4.1) ...
Setting up python-glade2 (2.24.0-3ubuntu3) ...
Setting up fluxgui (1.1.8) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for python-support (1.0.15) ...
hugh@SONY-VAIO-UBUNTU:~$
``` 

I noticed a warning in the above output.....

```
(gtk-update-icon-cache-3.0:5105): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
```

I tried to run the above command but message stats permission denied....
```
hugh@SONY-VAIO-UBUNTU:~$ gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
hugh@SONY-VAIO-UBUNTU:~$ 
```
 I also tried using sudo but same result.

I checked my version of flash again...

Flash Player version for Linux should be 11.2.202.540
my installed version of Flash is now       11.2.202.535 

.... it was 521 so it has had an update but not the latest.  But I am still unable to play video in YouTube.

Is there any other way to update flash?

---

### Post by Dennis N on 2015-10-17
Some information:

Linux Mint 17.2 uses adobe-flashplugin, and not flashplugin-installer.

Output from Mint 17.2 after all updates - this is the current version of adobe-flashplugin, released(?) Oct 13:
```
dmn@Roxanne ~ $ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 1:20151013.1-0trusty1
  Candidate: 1:20151013.1-0trusty1
  Version table:
 *** 1:20151013.1-0trusty1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
        100 /var/lib/dpkg/status

```
and pepperflashplugin-nonfree is now deprecated, if this announcement is correct:
[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

**adobe-flashplugin** installs **both** types of flash player in one package: Firefox compatable and Chromium compatatable:

My installed packages:
```
dmn@Roxanne /usr/lib/adobe-flashplugin $ ls -l
total 35960
-rw-r--r-- 1 root root 19269024 Sep 29 19:13 libflashplayer.so
-rw-r--r-- 1 root root 17547520 Sep 26 18:22 libpepflashplayer.so

```

I hope that clears up any confusion.

---

### Post by parker-hugh on 2015-10-17
> **Dennis N said:**
> Some information:

Linux Mint 17.2 uses adobe-flashplugin, and not flashplugin-installer.

Output from Mint 17.2 after all updates - this is the current version of adobe-flashplugin, released(?) Oct 13:
```
dmn@Roxanne ~ $ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 1:20151013.1-0trusty1
  Candidate: 1:20151013.1-0trusty1
  Version table:
 *** 1:20151013.1-0trusty1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
        100 /var/lib/dpkg/status

```
and pepperflashplugin-nonfree is now deprecated, if this announcement is correct:
[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

**adobe-flashplugin** installs **both** types of flash player in one package: Firefox compatable and Chromium compatatable:

My installed packages:
```
dmn@Roxanne /usr/lib/adobe-flashplugin $ ls -l
total 35960
-rw-r--r-- 1 root root 19269024 Sep 29 19:13 libflashplayer.so
-rw-r--r-- 1 root root 17547520 Sep 26 18:22 libpepflashplayer.so

```

I hope that clears up any confusion.
Thanks for the reply, ran the following commands....

```
hugh@SONY-VAIO-UBUNTU:~$ sudo apt-get install adobe-flashplugin
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
hugh@SONY-VAIO-UBUNTU:~$
``` 
message states adobe-flashplugin is already the newest version. but I don't seem to have the latest version when I check using [http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

Flash Player version for Linux should be  11.2.202.540
my installed version of Flash is still only 11.2.202.535

I also ran the same commands as you indicated in your post....
```
hugh@SONY-VAIO-UBUNTU:~$ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 1:20151013.1-0trusty1
  Candidate: 1:20151013.1-0trusty1
  Version table:
 *** 1:20151013.1-0trusty1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
        100 /var/lib/dpkg/status
hugh@SONY-VAIO-UBUNTU:~$
```

```
hugh@SONY-VAIO-UBUNTU:~$ /usr/lib/adobe-flashplugin $ ls -l
bash: /usr/lib/adobe-flashplugin: Is a directory
hugh@SONY-VAIO-UBUNTU:~$
``` 
the last command didn't seem to work as expected, any help would be appreciated.

---

### Post by Dennis N on 2015-10-17
You are working from your home directory. Change your working directory to **/usr/lib/adobe-flashplugin** before you try to list.

OR: from your home directory, you could also do:

```
dmn@Alexa:~$ ls -l /usr/lib/adobe-flashplugin
total 31144
-rw-r--r-- 1 root root 17467428 Sep 29 16:50 libflashplayer.so
-rw-r--r-- 1 root root 14420364 Sep 26 18:30 libpepflashplayer.so

```

---

### Post by Dennis N on 2015-10-17
> Flash Player version for Linux should be 11.2.202.540
my installed version of Flash is still only 11.2.202.535

We don't have the newest versions yet. The Firefox flash version in the package is: 11,2,202-535 and Chromium flash is 19,0,0-207 The packaging and testing is undoubtedly in progress, and it is a weekend. Wait a few days and a new one should come.

---

### Post by Dennis N on 2015-10-19
@parker-hugh;

**adobe-flashplugin** package was updated, and received today the 19th. New trusty version is **1:20151016.2-0trusty1**
Provides Chromium-compatible flash version 19,0,0,226 and Firefox-compatible version 11,2,202,540 in one package. Tested, and the plugins were recognized in each browser without any additional steps needed.

---

### Post by parker-hugh on 2015-10-21
> **Dennis N said:**
> You are working from your home directory. Change your working directory to **/usr/lib/adobe-flashplugin** before you try to list.

OR: from your home directory, you could also do:

```
dmn@Alexa:~$ ls -l /usr/lib/adobe-flashplugin
total 31144
-rw-r--r-- 1 root root 17467428 Sep 29 16:50 libflashplayer.so
-rw-r--r-- 1 root root 14420364 Sep 26 18:30 libpepflashplayer.so

```
thanks for reply, I entered the command as suggested and it seems to have worked ok....
```
hugh@DELL-VOSTRO-MINT ~ $ ls -l /usr/lib/adobe-flashplugin 
total 35960 
-rw-r--r-- 1 root root 19269024 Oct 15 03:53 libflashplayer.so 
-rw-r--r-- 1 root root 17547520 Oct 15 06:17 libpepflashplayer.so 
hugh@DELL-VOSTRO-MINT ~ $
``` 
Thanks for your help

---

### Post by parker-hugh on 2015-10-21
> **Dennis N said:**
> @parker-hugh;

**adobe-flashplugin** package was updated, and received today the 19th. New trusty version is **1:20151016.2-0trusty1**
Provides Chromium-compatible flash version 19,0,0,226 and Firefox-compatible version 11,2,202,540 in one package. Tested, and the plugins were recognized in each browser without any additional steps needed.
Thanks for reply, I ran an update via Update Manager and I now have the latest version ....
```
http://www.adobe.com/uk/software/flash/about/    You have version  11,2,202,540 installed 
Linux     Mozilla, Firefox - NPAPI (Extended Support Release)      11.2.202.540
```
I can now play video in YouTube. There are just a few that the video doesn't display (only sound) not sure if the video format is incorrect, but this only happen rarely.
 Thanks for your help.

---

### Post by parker-hugh on 2015-10-21
going forward, will I ever need to run "sudo apt-get install flashplugin-nonfree" because I still get the same error message, see below....

```
hugh@DELL-VOSTRO-MINT ~ $ sudo apt-get install flashplugin-nonfree
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is a virtual package provided by:
  adobe-flashplugin 1:20151016.2-0trusty1
  flashplugin-installer:i386 11.2.202.540ubuntu0.14.04.2
  flashplugin-installer 11.2.202.540ubuntu0.14.04.2
You should explicitly select one to install.

E: Package 'flashplugin-nonfree' has no installation candidate
hugh@DELL-VOSTRO-MINT ~ $ 
```
I just wondered if this error is because Firefox no longer supports flash.

---

