---
title: "[SOLVED] xserver-xorg-video-all, still broken package?"
date: 2008-12-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-20
I would like to know if the xserver-xorg-video-all and xserver-xorg-video-ati packages are still broken. This is what I am getting if I try a dist-upgrade: ```
Initializing package states... Done
The following packages are BROKEN:
  xserver-xorg-video-all xserver-xorg-video-ati 
The following packages will be REMOVED:
  xserver-xorg-video-apm{a} xserver-xorg-video-ark{a} xserver-xorg-video-fbdev{a} 
  xserver-xorg-video-mach64{a} xserver-xorg-video-mga{a} xserver-xorg-video-nsc{a} xserver-xorg-video-nv{a} 
  xserver-xorg-video-openchrome{a} xserver-xorg-video-r128{a} xserver-xorg-video-radeonhd{a} 
  xserver-xorg-video-rendition{a} xserver-xorg-video-s3{a} xserver-xorg-video-s3virge{a} 
  xserver-xorg-video-siliconmotion{a} xserver-xorg-video-sis{a} xserver-xorg-video-tdfx{a} 
  xserver-xorg-video-tga{a} xserver-xorg-video-trident{a} xserver-xorg-video-v4l{a} 
  xserver-xorg-video-vesa{a} 
The following packages will be upgraded:
  kdelibs-bin kdelibs5 kdelibs5-data xserver-xorg xserver-xorg-core xserver-xorg-core-dbg 
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics 
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel 
  xserver-xorg-video-intel-dbg xserver-xorg-video-neomagic xserver-xorg-video-radeon 
  xserver-xorg-video-savage xserver-xorg-video-sisusb xserver-xorg-video-tseng xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo 
27 packages upgraded, 0 newly installed, 20 to remove and 0 not upgraded.
Need to get 12.0MB/26.4MB of archives. After unpacking 9789kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-apm but it is not installable
                          Depends: xserver-xorg-video-ark but it is not installable
                          Depends: xserver-xorg-video-fbdev but it is not installable
                          Depends: xserver-xorg-video-mga but it is not installable
                          Depends: xserver-xorg-video-nv but it is not installable
                          Depends: xserver-xorg-video-rendition but it is not installable
                          Depends: xserver-xorg-video-s3 but it is not installable
                          Depends: xserver-xorg-video-s3virge but it is not installable
                          Depends: xserver-xorg-video-siliconmotion but it is not installable
                          Depends: xserver-xorg-video-sis but it is not installable
                          Depends: xserver-xorg-video-tdfx but it is not installable
                          Depends: xserver-xorg-video-trident but it is not installable
                          Depends: xserver-xorg-video-vesa but it is not installable
                          Depends: xserver-xorg-video-openchrome but it is not installable
                          Depends: xserver-xorg-video-v4l but it is not installable
  xserver-xorg-video-ati: Depends: xserver-xorg-video-r128 but it is not installable
                          Depends: xserver-xorg-video-mach64 but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
xserver-xorg-video-all
xserver-xorg-video-ati

Score is 188

```
I would like to think that I should not go through with that update as I don't see a replacement for xserver-xorg-video-all.

---

### Post by danf_1979 on 2008-12-20
I did it a nothing wrong happened. From aptitude's log:

