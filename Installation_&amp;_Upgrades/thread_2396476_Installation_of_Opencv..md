---
title: "Installation of Opencv."
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by sangamswadik on 2018-07-16
Hi all.I've just started using Ubuntu today(18.04).I want to install Open CV .I'm following  the procedure from Pyimagesearch
[https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/](https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/)

when I typed in this I got unable to locate package.

sudo apt-get install libavcodec-dev libavformat-dev libwscale-dev lib41-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libwscale-dev
E: Unable to locate package lib41-dev

can you please tell me how  I can resolve this?
Thanks

---

### Post by sangamswadik on 2018-07-16
I got this for cat -n  /etc/apt/sources.list
```
ubuntu@ubuntu-H310M-H:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
     2    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe #Added by software-properties
     3    
     4    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5    # newer versions of the distribution.
     6    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic main restricted universe
     7    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic main multiverse restricted
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates main restricted universe
    12    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates main multiverse restricted universe
    13    
    14    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15    ## team. Also, please note that software in universe WILL NOT receive any
    16    ## review or updates from the Ubuntu security team.
    17    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic universe
    18    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic multiverse
    26    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic multiverse
    27    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    28    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-backports main restricted multiverse universe
    36    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-backports main restricted multiverse universe
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    43    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    44    
    45    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    46    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main multiverse restricted universe
    47    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
ubuntu@ubuntu-H310M-H:~$ 

```

---

### Post by sangamswadik on 2018-07-16
And This.
```
$ apt-cache policy ubuntu-desktop
ubuntu-desktop:
  Installed: 1.417
  Candidate: 1.417
  Version table:
 *** 1.417 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by wildmanne39 on 2018-07-16
Hello and welcome to the forum!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

In the future please combine all the code into one post instead of creating several.

Thanks

---

### Post by deadflowr on 2018-07-17
libv4l-dev > that's a small L.
libswscale-dev > you missed the first S.

All else looks fine.

---

### Post by sangamswadik on 2018-07-17
Hi @deadflowr .Thank you for helping and notifying my mistake.

---

### Post by sangamswadik on 2018-07-17
> **wildmanne39 said:**
> Hello and welcome to the forum!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

In the future please combine all the code into one post instead of creating several.

Thanks


Sure !

---

