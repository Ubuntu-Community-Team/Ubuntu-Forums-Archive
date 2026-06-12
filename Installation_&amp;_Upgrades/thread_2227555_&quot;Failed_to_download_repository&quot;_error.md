---
title: "&quot;Failed to download repository&quot; error"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2014-06-02
I can't update software because the update-manager throws the error "Failed to download repository" and hangs.

---

### Post by Ubi_one_2014 on 2014-06-02
what happends when you do 
apt-get update

in a terminal?

---

### Post by asb3 on 2014-06-02
> **Ubi_one_2014 said:**
> what happends when you do 
apt-get update

in a terminal?

cavu{asb}97: sudo apt-get update
[sudo] password for asb: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main amd64 Packages          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse amd64 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources/DiffIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages/DiffIndex    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages/DiffIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main amd64 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2014-06-02
asb3; Hello.

The release 'raring' (13.04) has reached End-Of-Life and the software repository no longer exist.

It is highly recommended that you upgrade to a current release (14.04 is available ).
and 
[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by asb3 on 2014-06-02
> **Bashing-om said:**
> asb3; Hello.

The release 'raring' (13.04) has reached End-Of-Life and the software repository no longer exist.

It is highly recommended that you upgrade to a current release (14.04 is available ).
and [INDENT][INDENT]just keep on keep'n on
[/INDENT]
[/INDENT]


I was trying to update to 13.10 when I first got the error, causing the update to fail.  What should I do?

---

### Post by Bashing-om on 2014-06-03
asb3; Hi !

If it is your desire to upgrade on-line rather than do a clean install there is a means to do so as instructed in this tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades).

There always exist the possibility of errors and faults. it is the recommendation to backup your personal files before version upgrading .

the good news is that there is a way

---

### Post by Ubi_one_2014 on 2014-06-03
> **asb3 said:**
> I was trying to update to 13.10 when I first got the error, causing the update to fail.  What should I do?

how did you update?
what is your current ubuntu version? 13.10 or an earlier version?

---

### Post by asb3 on 2014-06-03
> **Bashing-om said:**
> asb3; Hi !

If it is your desire to upgrade on-line rather than do a clean install there is a means to do so as instructed in this tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades).

There always exist the possibility of errors and faults. it is the recommendation to backup your personal files before version upgrading .

the good news is that there is a way

The last upgrade covered in the tutorial is 8.01 to 9.04.

Assuming the same procedure should work for 13.04 to 13.10, ran
sudo aptitude update && sudo aptitude safe-upgrade

which failed because aptitude was not installed.

I installed aptitude using the package manager. 

The program ran for a while, and then threw the error:
dictionary-common
subprocess installed post-installation script
returned error exit status 25

Hoping the error was benign, I repeated

sudo aptitude update && sudo aptitude safe-upgrade

Lots of stuff was installed, but there were some errors:

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources:](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources:) 404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages:](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages:) 404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages:](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages:) 404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache

Current status: 4 new [+4].

With these errors, is there any chance that running
sudo do-release-upgrade

to upgrade to 13.10 will work?  I'm reluctant to try it, for fear of clobbering 13.04 without 
succesfully installing 13.10.

What failed in my updates?

---

### Post by Bashing-om on 2014-06-03
asb3l Hello,


It is a hassle, but can  be done. The doc is old, but still vialbe and relates to your situation - the means remains the same.
Page 2 of the tutorial has the directions to change your source list file to "old releases".
With that guide you will version upgrade to release 13.10. Now release 13.10 is End-Of-Life next month. At that time the 1st point release of 14.04 will be released/available and then version upgrade to release 14.04.1;
Else if in a hurry to get to 14.04, there is a way to do so. 14.04 is still in "development" but is considered to be stable.

Hope this helps
[INDENT][INDENT]the longest journey begins with 
[INDENT][INDENT][INDENT][INDENT]but  small step
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asb3 on 2014-06-04
I followed the tutorial.  The upgrade failed:

I added the lines to /etc/apt/sources.list
I ran 
sudo aptitude update && sudo aptitude safe-upgrade

