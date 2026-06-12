---
title: "Requires installation of untrusted packages"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by MrGibbage on 2015-08-09
Pretty much everything I try to install from the Ubuntu Software center always pops up a message that it requires the installation of untrusted packages. In fact, I am pretty sure it has said that for everything that I have tried installing. For example, I just tried installing the firewall config tool Gufw. Error. The button options are "OK" and "Repair", where, honestly, I would have expected an "Ignore" button, as in, "ignore this. I want to install it anyway". Neither of the buttons seem to do much of anything and there doesn't seem to be a way around it.

What am I doing wrong?

---

### Post by oldos2er on 2015-08-09
What version of Ubuntu are you using? Can you open a terminal, run the following command and copy/paste all the output here? ```
sudo apt-get update
```

---

### Post by MrGibbage on 2015-08-09
xbmc@xbmc-desktop:~$ sudo apt-get update
[sudo] password for xbmc: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-security InRelease                   
Get:2 [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) trusty InRelease                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
100% [2 InRelease gpgv 950 B] [Connecting to us.old-releases.ubuntu.com (92.242Splitting up /var/lib/apt/lists/partial/us.old-releases.ubuntu.com_ubuntu_dists_tIgn [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) trusty InRelease                         
E: GPG error: [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
xbmc@xbmc-desktop:~$

---

### Post by MrGibbage on 2015-08-10
Oh, I forgot to say that I am on 14.04.

---

### Post by Bashing-om on 2015-08-10
MrGibbage; Hello

In the update output:
> 
100% [2 InRelease gpgv 950 B] [Connecting to us.old-releases.ubuntu.com (92.242Splitting up /var/lib/apt/lists/partial/us.old-releases.ubuntu.com_ubuntu_dists_tIgn [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) trusty InRelease 
E: GPG error: [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)

Huh ? Why ! " us.old-releases.ubuntu.com" I can not imagine that repo to be of any use in the 14.04 release. Let's look at where that fetch is coming from:
Post back the results - Between Code Tags, Please - of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we look and see what we are going to do.

[INDENT][INDENT]there are those times that a thing seems right
[INDENT][INDENT][INDENT]but leads to the destruction of the system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MrGibbage on 2015-08-10
```

xbmc@xbmc-desktop:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted
     2    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
     3    
     4    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     5    # newer versions of the distribution.
     6    deb http://us.old-releases.ubuntu.com/ubuntu/ trusty main restricted
     7    deb-src http://us.old-releases.ubuntu.com/ubuntu/ trusty main restricted
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb http://us.old-releases.ubuntu.com/ubuntu/ trusty universe
    16    deb-src http://us.old-releases.ubuntu.com/ubuntu/ trusty universe
    17    
    18    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    19    ## team, and may not be under a free licence. Please satisfy yourself as to 
    20    ## your rights to use the software. Also, please note that software in 
    21    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    22    ## security team.
    23    deb http://us.old-releases.ubuntu.com/ubuntu/ trusty multiverse
    24    deb-src http://us.old-releases.ubuntu.com/ubuntu/ trusty multiverse
    25    
    26    ## N.B. software from this repository may not have been tested as
    27    ## extensively as that contained in the main release, although it includes
    28    ## newer versions of some applications which may provide useful features.
    29    ## Also, please note that software in backports WILL NOT receive any review
    30    ## or updates from the Ubuntu security team.
    31    
    32    
    33    ## Uncomment the following two lines to add software from Canonical's
    34    ## 'partner' repository.
    35    ## This software is not part of Ubuntu, but is offered by Canonical and the
    36    ## respective vendors as a service to Ubuntu users.
    37    # deb http://archive.canonical.com/ubuntu quantal partner
    38    # deb-src http://archive.canonical.com/ubuntu quantal partner
    39    
    40    ## This software is not part of Ubuntu, but is offered by third-party
    41    ## developers who want to ship their latest software.
    42    # deb http://extras.ubuntu.com/ubuntu saucy main
    43    # deb-src http://extras.ubuntu.com/ubuntu saucy main
    44    deb http://us.old-releases.ubuntu.com/ubuntu/ trusty-updates restricted main multiverse universe
    45    deb http://old-releases.ubuntu.com/ubuntu/ trusty-security restricted main multiverse universe
    46    # deb-src http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo lucid main
    47    
    48    
    49    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    50    # newer versions of the distribution.
    51    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
    52    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
    53    
    54    ## Major bug fix updates produced after the final release of the
    55    ## distribution.
    56    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    57    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    58    
    59    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    60    ## team. Also, please note that software in universe WILL NOT receive any
    61    ## review or updates from the Ubuntu security team.
    62    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    63    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    64    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    65    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    66    
    67    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    68    ## team, and may not be under a free licence. Please satisfy yourself as to 
    69    ## your rights to use the software. Also, please note that software in 
    70    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    71    ## security team.
    72    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    73    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    74    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    75    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    76    
    77    ## N.B. software from this repository may not have been tested as
    78    ## extensively as that contained in the main release, although it includes
    79    ## newer versions of some applications which may provide useful features.
    80    ## Also, please note that software in backports WILL NOT receive any review
    81    ## or updates from the Ubuntu security team.
    82    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    83    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    84    
    85    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    86    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    87    deb http://security.ubuntu.com/ubuntu trusty-security universe
    88    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    89    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    90    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    91    
    92    ## Uncomment the following two lines to add software from Canonical's
    93    ## 'partner' repository.
    94    ## This software is not part of Ubuntu, but is offered by Canonical and the
    95    ## respective vendors as a service to Ubuntu users.
    96    # deb http://archive.canonical.com/ubuntu trusty partner
    97    # deb-src http://archive.canonical.com/ubuntu trusty partner
    98    
    99    ## This software is not part of Ubuntu, but is offered by third-party
   100    ## developers who want to ship their latest software.
   101    deb http://extras.ubuntu.com/ubuntu trusty main
   102    deb-src http://extras.ubuntu.com/ubuntu trusty main
xbmc@xbmc-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open &#8216;/etc/apt/sources.list.d/*&#8217; for reading: No such file or directory
xbmc@xbmc-desktop:~$ tail -v -n +1 /etc/apt/sources.list
sources.list    sources.list.d/ 
xbmc@xbmc-desktop:~$ ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Aug  8 18:03 .
drwxr-xr-x 6 root root 4096 Aug  9 09:29 ..
xbmc@xbmc-desktop:~$ 

```

---

### Post by Bashing-om on 2015-08-10
MrGibbage; Humm ...

I can not fathom why:
> 
6    deb [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty main restricted
7    deb-src [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty main restricted
15    deb [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty universe
16    deb-src [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty universe
23    deb [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty multiverse
24    deb-src [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty multiverse
44    deb [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) trusty-updates restricted main multiverse universe
45    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) trusty-security restricted main multiverse universe

Would exist on the system as their existence on a stable 14.04 release can serve absolutely no purpose.

I would comment them all out/
make a backup prior to editing any file as Standard Operating Procedure 
make the edits
save the file .
Now what results:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by MrGibbage on 2015-08-10
All right. I think everything is good now. Thanks!

---

### Post by Bashing-om on 2015-08-10
MrGibbage; Great !

If all is good;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

