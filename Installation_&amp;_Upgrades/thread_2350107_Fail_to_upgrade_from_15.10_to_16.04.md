---
title: "Fail to upgrade from 15.10 to 16.04"
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by francois_baret on 2017-01-21
Whatever I am trying to install with apt-get I get an error:
```
systemd : Depends: libsystemd0 (= 225-1ubuntu9.1) but 229-4ubuntu4 is to be installed
 xserver-xorg-core : Breaks: systemd (< 226-4~)
                     Breaks: systemd:i386 (< 226-4~)


```
cat gives me:
```
francois@Andalous:~$ cat /etc/issue
Ubuntu 16.04.1 LTS \n \l


```
uname:
```
francois@Andalous:~$ uname -r
3.16.0-38-generic


```
cat -n /etc/apt/sources.list:
```
francois@Andalous:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ma.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://ma.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://ma.archive.ubuntu.com/ubuntu/ xenial universe
    17    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial universe
    18    deb http://ma.archive.ubuntu.com/ubuntu/ xenial-updates universe
    19    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://ma.archive.ubuntu.com/ubuntu/ xenial multiverse
    27    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial multiverse
    28    deb http://ma.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    29    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://ma.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    37    deb-src http://ma.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    41    deb http://security.ubuntu.com/ubuntu xenial-security universe
    42    deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    43    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu utopic partner
    51    # deb-src http://archive.canonical.com/ubuntu utopic partner
    52    
    53    # deb http://vontaene.de/raspbian-updates/ . main # disabled on upgrade to wily
    54    deb http://archive.canonical.com/ xenial partner
    55    # deb-src http://archive.canonical.com/ vivid partner
```
tail:
```
francois@Andalous:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/damien-moore-ubuntu-codeblocks-stable-wily.list <==
# deb http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu wily main

==> /etc/apt/sources.list.d/damien-moore-ubuntu-codeblocks-stable-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu wily main
# deb-src http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu wily main

==> /etc/apt/sources.list.d/freecad-maintainers-ubuntu-freecad-stable-wily.list <==
# deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu wily main

==> /etc/apt/sources.list.d/freecad-maintainers-ubuntu-freecad-stable-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu wily main
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu wily main

==> /etc/apt/sources.list.d/freecad-maintainers-ubuntu-freecad-stable-wily.list.save <==
deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu wily main
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu wily main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/gstreamer-developers-ubuntu-ppa-vivid.list <==
# deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/gstreamer-developers-ubuntu-ppa-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/gstreamer-developers-ubuntu-ppa-vivid.list.save <==
# deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/gstreamer-sdk.list <==
# deb http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64 ./


==> /etc/apt/sources.list.d/gstreamer-sdk.list.distUpgrade <==
# deb http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64 ./


==> /etc/apt/sources.list.d/gstreamer-sdk.list.save <==
# deb http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64 ./


==> /etc/apt/sources.list.d/ivideon.list <==
# deb http://packages.ivideon.com/ubuntu stable non-free # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/ivideon.list.distUpgrade <==
deb http://packages.ivideon.com/ubuntu stable non-free

==> /etc/apt/sources.list.d/ivideon.list.save <==
deb http://packages.ivideon.com/ubuntu stable non-free

==> /etc/apt/sources.list.d/jitsi-stable.list <==
# deb https://download.jitsi.org stable/ # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/jitsi-stable.list.distUpgrade <==
deb https://download.jitsi.org stable/

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-utopic.list <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu utopic main

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu utopic main

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-utopic.list.save <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu utopic main

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-vivid.list <==
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-vivid.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main

==> /etc/apt/sources.list.d/kirillshkrogalev-ubuntu-ffmpeg-next-vivid.list.save <==
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu vivid main

==> /etc/apt/sources.list.d/kurento.list <==
# deb http://ubuntu.kurento.org trusty kms6

==> /etc/apt/sources.list.d/kurento.list.distUpgrade <==
# deb http://ubuntu.kurento.org trusty kms6

==> /etc/apt/sources.list.d/kurento.list.save <==
# deb http://ubuntu.kurento.org trusty kms6

==> /etc/apt/sources.list.d/kurento-ubuntu-kurento-vivid.list <==
# deb http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main
# deb-src http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main

==> /etc/apt/sources.list.d/kurento-ubuntu-kurento-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main
# deb-src http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main

==> /etc/apt/sources.list.d/kurento-ubuntu-kurento-vivid.list.save <==
# deb http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main
# deb-src http://ppa.launchpad.net/kurento/kurento/ubuntu vivid main

==> /etc/apt/sources.list.d/nodesource.list <==
# deb https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid
# deb-src https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/nodesource.list.distUpgrade <==
# deb https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid
# deb-src https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/nodesource.list.save <==
# deb https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid
# deb-src https://deb.nodesource.com/node_0.10 vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-vivid.list <==
# deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-vivid.list.save <==
# deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu vivid main

==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-vivid.list <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main

==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main

==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-vivid.list.save <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main

==> /etc/apt/sources.list.d/ros-latest.list <==
# deb http://packages.ros.org/ros/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/ros-latest.list.distUpgrade <==
deb http://packages.ros.org/ros/ubuntu wily main


```
update:
```
francois@Andalous:~$ sudo apt update
Hit:1 http://archive.canonical.com xenial InRelease
Hit:2 http://ma.archive.ubuntu.com/ubuntu xenial InRelease                     
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://ma.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Get:7 http://ma.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Fetched 306 kB in 1s (200 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.


```
upgrade:
```
francois@Andalous:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ifupdown : Breaks: systemd (< 228-3~)
            Breaks: systemd:i386 (< 228-3~)
 initscripts : Breaks: systemd (< 228-5ubuntu3)
               Breaks: systemd:i386 (< 228-5ubuntu3)
 libpam-systemd : Depends: systemd (= 229-4ubuntu16)
 libsystemd0 : Breaks: libsystemd0:i386 (!= 229-4ubuntu4) but 229-4ubuntu16 is installed
 libsystemd0:i386 : Breaks: libsystemd0 (!= 229-4ubuntu16) but 229-4ubuntu4 is installed
 systemd : Depends: libsystemd0 (= 225-1ubuntu9.1) but 229-4ubuntu4 is installed
 xserver-xorg-core : Breaks: systemd (< 226-4~)
                     Breaks: systemd:i386 (< 226-4~)
E: Unmet dependencies. Try using -f.


```
What can I do to fix my system?

---

### Post by mörgæs on 2017-01-22
> **francois_baret said:**
> 
What can I do to fix my system?
In your last CODE section Ubuntu suggests something.

---

### Post by ian-weisser on 2017-01-22
Which method did you use to upgrade from 15.10 to 16.04?

---

