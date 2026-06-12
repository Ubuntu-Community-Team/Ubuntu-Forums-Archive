---
title: "dpkg installation issues"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by ToFue on 2011-08-24
Hullo, I upgrade to 11.04 and have errors while upgrading things:
```
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit

...and...

error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
```

I've tried a fix as suggested [**--> In This Thread <-- **](http://ubuntuforums.org/showthread.php?t=1772889&highlight=version+number+start+digit)  but, it does not fix the errors in my case. I've also tried using **apt-get** with **--fix-broken**, **--fix-missing**, and **--reinstall** and **clean** combinations, to no avail..

  Is there a solid fix for this, or should I just do a clean install to 11.10 (I've read that a lot of issues are resolved in that distro version)?  I'd hate to go through the trouble if there's a simpler way...

  Let me also state that the new kernel also won't install: 
```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic linux-headers-generic-pae
  linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```
Am I correct to assume that it's due to a versioning conflict of some sort as related to my other errors?

I also attempted to reinstall dpkg, git, and synaptic.. though I don't see synaptic being a cause. Here's the full output, with errors like all the rest: ```
~$ sudo apt-get install --reinstall dpkg git synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgwenhywfar60 libaqofxconnect7 libktoblzcheck1c2a libaqbanking33
  libaqbanking-plugins-libgwenhywfar60 libaqhbci19 aqbanking-tools
  libgwenhywfar-data libaqbanking-data libaqbanking33-plugins
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 4 not upgraded.
Need to get 6,747 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main dpkg i386 1.16.0~ubuntu7 [1,848 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main git i386 1:1.7.4.1-3 [4,184 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main synaptic i386 0.75.1ubuntu2 [715 kB]
Fetched 6,747 kB in 11s (582 kB/s)                                             
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 61863 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit
(Reading database ... 401566 files and directories currently installed.)
Preparing to replace dpkg 1.16.0~ubuntu7 (using .../dpkg_1.16.0~ubuntu7_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 61864 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit
Setting up dpkg (1.16.0~ubuntu7) ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 61863 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit
(Reading database ... 401566 files and directories currently installed.)
Preparing to replace git 1:1.7.4.1-3 (using .../git_1%3a1.7.4.1-3_i386.deb) ...
Unpacking replacement git ...
Preparing to replace synaptic 0.75.1ubuntu2 (using .../synaptic_0.75.1ubuntu2_i386.deb) ...
Unpacking replacement synaptic ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 61863 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit
Processing triggers for python-support ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 61865 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit
Setting up git (1:1.7.4.1-3) ...
Setting up synaptic (0.75.1ubuntu2) ...
Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 23662 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 61865 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit

```

Thanks for any assistance!

---

### Post by rob45 on 2011-08-24
Have you tried using update manager to run updates?

---

### Post by ToFue on 2011-08-25
Hi, thanks for the reply! 

This occurs in update manager and synaptic (where the terminal output screen shows the errors), as well as any cli invocation of dpkg or apt-get.

Always the same errors on any and all packages that are requested.

---

### Post by Hakunka-Matata on 2011-08-25
I see you have issued 'sudo apt-get upgrade, but I don't see where update command was run"

Have you updated and upgraded current repositories?

```
sudo apt-get update && sudo apt-get upgrade
```"What the Bleep do we know"  One of my favourites!

---

### Post by ToFue on 2011-08-26
hehe, great book! 
 
  I showed the output of **sudo apt-get upgrade** only to show the kernel packages that refuse to install.. I run ** sudo apt-get update** prior/between each and every other command step, but the errors don't show up there.. it's only when dpkg is (i suppose) checking for versioning info..

here's the output for the update check, if it helps:
```
~$ sudo apt-get update
[sudo] password for tofue: 
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.canonical.com natty Release.gpg                             
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Hit http://archive.ubuntu.com natty Release.gpg                                
Get:3 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:4 http://dl.google.com stable Release [1,338 B]                            
Hit http://archive.ubuntu.com natty Release                                    
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Get:5 http://security.ubuntu.com natty-security Release [31.4 kB]              
Get:6 http://dl.google.com stable/main i386 Packages [464 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://extras.ubuntu.com natty/main Sources                                
Get:7 http://security.ubuntu.com natty-security/restricted Sources [14 B]      
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:8 http://security.ubuntu.com natty-security/main Sources [65.0 kB]         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:9 http://security.ubuntu.com natty-security/multiverse Sources [655 B]     
Get:10 http://security.ubuntu.com natty-security/universe Sources [10.2 kB]    
Get:11 http://security.ubuntu.com natty-security/main i386 Packages [170 kB]   
Get:12 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Get:13 http://security.ubuntu.com natty-security/universe i386 Packages [34.5 kB]
Get:14 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,077 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Get:15 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Hit http://us.archive.ubuntu.com natty Release                                 
Get:16 http://us.archive.ubuntu.com natty-updates Release [31.4 kB]            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:17 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:18 http://us.archive.ubuntu.com natty-updates/main Sources [102 kB]        
Get:19 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,895 B] 
Get:20 http://us.archive.ubuntu.com natty-updates/universe Sources [23.2 kB]   
Get:21 http://us.archive.ubuntu.com natty-updates/main i386 Packages [307 kB]  
Get:22 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:23 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [85.6 kB]
Get:24 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [4,257 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 872 kB in 10s (86.2 kB/s)                                              
Reading package lists... Done

```

...and here's my repo list: 
```
:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse

```

If this issue isn't going to destroy my system in the long run, I suppose I can live with it for a while... 

  The errors began since .during. the distro upgrade from 10.10 to 11.04, part-way through the package installation phase, so now I question my system's integrity. It doesn't seem (at a glance) that installed packages are affected (binaries), but could there be issues for updates that have version registers stepping on older or wrong versions of whatever package (or whatever hidden issues)? I'm not sure how version integrity works nor of it's importance.. am I on track there?

 Again, thanks for your time and interest in my issue, rob45 and Hakunka-Matata!

---

### Post by garvinrick4 on 2011-08-26
Does Synaptic say you have any broken packages?
Can you fix packages if so in Synaptic?
You have run:
```
sudo dpkg --configure -a
``````
sudo apt-get -f install
```Just to check out, might work, might not.

If not look in  /var/lib/dpkg/status see what if it tells you why not installing certain packages. Can open in text editor, gedit, leafpad or even nano or vi
or just follow path and open in.

---

### Post by ToFue on 2011-08-28
Hi, thanks for the reply, garvinrick4, and sorry for my delay to get back to this!

  The fix-broken for apt-get doesn't seem to see anything and nothing's reported as broken; I used **sudo apt-get --fix-broken install** as well as the short switch (**sudo apt-get -f install**)to no avail. Output:
```
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It seems that the packages that I upgrade or install don't appear to be compromised in any way, though the references in the errors are in question.

the output for **sudo dpkg --configure -a** shows the errors (only) that I've been getting: ```
~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23768 package 'ffmpeg':
 error in Version string '5:git-N-55252-gcf74079-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 62027 package 'qt-faststart':
 error in Version string 'git-N-55252-gcf74079-1': version number does not start with digit

```

The status file (/var/lib/dpkg/status) yielded something interesting by filtering 'root@<machine-name>'. Three entries for packages that I'd forgotten that I self-compiled, two of which are packages complained about in the error: ```
Package: ffmpeg
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 79960
Maintainer: root@Ectonut
Architecture: i386
Version: 5:git-N-55252-gcf74079-1
Provides: ffmpeg
Conffiles:
 /etc/ffserver.conf 7e84402ab9129df85117336840b3d78f obsolete
Description: Package created with checkinstall 1.6.2

Package: qt-faststart
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 1720
Maintainer: root@Ectonut
Architecture: i386
Version: git-N-55252-gcf74079-1
Provides: qt-faststart
Description: Package created with checkinstall 1.6.2

Package: x264
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 2208
Maintainer: root@Ectonut
Architecture: i386
Version: 3:0.114.1913+git5fd3dce-1
Provides: x264
Description: Package created with checkinstall 1.6.2
```

So then that makes me think that I should recompile them and (re)install w/ dpkg? the older binaries should work fine, though I also wonder if the distro-upgrade installed the generic packages for those also..

Before I realized that I compiled those specifically, apt-get was refusing to **--reinstall**. ```
~$ sudo apt-get --reinstall install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of ffmpeg is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The status for gstreamer0.10-ffmpeg is listed as well: ```
Package: gstreamer0.10-ffmpeg
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 344
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.10.11-4
Depends: libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~), libavformat52 (>= 4:0.6-1~) | libavformat-extra-52 (>= 4:0.6-1~), libavutil50 (>= 4:0.6-1~) | libavutil-extra-50 (>= 4:0.6-1~), libc6 (>= 2.7), libglib2.0-0 (>= 2.24.0), libgstreamer-plugins-base0.10-0 (>= 0.10.22), libgstreamer0.10-0 (>= 0.10.26), liborc-0.4-0 (>= 1:0.4.10), libpostproc51 (>= 4:0.6-1~) | libpostproc-extra-51 (>= 4:0.6-1~), libswscale0 (>= 4:0.6-1~) | libswscale-extra-0 (>= 4:0.6-1~), libavcodec52 (<< 5:0) | libavcodec-extra-52 (<< 5:0)
Description: FFmpeg plugin for GStreamer
 This GStreamer plugin supports a large number of audio and video compression
 formats through the use of the FFmpeg library.  The plugin contains GStreamer
 elements for decoding 90+ formats (AVI, MPEG, OGG, Matroska, ASF, ...),
 demuxing 30+ formats and colorspace conversion.
```

...so I suspect that's the conflict, and it would seem I'll have to find out some how what packages are actually registered (i'm not sure where to go to do that). Do I need to uninstall, for instance, gstreamer0.10-ffmpeg and recompile the custom ffmpeg, or can they co-exist and to be rid of errors otherwise?

**note:** being that this is a distro-upgrade, the env variable **DIST_VERSION=Ubuntu 10.10 - The Maverick Meerkat** yet exists.. shouldn't it value with "11.04" and "Natty"? Also note that the update-manager found a new kernel revision yesterday and installed successfully; I no longer see them in any apt-* verbose

Thanks again for your time on my issue!

---

### Post by dino99 on 2011-08-28
propositions in a few steps:

sudo shutdown -r now
( will force fsck on next boot)

boot in recovery mode, then select "repair packages"

sudo dpkg-reconfigure -phigh -a
(wait it to end itself, can be long)

sudo reboot

---

