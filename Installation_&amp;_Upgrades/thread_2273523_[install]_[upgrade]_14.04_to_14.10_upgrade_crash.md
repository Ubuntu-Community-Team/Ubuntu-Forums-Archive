---
title: "[install] [upgrade] 14.04 to 14.10 upgrade crash"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by allaf on 2015-04-13
Hello,

Just wanted to upgrade from trusty 14.04 to 14.10 to try it out, bad idea.
I launched kubuntu-devel-release-upgrade, everything went fine until it stop a one of the last step with a popup telling me there was errors installing some packages and i should do a dpkg --configure -a.

When i launch dpkg --configure -a it fails :
```

Setting up keyboard-configuration (1.70ubuntu9) ...
git: 'LC_CTYPE=en_US.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-wacom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-qxl:
 xserver-xorg-video-qxl depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-qxl depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-qxl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.15.0.901); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.

dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-r128:
 xserver-xorg-video-r128 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-r128 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-r128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-modesetting:
 xserver-xorg-video-modesetting depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-modesetting depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-modesetting (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
 xserver-xorg-video-mga depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-trident (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mach64:
 xserver-xorg-video-mach64 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mach64 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mach64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics; however:
  Package xserver-xorg-input-synaptics is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-wacom; however:
  Package xserver-xorg-input-wacom is not configured yet.

dpkg: error processing package xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-331-updates:
 nvidia-331-updates depends on xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19; however:
  Package xorg-video-abi-11 is not installed.
  Package xorg-video-abi-12 is not installed.
  Package xorg-video-abi-13 is not installed.
  Package xorg-video-abi-14 is not installed.
  Package xorg-video-abi-15 is not installed.
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
  Package xorg-video-abi-19 is not installed.
 nvidia-331-updates depends on xserver-xorg-core; however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package nvidia-331-updates (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-r128; however:
  Package xserver-xorg-video-r128 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-mach64; however:
  Package xserver-xorg-video-mach64 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.

dpkg: error processing package xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-siliconmotion:
 xserver-xorg-video-siliconmotion depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-siliconmotion depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-siliconmotion (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-input-mouse; however:
  Package xserver-xorg-input-mouse is not configured yet.

dpkg: error processing package xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.7+7ubuntu2); however:
  Package xserver-xorg is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-331-updates-uvm:
 nvidia-331-updates-uvm depends on nvidia-331-updates (>= 331.113); however:
  Package nvidia-331-updates is not configured yet.

dpkg: error processing package nvidia-331-updates-uvm (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 xserver-xorg-core
 xserver-xorg-video-openchrome
 xserver-xorg-video-vmware
 xserver-xorg-input-wacom
 xserver-xorg-video-radeon
 xserver-xorg-video-qxl
 xserver-xorg-video-savage
 xserver-xorg-video-fbdev
 xserver-xorg-input-evdev
 xserver-xorg
 console-setup
 xserver-xorg-input-synaptics
 xserver-xorg-video-vesa
 xserver-xorg-video-sisusb
 xserver-xorg-video-tdfx
 xserver-xorg-video-cirrus
 xserver-xorg-video-r128
 xserver-xorg-video-neomagic
 xserver-xorg-video-modesetting
 xserver-xorg-video-mga
 xserver-xorg-video-s3
 xserver-xorg-video-trident
 xserver-xorg-video-intel
 xserver-xorg-video-mach64
 xserver-xorg-input-all
 xserver-xorg-input-mouse
 nvidia-331-updates
 ubuntu-minimal
 xserver-xorg-video-ati
 xserver-xorg-video-siliconmotion
 xserver-xorg-input-vmmouse
 xorg
 kubuntu-desktop
 nvidia-331-updates-uvm


```


How can I fix this ?

Also is it possible to cancel the upgrade and stay safely on 14.04 ?

Thanks.

---

### Post by grahammechanical on 2015-04-13
14.10 is a stable release not a development release. Therefore. devel-release-upgrade must surely be the wrong command to use. Have you tried

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
```

Regards.

---

### Post by allaf on 2015-04-14
> **grahammechanical said:**
> 14.10 is a stable release not a development release. Therefore. devel-release-upgrade must surely be the wrong command to use. Have you tried

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
```

Regards.

I tried that already, gives me the exact same error.
Can't give you the trace right now (i will later) but it's basically the same.

---

### Post by allaf on 2015-04-14
> **allaf said:**
> I tried that already, gives me the exact same error.
Can't give you the trace right now (i will later) but it's basically the same.