```

===============================================================================
[REMOVE, DEPENDENCIES] xserver-xorg-video-all
[REMOVE, DEPENDENCIES] xserver-xorg-video-apm
[REMOVE, DEPENDENCIES] xserver-xorg-video-ark
[REMOVE, DEPENDENCIES] xserver-xorg-video-ati
[REMOVE, DEPENDENCIES] xserver-xorg-video-fbdev
[REMOVE, DEPENDENCIES] xserver-xorg-video-mach64
[REMOVE, DEPENDENCIES] xserver-xorg-video-mga
[REMOVE, DEPENDENCIES] xserver-xorg-video-nsc
[REMOVE, DEPENDENCIES] xserver-xorg-video-nv
[REMOVE, DEPENDENCIES] xserver-xorg-video-openchrome
[REMOVE, DEPENDENCIES] xserver-xorg-video-r128
[REMOVE, DEPENDENCIES] xserver-xorg-video-radeonhd
[REMOVE, DEPENDENCIES] xserver-xorg-video-rendition
[REMOVE, DEPENDENCIES] xserver-xorg-video-s3
[REMOVE, DEPENDENCIES] xserver-xorg-video-s3virge
[REMOVE, DEPENDENCIES] xserver-xorg-video-siliconmotion
[REMOVE, DEPENDENCIES] xserver-xorg-video-sis
[REMOVE, DEPENDENCIES] xserver-xorg-video-tdfx
[REMOVE, DEPENDENCIES] xserver-xorg-video-tga
[REMOVE, DEPENDENCIES] xserver-xorg-video-trident
[REMOVE, DEPENDENCIES] xserver-xorg-video-v4l
[REMOVE, DEPENDENCIES] xserver-xorg-video-vesa
[UPGRADE] xserver-xorg 1:7.4~5ubuntu5 -> 1:7.4~5ubuntu7
[UPGRADE] xserver-xorg-core 2:1.5.3-1ubuntu1 -> 2:1.5.99.3-0ubuntu3
[UPGRADE] xserver-xorg-input-evdev 1:2.1.0-0ubuntu1 -> 1:2.1.0-0ubuntu2
[UPGRADE] xserver-xorg-input-kbd 1:1.3.1-1ubuntu2 -> 1:1.3.1-2ubuntu1
[UPGRADE] xserver-xorg-input-mouse 1:1.3.0-2 -> 1:1.3.0-2ubuntu1
[UPGRADE] xserver-xorg-input-synaptics 0.15.2-0ubuntu7 -> 0.15.2-0ubuntu8
[UPGRADE] xserver-xorg-input-vmmouse 1:12.5.1-4ubuntu1 -> 1:12.5.1-4ubuntu3
[UPGRADE] xserver-xorg-input-wacom 1:0.8.1.4-0ubuntu3 -> 1:0.8.1.6-1ubuntu1
[UPGRADE] xserver-xorg-video-chips 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
[UPGRADE] xserver-xorg-video-cirrus 1:1.2.1-1build2 -> 1:1.2.1-1build3
[UPGRADE] xserver-xorg-video-geode 2.10.1-5 -> 2.11.0-1
[UPGRADE] xserver-xorg-video-i128 1:1.3.1-1 -> 1:1.3.1-1build1
[UPGRADE] xserver-xorg-video-i740 1:1.2.0-1build2 -> 1:1.2.0-1build3
[UPGRADE] xserver-xorg-video-intel 2:2.5.1-1ubuntu5 -> 2:2.5.1-1ubuntu6
[UPGRADE] xserver-xorg-video-neomagic 1:1.2.1-1build2 -> 1:1.2.1-1ubuntu1
[UPGRADE] xserver-xorg-video-radeon 1:6.9.0+git20081003.f9826a56-0ubuntu4 -> 1:6.9.0+git20081003.f9826a56-0ubuntu5
[UPGRADE] xserver-xorg-video-savage 1:2.2.1-3 -> 1:2.2.1-3build1
[UPGRADE] xserver-xorg-video-sisusb 1:0.9.0-1build2 -> 1:0.9.0-1ubuntu1
[UPGRADE] xserver-xorg-video-tseng 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
[UPGRADE] xserver-xorg-video-vmware 1:10.16.5-1 -> 1:10.16.5-1build1
[UPGRADE] xserver-xorg-video-voodoo 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
===============================================================================

```

I'm still alive :guitar:

---

### Post by danf_1979 on 2008-12-20
xserver-xorg-video-all is just a metapackage. Just read its description :)

```

xserver-xorg-driver-all
Description: the X.Org X server -- output driver metapackage
 This package depends on the full suite of output drivers for the X.Org X server (Xorg).  It does not provide any drivers itself, and may be removed if you wish to only have certain drivers installed.

```

---

### Post by DougieFresh4U on 2008-12-20
I am using 'vesa' as intel has been 'borked' for some time.
I have the 'Intel865G' graphics. If I go through with the 'dist-upgrade' it wants to remove 'vesa', therefore leaving me with a broken x, am I correct in assuming that?

---

### Post by danf_1979 on 2008-12-20
Hi again! I checked about vesa and I had it uninstalled, but I had no problems installing it now:

```

$ sudo aptitude install xserver-xorg-video-vesa
[sudo] password for daniel:                                   
Reading package lists... Done                                 
Building dependency tree                                      
Reading state information... Done                             
Reading extended state information                            
Initializing package states... Done                           
The following NEW packages will be installed:                 
  xserver-xorg-video-vesa                                     
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23,9kB of archives. After unpacking 102kB will be used.    
Writing extended state information... Done                             
Get:1 http://archive.ubuntu.com jaunty/main xserver-xorg-video-vesa 1:2.0.0-1ubuntu5 [23,9kB]
Fetched 23,9kB in 1s (20,5kB/s)
Selecting previously deselected package xserver-xorg-video-vesa.
(Reading database ... 194925 files and directories currently installed.)
Unpacking xserver-xorg-video-vesa (from .../xserver-xorg-video-vesa_1%3a2.0.0-1ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-vesa (1:2.0.0-1ubuntu5) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

```

Also, there is a warning for intel video users in here: [http://www.ubuntu.com/testing/jaunty/alpha2](http://www.ubuntu.com/testing/jaunty/alpha2), better read that.

---

### Post by DougieFresh4U on 2008-12-20
> **danf_1979 said:**
> Also, there is a warning for intel video users in here: [http://www.ubuntu.com/testing/jaunty/alpha2](http://www.ubuntu.com/testing/jaunty/alpha2), better read that.

Thanks for the info.
Yes, I have been aware of that bug, as I have submitted to it. That is why I have held off on doing that dist-upgrade. Using the 'vesa' for now works ok. I just wish the Intel mess would get fixed. In the mean time I shall leave as is.

---

### Post by danf_1979 on 2008-12-20
Hi again, just posting to let you know I had no problems installing xserver-xorg-video-all again, its not broken here anymore.

---

### Post by DougieFresh4U on 2008-12-20
> **danf_1979 said:**
> Hi again, just posting to let you know I had no problems installing xserver-xorg-video-all again, its not broken here anymore.

Thanks danf_1979
I am gonna hold off till this Intel mess is cleared up

---