which threw some errors:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found
97% [Working]W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources:](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources:) 404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages:](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages:) 404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages:](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages:) 404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache

I then tried to upgrade:
sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.

Now what?

---

### Post by Bashing-om on 2014-06-04
asb3; Humm ...

Let's look at your sources, see what conclusions we can draw.
Post back the outputs - between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once we are stable on 13.10 will see what is the next to do.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by asb3 on 2014-06-04
```

cavu{asb}89: cat /etc/*-release                                                                                                                   
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 13.04"
VERSION_ID="13.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

cavu{asb}86: cat -n /etc/apt/sources.list
     1  # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
     2
     3  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4  # newer versions of the distribution.
     5  deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
     6  deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
    11  deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team. Also, please note that software in universe WILL NOT receive any
    15  ## review or updates from the Ubuntu security team.
    16  deb http://us.archive.ubuntu.com/ubuntu/ raring universe
    17  deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
    18  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team, and may not be under a free licence. Please satisfy yourself as to
    23  ## your rights to use the software. Also, please note that software in
    24  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25  ## security team.
    26  deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
    28  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
    29  deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
    30
    31  ## N.B. software from this repository may not have been tested as
    32  ## extensively as that contained in the main release, although it includes
    33  ## newer versions of some applications which may provide useful features.
    34  ## Also, please note that software in backports WILL NOT receive any review
    35  ## or updates from the Ubuntu security team.
    36
    37  deb http://security.ubuntu.com/ubuntu raring-security main restricted
    38  deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
    39  deb http://security.ubuntu.com/ubuntu raring-security universe
    40  deb-src http://security.ubuntu.com/ubuntu raring-security universe
    41  deb http://security.ubuntu.com/ubuntu raring-security multiverse
    42  deb-src http://security.ubuntu.com/ubuntu raring-security multiverse
    43
    44  ## Uncomment the following two lines to add software from Canonical's
    45  ## 'partner' repository.
    46  ## This software is not part of Ubuntu, but is offered by Canonical and the
    47  ## respective vendors as a service to Ubuntu users.
    48  # deb http://archive.canonical.com/ubuntu quantal partner
    49  # deb-src http://archive.canonical.com/ubuntu quantal partner
    50
    51  ## This software is not part of Ubuntu, but is offered by third-party
    52  ## developers who want to ship their latest software.
    53  deb http://extras.ubuntu.com/ubuntu raring main
    54  deb-src http://extras.ubuntu.com/ubuntu raring main
    55
    56  deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
    57  deb http://old-releases.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
    58  deb http://old-releases.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
cavu{asb}87: ls -la /etc/apt/sources.list.d
total 28
drwxr-xr-x 2 root root 4096 Jun  2 17:48 .
drwxr-xr-x 6 root root 4096 Jun  4 07:39 ..
-rw-r--r-- 1 root root  134 Jun  2 17:52 kubuntu-ppa-ppa-raring.list
-rw-r--r-- 1 root root  134 Jun  2 17:52 kubuntu-ppa-ppa-raring.list.save
-rw-r--r-- 1 root root  226 Jun  2 17:52 unity-2d-team-unity-2d-daily-quantal.list
-rw-r--r-- 1 root root  160 May 29  2013 unity-2d-team-unity-2d-daily-quantal.list.distUpgrade
-rw-r--r-- 1 root root  226 Jun  2 17:52 unity-2d-team-unity-2d-daily-quantal.list.save
cavu{asb}88: tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/kubuntu-ppa-ppa-raring.list <==                                                                                       
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu raring main                                                                                   
# deb-src http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu raring main                                                                             
                                                                                                                                                  
==> /etc/apt/sources.list.d/kubuntu-ppa-ppa-raring.list.save <==                                                                                  
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu raring main                                                                                   
# deb-src http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu raring main                                                                             
                                                                                                                                                  
==> /etc/apt/sources.list.d/unity-2d-team-unity-2d-daily-quantal.list <==                                                                         
# deb http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu raring main # disabled on upgrade to raring                                    
# deb-src http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu raring main # disabled on upgrade to raring                                
                                                                                                                                                  
==> /etc/apt/sources.list.d/unity-2d-team-unity-2d-daily-quantal.list.distUpgrade <==                                                             
deb http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu quantal main                                                                     
deb-src http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu quantal main                                                                 
                                                                                                                                                  
==> /etc/apt/sources.list.d/unity-2d-team-unity-2d-daily-quantal.list.save <==                                                                    
# deb http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu raring main # disabled on upgrade to raring                                    
# deb-src http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu raring main # disabled on upgrade to raring                                

```

