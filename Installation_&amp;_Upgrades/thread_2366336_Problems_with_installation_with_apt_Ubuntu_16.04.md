---
title: "Problems with installation with apt Ubuntu 16.04"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by yosoufe on 2017-07-16
Hi,

I guess few weeks ago, I did an update and upgrade with apt. After that apt gave error that it could not unlock something for installation. I searched somewhere and did some stuff to solve. I think some of them was probably wrong. I don't remember them exactly unfortunately. I remember I removed some folders. for example it was a folder called '13' inside a folder with many other folders with numbers,

I did as well ```
sudo dpkg --configure -a
```. but at first time it didn't work and it worked after some other stuff.

The main problem is NOW I cannot install some software using apt and I get errors about dependencies. I guess this is because of some wrong stuff I did during that time.

For example

```

sudo apt-get install doxygen
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 doxygen : Depends: libclang1-3.6 (>= 3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Or for qtcreator:
```

sudo apt-get install qtcreator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 qtcreator : Depends: libclang1-3.6 (>= 3.6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


Do you think it is something wrong about package manager or it is really dependecy problem?? how should I solve then the dependency problem??

---

### Post by oldos2er on 2017-07-16
You can try ```
sudo apt-get install -f
``` but don't be surprised if it doesn't work.

Can you run the following commands one at a time and copy/paste all the output here? ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/

sudo apt-get update
```

---

### Post by yosoufe on 2017-07-16
> **oldos2er said:**
> You can try ```
sudo apt-get install -f
``` but don't be surprised if it doesn't work.

Can you run the following commands one at a time and copy/paste all the output here? ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/

sudo apt-get update
```

Thanks. -f did not work. These are the result of the commands you asked:
```

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://archive.canonical.com/ xenial partner
# deb-src http://archive.canonical.com/ xenial partner

```


```

ll /etc/apt/sources.list.d/
total 176
drwxr-xr-x 2 root root 4096 Jun 30 00:25 ./
drwxr-xr-x 6 root root 4096 Apr  6 01:40 ../
-rw-r--r-- 1 root root   71 Jul 16 21:34 bazel.list
-rw-r--r-- 1 root root   71 Jul 16 21:34 bazel.list.save
-rw-r--r-- 1 root root  150 Jul 16 21:34 brousselle-ubuntu-slowmovideo-xenial.list
-rw-r--r-- 1 root root  150 Jul 16 21:34 brousselle-ubuntu-slowmovideo-xenial.list.save
-rw-r--r-- 1 root root  224 Jul 16 21:34 colingille-ubuntu-freshlight-xenial.list
-rw-r--r-- 1 root root  224 Jul 16 21:34 colingille-ubuntu-freshlight-xenial.list.save
-rw-r--r-- 1 root root   80 Jul 16 21:34 cuda.list
-rw-r--r-- 1 root root   80 Jul 16 21:34 cuda.list.save
-rw-r--r-- 1 root root   64 Jul 16 21:34 dropbox.list
-rw-r--r-- 1 root root   64 Jul 16 21:34 dropbox.list.save
-rw-r--r-- 1 root root  189 Jul 16 21:34 google-chrome.list
-rw-r--r-- 1 root root  189 Jul 16 21:34 google-chrome.list.save
-rw-r--r-- 1 root root  219 Jul 16 21:34 graphics-drivers-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root  219 Jul 16 21:34 graphics-drivers-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  172 Jul 16 21:34 maarten-baert-ubuntu-simplescreenrecorder-xenial.list
-rw-r--r-- 1 root root  172 Jul 16 21:34 maarten-baert-ubuntu-simplescreenrecorder-xenial.list.save
-rw-r--r-- 1 root root  130 Jul 16 21:34 octave-ubuntu-stable-xenial.list
-rw-r--r-- 1 root root  130 Jul 16 21:34 octave-ubuntu-stable-xenial.list.save
-rw-r--r-- 1 root root    0 Mär 27 23:57 osd-lyrics-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root    0 Mär 27 23:57 osd-lyrics-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  152 Jul 16 21:34 plushuang-tw-ubuntu-uget-stable-xenial.list
-rw-r--r-- 1 root root  152 Jul 16 21:34 plushuang-tw-ubuntu-uget-stable-xenial.list.save
-rw-r--r-- 1 root root   51 Jul 16 21:34 ros-latest.list
-rw-r--r-- 1 root root   51 Jul 16 21:34 ros-latest.list.save
-rw-r--r-- 1 root root    0 Mär 28 20:54 screenlets-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root    0 Mär 28 20:54 screenlets-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root   56 Jul 16 21:34 skype-stable.list
-rw-r--r-- 1 root root   56 Jul 16 21:34 skype-stable.list.save
-rw-r--r-- 1 root root  193 Jul 16 21:34 slack.list
-rw-r--r-- 1 root root  193 Jul 16 21:34 slack.list.save
-rw-r--r-- 1 root root   52 Jul 16 21:34 spotify.list
-rw-r--r-- 1 root root   52 Jul 16 21:34 spotify.list.save
-rw-r--r-- 1 root root  130 Jul 16 21:34 team-xbmc-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root  130 Jul 16 21:34 team-xbmc-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  158 Jul 16 21:34 terry_guo-ubuntu-gcc-arm-embedded-xenial.list
-rw-r--r-- 1 root root  158 Jul 16 21:34 terry_guo-ubuntu-gcc-arm-embedded-xenial.list.save
-rw-r--r-- 1 root root  156 Jul 16 21:34 tsbarnes-ubuntu-indicator-keylock-xenial.list
-rw-r--r-- 1 root root  156 Jul 16 21:34 tsbarnes-ubuntu-indicator-keylock-xenial.list.save
-rw-r--r-- 1 root root  308 Jul 16 21:34 ubuntu-toolchain-r-ubuntu-test-xenial.list
-rw-r--r-- 1 root root  308 Jul 16 21:34 ubuntu-toolchain-r-ubuntu-test-xenial.list.save
-rw-r--r-- 1 root root  158 Jul 16 21:34 umang-ubuntu-indicator-stickynotes-xenial.list
-rw-r--r-- 1 root root  158 Jul 16 21:34 umang-ubuntu-indicator-stickynotes-xenial.list.save
-rw-r--r-- 1 root root  136 Jul 16 21:34 webupd8team-ubuntu-java-xenial.list
-rw-r--r-- 1 root root  136 Jul 16 21:34 webupd8team-ubuntu-java-xenial.list.save
-rw-r--r-- 1 root root  138 Jul 16 21:34 wine-ubuntu-wine-builds-xenial.list
-rw-r--r-- 1 root root  138 Jul 16 21:34 wine-ubuntu-wine-builds-xenial.list.save

```


```

sudo apt-get update
Hit:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com xenial InRelease                                                                                             
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                                                                                         
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                    
Hit:5 http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial InRelease                                                       
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                        
Hit:7 http://ppa.launchpad.net/octave/stable/ubuntu xenial InRelease                                                                            
Ign:8 http://linux.dropbox.com/ubuntu wily InRelease                                                                                            
Hit:9 http://dl.google.com/linux/chrome/deb stable Release                                                                                      
Get:10 http://linux.dropbox.com/ubuntu wily Release [6.596 B]                                                                                   
Hit:11 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu xenial InRelease                                                                
Hit:12 http://storage.googleapis.com/bazel-apt stable InRelease                                                                                 
Hit:13 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease                                                                           
Hit:14 https://repo.skype.com/deb stable InRelease                                                                                              
Hit:15 http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu xenial InRelease                                                              
Get:16 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                                     
Hit:17 http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu xenial InRelease                                                             
Ign:18 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  InRelease                                 
Get:19 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                          
Hit:20 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease                                                       
Hit:21 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  Release                                      
Hit:22 http://packages.ros.org/ros/ubuntu xenial InRelease                                                
Hit:26 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Fetched 313 kB in 2s (140 kB/s)
Reading package lists... Done

```

---

### Post by yosoufe on 2017-07-18
I followed all the dependencies and tries to download them. The main problem is the gcc version. These stuff require
```
gcc-5-base (= 5.4.0-6ubuntu1~16.04.4)
``` and I have ```
gcc (Ubuntu 5.4.1-2ubuntu1~16.04)
``` installed.

What do you  think?? shall I downgrade my gcc?? or is going to ruin everything?? or is there a better solution??

This is the error that I deduced I have a different version
```

sudo apt install libobjc-5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libobjc-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.1-2ubuntu1~16.04 is to be installed
                 Depends: libgcc-5-dev (= 5.4.0-6ubuntu1~16.04.4) but 5.4.1-2ubuntu1~16.04 is to be installed
                 Depends: libobjc4 (>= 5.4.0-6ubuntu1~16.04.4) but it is not going to be installed

```

---