```

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libxext-dev libxext6 libxext6:i386 libxrender-dev libxrender1 libxrender1:i386 linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic linux-headers-3.16.0-34 linux-headers-3.16.0-34-generic linux-image-3.13.0-49-generic
  linux-image-3.16.0-34-generic linux-image-extra-3.13.0-49-generic linux-image-extra-3.16.0-34-generic
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
Need to get 125 MB of archives.
After this operation, 1 777 kB disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxext-dev amd64 2:1.3.2-1ubuntu0.0.14.04.1 [81,2 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxext6 i386 2:1.3.2-1ubuntu0.0.14.04.1 [28,5 kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxext6 amd64 2:1.3.2-1ubuntu0.0.14.04.1 [28,8 kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrender-dev amd64 1:0.9.8-1build0.14.04.1 [23,8 kB]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrender1 i386 1:0.9.8-1build0.14.04.1 [17,5 kB]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrender1 amd64 1:0.9.8-1build0.14.04.1 [17,9 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-49-generic amd64 3.13.0-49.83 [15,1 MB]
Get:8 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.16.0-34-generic amd64 3.16.0-34.47~14.04.1 [16,2 MB]                                                                                                                 
Get:9 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-49 all 3.13.0-49.83 [8 878 kB]                                                                                                                                
Get:10 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-49-generic amd64 3.13.0-49.83 [699 kB]                                                                                                                       
Get:11 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-34 all 3.16.0-34.47~14.04.1 [9 076 kB]                                                                                                                       
Get:12 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-34-generic amd64 3.16.0-34.47~14.04.1 [728 kB]                                                                                                               
Get:13 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-49-generic amd64 3.13.0-49.83 [36,8 MB]                                                                                                                  
Get:14 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.16.0-34-generic amd64 3.16.0-34.47~14.04.1 [37,7 MB]                                                                                                          
Fetched 125 MB in 1min 30s (1 390 kB/s)                                                                                                                                                                                                           
(Reading database ... 218646 files and directories currently installed.)
Preparing to unpack .../libxext-dev_2%3a1.3.2-1ubuntu0.0.14.04.1_amd64.deb ...
Unpacking libxext-dev:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) over (2:1.3.2-1) ...
Preparing to unpack .../libxext6_2%3a1.3.2-1ubuntu0.0.14.04.1_amd64.deb ...
De-configuring libxext6:i386 (2:1.3.2-1) ...
Unpacking libxext6:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) over (2:1.3.2-1) ...
Preparing to unpack .../libxext6_2%3a1.3.2-1ubuntu0.0.14.04.1_i386.deb ...
Unpacking libxext6:i386 (2:1.3.2-1ubuntu0.0.14.04.1) over (2:1.3.2-1) ...
Preparing to unpack .../libxrender-dev_1%3a0.9.8-1build0.14.04.1_amd64.deb ...
Unpacking libxrender-dev:amd64 (1:0.9.8-1build0.14.04.1) over (1:0.9.8-1) ...
Preparing to unpack .../libxrender1_1%3a0.9.8-1build0.14.04.1_amd64.deb ...
De-configuring libxrender1:i386 (1:0.9.8-1) ...
Unpacking libxrender1:amd64 (1:0.9.8-1build0.14.04.1) over (1:0.9.8-1) ...
Preparing to unpack .../libxrender1_1%3a0.9.8-1build0.14.04.1_i386.deb ...
Unpacking libxrender1:i386 (1:0.9.8-1build0.14.04.1) over (1:0.9.8-1) ...
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Preparing to unpack .../linux-image-3.16.0-34-generic_3.16.0-34.47~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-34-generic (3.16.0-34.47~14.04.1) over (3.16.0-34.45) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Preparing to unpack .../linux-headers-3.13.0-49_3.13.0-49.83_all.deb ...
Unpacking linux-headers-3.13.0-49 (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../linux-headers-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Unpacking linux-headers-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../linux-headers-3.16.0-34_3.16.0-34.47~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-34 (3.16.0-34.47~14.04.1) over (3.16.0-34.45) ...
Preparing to unpack .../linux-headers-3.16.0-34-generic_3.16.0-34.47~14.04.1_amd64.deb ...
Unpacking linux-headers-3.16.0-34-generic (3.16.0-34.47~14.04.1) over (3.16.0-34.45) ...
Preparing to unpack .../linux-image-extra-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Unpacking linux-image-extra-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../linux-image-extra-3.16.0-34-generic_3.16.0-34.47~14.04.1_amd64.deb ...
Unpacking linux-image-extra-3.16.0-34-generic (3.16.0-34.47~14.04.1) over (3.16.0-34.45) ...
Processing triggers for man-db (2.7.0.2-2) ...
Setting up keyboard-configuration (1.70ubuntu9) ...
git: 'LC_CTYPE=en_US.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-siliconmotion:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
                                                                                             No apport report written because MaxReports is reached already
                                                                                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                                                                                         No apport report written because MaxReports is reached already

                                      Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-siliconmotion depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-siliconmotion (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-r128:
 xserver-xorg-video-r128 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-r128 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-r128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mach64:
 xserver-xorNo apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                                                                      g-video-mach64 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mach64 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mach64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuraNo apport report written because MaxReports is reached already
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
                                                                                                                                                                                                                                               tion of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-r128; however:
  Package xserver-xorg-video-r128 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-mach64; however:
  Package xserver-xorg-video-mach64 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.

dpkg: error processing package xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
Setting up libxext6:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Setting up libxext6:i386 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Setting up libxext-dev:amd64 (2:No apport report written because MaxReports is reached already
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
                                               1.3.2-1ubuntu0.0.14.04.1) ...
dpkg: dependency problems prevent configuration of nvidia-331-updates:
 nvidia-331-updates depends on xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19; however:
  Package xorg-video-abi-11 is not installed.
  Package xorg-video-abi-12 is not installed.
  Package xorg-video-abi-13 is not installed.
  Package xorg-video-abi-14 is not installed.
  Package xorg-video-abi-15 is not installed.
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
  Package xorg-video-abi-19 is not installed.
 nvidia-331-updates depends on xserver-xorg-core; however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package nvidia-331-updates (--configure):
 dependency problems - leaving unconfigured
Setting up libxrender1:amd64 (1:0.9.8-1build0.14.04.1) ...
Setting up libxrender1:i386 (1:0.9.8-1builNo apport report written because MaxReports is reached already
                                                                                                        d0.14.04.1) ...
Setting up libxrender-dev:amd64 (1:0.9.8-1build0.14.04.1) ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-trident (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
 xserver-xorg-video-mga depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-modesetting:
 xserver-xorg-video-modesetting depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-modesetting depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-modesetting (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-qxl:
 xserver-xorg-video-qxl depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-qxl depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-qxl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-input-mouse; however:
  Package xserver-xorg-input-mouse is not configured yet.

dpkg: error processing package xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-wacom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-vmmouse; however:
  Package xserver-xorg-input-vmmouse is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics; however:
  Package xserver-xorg-input-synaptics is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-wacom; however:
  Package xserver-xorg-input-wacom is not configured yet.

dpkg: error processing package xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.15.0.901); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg depends on xserver-xorg-video-all | xorg-driver-video; however:
  Package xserver-xorg-video-all is not installed.
  Package xorg-driver-video is not installed.
  Package xserver-xorg-video-siliconmotion which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-ati which provides xorg-driver-video is not configured yet.
  Package nvidia-331-updates which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-mach64 which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-intel which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-trident which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-s3 which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-m
dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.7+7ubuntu2); however:
  Package xserver-xorg is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-331-updates-uvm:
 nvidia-331-updates-uvm depends on nvidia-331-updates (>= 331.113); however:
  Package nvidia-331-updates is not configured yet.

dpkg: error processing package nvidia-331-updates-uvm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-49.81 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-49.81 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-headers-3.13.0-49 (3.13.0-49.83) ...
Setting up linux-headers-3.13.0-49-generic (3.13.0-49.83) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Setting up linux-headers-3.16.0-34 (3.16.0-34.47~14.04.1) ...
Setting up linux-headers-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Setting up linux-image-extra-3.13.0-49-generic (3.13.0-49.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-extra-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Errors were encountered while processing:
 keyboard-configuration
 console-setup
 xserver-xorg-core
 xserver-xorg-video-siliconmotion
 xserver-xorg-video-r128
 xserver-xorg-video-mach64
 xserver-xorg-video-radeon
 xserver-xorg-video-ati
 nvidia-331-updates
 xserver-xorg-video-intel
 xserver-xorg-video-trident
 xserver-xorg-video-s3
 xserver-xorg-video-mga
 xserver-xorg-video-modesetting
 xserver-xorg-video-neomagic
 xserver-xorg-video-cirrus
 xserver-xorg-video-tdfx
 xserver-xorg-video-sisusb
 xserver-xorg-video-vesa
 xserver-xorg-video-fbdev
 xserver-xorg-video-savage
 xserver-xorg-video-qxl
 xserver-xorg-video-vmware
 xserver-xorg-video-openchrome
 xserver-xorg-input-evdev
 xserver-xorg-input-mouse
 xserver-xorg-input-vmmouse
 xserver-xorg-input-synaptics
 xserver-xorg-input-wacom
 xserver-xorg-input-all
 xserver-xorg
 xorg
 kubuntu-desktop
 nvidia-331-updates-uvm
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by allaf on 2015-04-18
It looks like the  keyboard-configuration package is the problem, how can fix this ?


```
Setting up keyboard-configuration (1.70ubuntu9) ...
git: 'LC_CTYPE=en_US.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.
```

---