---

### Post by Bashing-om on 2014-06-04
asb3; OK,

these: from "/etc/apt/sources.list" file:
```

56  deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
57  deb http://old-releases.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
58  deb http://old-releases.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse

``` I see no need of, and appear to be duplicates of the "raring" install. I suggest that you comment out those entries.

And this from the 3rd party directory "/etc/apt/sources.list.d" :
```

/etc/apt/sources.list.d/unity-2d-team-unity-2d-daily-quantal.list.distUpgrade

```
no longer has support, per:
[http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/)
It should be removed.

Once these are done, try again and see what results from:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##does not do version upgrade, just installed packages upgrades that apt-get install does not handle##

```

Now let's see what the condition the condition is in.

---

### Post by asb3 on 2014-06-05
I ran
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

and they seemed to succeed.  I then rebooted the computer, and I'm still running 13.04:
cavu{asb}83: lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring

What next?

---

### Post by Bashing-om on 2014-06-05
asb3; Hello;


OK, running clean. Try the End-of-Life upgrade procedure once more;
Remember the upgrade command is
```

sudo do-release-upgrade

```

[INDENT][INDENT]we will get through this
[/INDENT][/INDENT]

---

### Post by asb3 on 2014-06-06
The upgrade failed again.  I reran 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo do-release-upgrade
and rebooted, and I'm still on 13.04
```

cavu{asb}83: lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring
cavu{asb}84: sudo apt-get update
Hit http://security.ubuntu.com raring-security Release.gpg
Hit http://us.archive.ubuntu.com raring Release.gpg                                                                         
Hit http://security.ubuntu.com raring-security Release                                                                      
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                                                                                        
Hit http://us.archive.ubuntu.com raring Release                                                                                                    
Hit http://security.ubuntu.com raring-security/main Sources                                                                 
Hit http://security.ubuntu.com raring-security/restricted Sources                                                           
Hit http://us.archive.ubuntu.com raring-updates Release                                                                                            
Hit http://security.ubuntu.com raring-security/universe Sources                                                                                     
Hit http://us.archive.ubuntu.com raring/main Sources                                                                                                
Hit http://security.ubuntu.com raring-security/multiverse Sources                                                                                    
Hit http://us.archive.ubuntu.com raring/restricted Sources                                                                                           
Ign http://extras.ubuntu.com raring Release.gpg                                                                                                      
Hit http://security.ubuntu.com raring-security/main amd64 Packages                                                                                    
Hit http://us.archive.ubuntu.com raring/universe Sources                                                                                              
Hit http://ppa.launchpad.net raring Release.gpg                                                                                                       
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com raring/multiverse Sources                                                                                            
Hit http://security.ubuntu.com raring-security/universe amd64 Packages                                                                                 
Hit http://us.archive.ubuntu.com raring/main amd64 Packages                                                                                            
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages                                                                                
Ign http://extras.ubuntu.com raring Release                                                                                                             
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages                                                                                        
Hit http://security.ubuntu.com raring-security/main i386 Packages                                                                                        
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages      
Hit http://security.ubuntu.com raring-security/restricted i386 Packages                    
Hit http://ppa.launchpad.net raring Release                                                
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages                           
Hit http://security.ubuntu.com raring-security/universe i386 Packages
Hit http://us.archive.ubuntu.com raring/main i386 Packages           
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages
Ign http://extras.ubuntu.com raring/main Sources/DiffIndex           
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages     
Hit http://security.ubuntu.com raring-security/main Translation-en   
Hit http://us.archive.ubuntu.com raring/universe i386 Packages       
Hit http://ppa.launchpad.net raring/main amd64 Packages              
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages     
Ign http://extras.ubuntu.com raring/main amd64 Packages/DiffIndex    
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages               
Ign http://extras.ubuntu.com raring/main i386 Packages/DiffIndex     
Hit http://us.archive.ubuntu.com raring/main Translation-en          
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en    
Hit http://security.ubuntu.com raring-security/universe Translation-en
Hit http://us.archive.ubuntu.com raring/restricted Translation-en    
Hit http://us.archive.ubuntu.com raring/universe Translation-en      
Hit http://us.archive.ubuntu.com raring-updates/main Sources         
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources   
Hit http://us.archive.ubuntu.com raring-updates/universe Sources     
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources   
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages  
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages
Ign http://ppa.launchpad.net raring/main Translation-en_US
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Ign http://ppa.launchpad.net raring/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Ign http://extras.ubuntu.com raring/main Translation-en_US
Ign http://extras.ubuntu.com raring/main Translation-en
Err http://extras.ubuntu.com raring/main Sources
  404  Not Found
