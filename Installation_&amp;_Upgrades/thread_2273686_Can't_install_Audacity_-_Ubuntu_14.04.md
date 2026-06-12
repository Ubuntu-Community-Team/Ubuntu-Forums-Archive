---
title: "Can't install Audacity - Ubuntu 14.04"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by henrique8 on 2015-04-14
Hello there,

First, it is important to say that I am totally new to ubuntu.

Well, I got Audacity installed and working correctly for a couple of weeks. Suddenly, it started not to work anymore, and I couldnt import nor record anything.
So I`ve decided to remove it, using 
```
sudo apt-get purge audacity
```

Then, I've tried to install it again, using 
```
sudo apt-get install audacity
```

And this is what I got:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacity : Depends: audacity-data (= 2.0.5-1ubuntu3) but 2.0.5-1ubuntu3.2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

then I've tried to install it via software center, and got the following:

The following packages have unmet dependencies:

audacity: Depends: audacity-data (= 2.0.5-1ubuntu3) but 2.0.5-1ubuntu3.2 is to be installed
          Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.5 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.40.2-0ubuntu1 is to be installed
          Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.23-0ubuntu1.1 is to be installed
          Depends: libportaudio2 (>= 19+svn20101113-2~) but 19+svn20140130-1 is to be installed
          Depends: libstdc++6 (>= 4.4.0) but 4.8.2-19ubuntu1 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.12.1) but 2.8.12.1+dfsg-2ubuntu2 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.12.1) but 2.8.12.1+dfsg-2ubuntu2 is to be installed

Any ideas on how to solve this issue?

Thanks in advance!

Henrique

---

### Post by ubfan1 on 2015-04-14
You probably need to run
sudo apt-get update
before installing the audacity again.

---

### Post by Bucky Ball on 2015-04-15
Welcome. Try this:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors.

---

### Post by bapoumba on 2015-04-15
How did you install audacity in the first place ?
Are you using any repositories outside the regular ubuntu ones (ppas for ex) ?

In addition, and before you run Bucky's commands, please post the output to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by mc4man on 2015-04-15
If you haven't squared away - you have disabled the trusty-updates repo which has audacity @ 2.0.5-1ubuntu3.2
So open Software & Updates > Updates tab > enable the 1st 2 entries (trusty-security, trusty-updates) > reload sources & try again.

---

### Post by henrique8 on 2015-04-15
Guys, it worked!
I've executed Bucky's commands and it went fine without any errors. Thanks man :)

ubfan1, I've tried updating before, but it didn't work for the first time. Apparently, I got some dependencies problems and couldn't install some packages, and what Bucky suggested resolved the issue. I've read about those commands and found a nice explanation about the dist-upgrade in the link below, which helped me to understand.

[http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)

bapoumba, I know the problem was already solved, but here the outputs you asked. can you tell what are they for?

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://br.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://br.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://br.archive.ubuntu.com/ubuntu/ trusty universe
    15    deb-src http://br.archive.ubuntu.com/ubuntu/ trusty universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb http://br.archive.ubuntu.com/ubuntu/ trusty multiverse
    23    deb-src http://br.archive.ubuntu.com/ubuntu/ trusty multiverse
    24    
    25    ## N.B. software from this repository may not have been tested as
    26    ## extensively as that contained in the main release, although it includes
    27    ## newer versions of some applications which may provide useful features.
    28    ## Also, please note that software in backports WILL NOT receive any review
    29    ## or updates from the Ubuntu security team.
    30    
    31    
    32    ## Uncomment the following two lines to add software from Canonical's
    33    ## 'partner' repository.
    34    ## This software is not part of Ubuntu, but is offered by Canonical and the
    35    ## respective vendors as a service to Ubuntu users.
    36    deb http://archive.canonical.com/ubuntu trusty partner
    37    deb-src http://archive.canonical.com/ubuntu trusty partner
    38    
    39    ## This software is not part of Ubuntu, but is offered by third-party
    40    ## developers who want to ship their latest software.
    41    deb http://extras.ubuntu.com/ubuntu trusty main
    42    deb-src http://extras.ubuntu.com/ubuntu trusty main
```

```
ls -la /etc/apt/sources.list.d
total 16
drwxr-xr-x 2 root root 4096 Abr 13 18:41 .
drwxr-xr-x 6 root root 4096 Abr 14 20:45 ..
-rw-r--r-- 1 root root  180 Abr 13 18:41 google-talkplugin.list
-rw-r--r-- 1 root root  150 Abr  2 00:04 webupd8team-tor-browser-trusty.list
```

```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
```

Thank you all for the help!

---

### Post by Bucky Ball on 2015-04-16
Great news. Could you please mark the thread as solved by following the second link in my signature. This will not close the thread so discussion can continue. Just helps future travelers to find a fix.

Good luck and enjoy the OS and the learning curve. ;)

---

### Post by bapoumba on 2015-04-16
And please enable the security and updates repos as mc4man said in post #5, thanks.

---

