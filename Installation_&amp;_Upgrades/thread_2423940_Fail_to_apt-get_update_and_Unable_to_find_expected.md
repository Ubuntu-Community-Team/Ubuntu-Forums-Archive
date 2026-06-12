---
title: "Fail to apt-get update and Unable to find expected entry of sources. Ubuntu 16.04 LTS"
date: 2019-07-31
forum: Installation &amp; Upgrades
---

### Post by jiang765 on 2019-07-31
This is what my terminal shows:

```

$ sudo apt-get update

Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:2 [http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu) xenial InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                                                                                                            
Hit:4 [http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo](http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo) xenial InRelease                                                                                                 
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                                              
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                    
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease                                 
Hit:8 [https://typora.io/linux](https://typora.io/linux) ./ InRelease                                 
Hit:9 [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) xenial InRelease
Reading package lists... Done                     
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Unable to find expected entry 'http://us.archive.ubuntu.com/ubuntu//source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.[/QUOTE]

```

I am using Ubuntu 16.04 LTS.
  
The error is: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Unable to find expected entry '[http://us.archive.ubuntu.com/ubuntu//source/Sources](http://us.archive.ubuntu.com/ubuntu//source/Sources)' in Release file (Wrong sources.list entry or malformed file)

I tried  a lot of methods like changing source of update, changing  DNS and autoclean the list.They did not work for me. Hope someone can  fix my problem.

Thank you very much!

my sources.list is:
```

#deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

deb https://typora.io/linux ./
# deb-src https://typora.io/linux ./
deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo xenial main
# deb-src http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo xenial main
```

---

