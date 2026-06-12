---
title: "Problems using apt-get"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by quei on 2018-05-08
Hi,
I'm a new user of Ubuntu and tried downloading a module for python, but apparently whenever i try to download something using apt-get command i get this error:
```

      
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_wily_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



```

i find a thread where a problem very similar to mine was solved: [https://ubuntuforums.org/showthread.php?t=1897475](https://ubuntuforums.org/showthread.php?t=1897475) 
but i still didn't managed to solve the problem, can anyone help me ?
Thanks!

---

### Post by Bashing-om on 2018-05-08
Hello quei;  Welcome to the forum.

what release are you running ?
> 
/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_wily_main_binary-amd64_Packages

Terminal command:
```

lsb_release -a

```
to verify we have someting we can work with.
wily ?? then:
> 
Ubuntu 15.10 (Wily Werewolf) was the 23rd release of Ubuntu. Support ended on July 28th, 2016.


[INDENT][INDENT]see which way we go
[/INDENT][/INDENT]

---

### Post by quei on 2018-05-08
Well if I understood i should be running the 16.04 release, that's what i get writing down lsb_release -a :
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by Bashing-om on 2018-05-08
quei; Great !

Then next is to find out where 'wily' is coming from.
Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And clean up to fix the issue.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by quei on 2018-05-09
So the from the first command i get:
```

     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://nl.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://nl.archive.ubuntu.com/ubuntu/ xenial universe
    15    deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb http://nl.archive.ubuntu.com/ubuntu/ xenial multiverse
    23    deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial multiverse
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
    36    # deb http://archive.canonical.com/ubuntu trusty partner
    37    # deb-src http://archive.canonical.com/ubuntu trusty partner
    38    
    39    deb http://archive.canonical.com/ xenial partner
    40    # deb-src http://archive.canonical.com/ trusty partner
    41    deb http://security.ubuntu.com/ubuntu/ xenial-security restricted universe multiverse main
    42    deb http://nl.archive.ubuntu.com/ubuntu/ xenial-updates restricted universe multiverse main


```

While i get that from the second one:
```

==> /etc/apt/sources.list.d/damien-moore-ubuntu-codeblocks-stable-xenial.list <==
deb http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu xenial main
# deb-src http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu xenial main

==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu trusty main

==> /etc/apt/sources.list.d/dropbox.list.save <==
# deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list <==
# deb http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main

==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.distUpgrade <==
deb http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main

==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.save <==
# deb http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main

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

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/spotify.list <==
# deb http://repository.spotify.com stable non-free # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/spotify.list.distUpgrade <==
deb http://repository.spotify.com stable non-free

==> /etc/apt/sources.list.d/spotify.list.save <==
# deb http://repository.spotify.com stable non-free # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/windscribe-repo.list <==
deb https://repo.windscribe.com/ubuntu xenial main

```

---

### Post by Bashing-om on 2018-05-09
queil Uh Huh :)

Here be that wily source:
> 
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily main


As there is a PPA in xenial for dropbox:
[https://linux.dropboxstatic.com/ubuntu/dists/](https://linux.dropboxstatic.com/ubuntu/dists/)
 if you desire to maintain dropbox: change wily here
 /etc/apt/sources.list.d/dropbox.list
 to xenial and update:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]no step for a stepper[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2018-05-09
Looks like the problem is some of your repositories are not xenaial. You can easily get this way if your use thrid party repositories or PPAs. You should check them all and make sure they are the correct version.

---

### Post by quei on 2018-05-10
Thank you very much, I managed at the end!
Thanks!

---

### Post by Bashing-om on 2018-05-10
quei; Great !

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]weren't nothing but a thing :)
[/INDENT]

---