Err http://extras.ubuntu.com raring/main amd64 Packages
  404  Not Found
Err http://extras.ubuntu.com raring/main i386 Packages
  404  Not Found
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
cavu{asb}85: sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  kscreen
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
cavu{asb}86: sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kscreen
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
cavu{asb}87: sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found

```

---

### Post by Ubi_one_2014 on 2014-06-06
remove all of this from your sources.list:

```
[COLOR=#000000][FONT=Ubuntu Mono]50[/FONT][/COLOR]   
     51  ## This software is not part of Ubuntu, but is offered by third-party
    52  ## developers who want to ship their latest software.
    53  deb http://extras.ubuntu.com/ubuntu raring main
    54  deb-src http://extras.ubuntu.com/ubuntu raring main
    55
    56  deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
    57  deb http://old-releases.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse 
    58  deb http://old-releases.ubuntu.com/ubuntu/ raring-security main restricted universe multivers
```

---

### Post by asb3 on 2014-06-06
I commented out the lines and tried again.  No error messages, but the upgrade still failed.
```

cavu{asb}81: 
cavu{asb}84: cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
##deb http://extras.ubuntu.com/ubuntu raring main
##deb-src http://extras.ubuntu.com/ubuntu raring main

##deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
##deb http://old-releases.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
##deb http://old-releases.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse

sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for asb: 
Hit http://security.ubuntu.com raring-security Release.gpg
Hit http://us.archive.ubuntu.com raring Release.gpg                       
Hit http://security.ubuntu.com raring-security Release                    
Hit http://us.archive.ubuntu.com raring-updates Release.gpg               
Hit http://us.archive.ubuntu.com raring Release                            
Hit http://security.ubuntu.com raring-security/main Sources
Hit http://us.archive.ubuntu.com raring-updates Release               
Hit http://security.ubuntu.com raring-security/restricted Sources
Hit http://us.archive.ubuntu.com raring/main Sources                  
Hit http://security.ubuntu.com raring-security/universe Sources
Hit http://us.archive.ubuntu.com raring/restricted Sources
Hit http://security.ubuntu.com raring-security/multiverse Sources
Hit http://ppa.launchpad.net raring Release.gpg
Hit http://us.archive.ubuntu.com raring/universe Sources
Hit http://security.ubuntu.com raring-security/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/multiverse Sources
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring/main amd64 Packages
Hit http://security.ubuntu.com raring-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages
Hit http://security.ubuntu.com raring-security/main i386 Packages
Hit http://ppa.launchpad.net raring Release    
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages
Hit http://security.ubuntu.com raring-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring/main i386 Packages
Hit http://security.ubuntu.com raring-security/universe i386 Packages
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring/universe i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages
Hit http://security.ubuntu.com raring-security/main Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring/main Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/restricted Translation-en                                                                                 
Hit http://security.ubuntu.com raring-security/universe Translation-en
Hit http://us.archive.ubuntu.com raring/restricted Translation-en
Hit http://us.archive.ubuntu.com raring/universe Translation-en
Hit http://us.archive.ubuntu.com raring-updates/main Sources
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources
Hit http://us.archive.ubuntu.com raring-updates/universe Sources
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
                            
Resolving dependencies...                
The following NEW packages will be installed:
  libkscreen1{a} 
The following packages will be REMOVED:
  libkscreen0{u} 
The following packages will be upgraded:
  kscreen 
1 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 259 kB of archives. After unpacking 127 kB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://us.archive.ubuntu.com/ubuntu/ raring-updates/universe kscreen amd64 1.0.1-0ubuntu1~ubuntu13.04.1 [168 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ raring-updates/universe libkscreen1 amd64 1.0.1-0ubuntu1~ubuntu13.04.1 [90.8 kB]
Fetched 259 kB in 0s (945 kB/s)       
(Reading database ... 308109 files and directories currently installed.)
Preparing to replace kscreen 0.0.92-0ubuntu0.2 (using .../kscreen_1.0.1-0ubuntu1~ubuntu13.04.1_amd64.deb) ...
Unpacking replacement kscreen ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
(Reading database ... 308128 files and directories currently installed.)
Removing libkscreen0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package libkscreen1.
(Reading database ... 308121 files and directories currently installed.)
Unpacking libkscreen1 (from .../libkscreen1_1.0.1-0ubuntu1~ubuntu13.04.1_amd64.deb) ...
Setting up libkscreen1 (1.0.1-0ubuntu1~ubuntu13.04.1) ...
Setting up kscreen (1.0.1-0ubuntu1~ubuntu13.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 updates [-1].
cavu{asb}82: sudo apt-get update
Hit http://us.archive.ubuntu.com raring Release.gpg
Hit http://us.archive.ubuntu.com raring-updates Release.gpg               
Hit http://us.archive.ubuntu.com raring Release                           
Hit http://us.archive.ubuntu.com raring-updates Release                                                                
Hit http://us.archive.ubuntu.com raring/main Sources                                            
Hit http://us.archive.ubuntu.com raring/restricted Sources          
Hit http://us.archive.ubuntu.com raring/universe Sources
Hit http://ppa.launchpad.net raring Release.gpg
Hit http://us.archive.ubuntu.com raring/multiverse Sources
Hit http://us.archive.ubuntu.com raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages
Hit http://ppa.launchpad.net raring Release    
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring/universe i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring/main Translation-en
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring/restricted Translation-en
Hit http://us.archive.ubuntu.com raring/universe Translation-en
Hit http://us.archive.ubuntu.com raring-updates/main Sources
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources
Hit http://us.archive.ubuntu.com raring-updates/universe Sources
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://security.ubuntu.com raring-security Release.gpg
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://security.ubuntu.com raring-security Release
Hit http://security.ubuntu.com raring-security/main Sources           
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/restricted Sources
Hit http://security.ubuntu.com raring-security/universe Sources
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Sources
Hit http://security.ubuntu.com raring-security/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages
Hit http://security.ubuntu.com raring-security/universe amd64 Packages
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages
Hit http://security.ubuntu.com raring-security/main i386 Packages
Hit http://security.ubuntu.com raring-security/restricted i386 Packages
Hit http://security.ubuntu.com raring-security/universe i386 Packages
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages
Hit http://security.ubuntu.com raring-security/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://security.ubuntu.com raring-security/universe Translation-en
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Reading package lists... Done
cavu{asb}83: sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found

```

---

### Post by Ubi_one_2014 on 2014-06-07
pls post the output of:
sudo apt-get remove kscreen libscreen

---

### Post by asb3 on 2014-06-07
cavu{asb}88: sudo apt-get remove kscreen libscreen
[sudo] password for asb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libscreen

---

### Post by asb3 on 2014-06-09
I finally upgraded by system.  The problem was in the file
/etc/update-manager/release-upgrades.

I changed the line
Prompt=lts

to

Prompt=normal

and the upgrade succeeded.  I was then able to upgrade to 14.04, so I'm up to date.

Thanks to all who helped.

I'd like to change the status of the tread to "Solved", but I don't know how.

---

### Post by Bashing-om on 2014-06-09
asb3; Outstanding !

Glad you figured it out, sure had me stumped what was the problem. I will file that one for future reference .

To mark as solved.
top of the post: thread tools -> "mark as solved".

[INDENT][INDENT]enjoy
[INDENT][INDENT][INDENT]and keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

