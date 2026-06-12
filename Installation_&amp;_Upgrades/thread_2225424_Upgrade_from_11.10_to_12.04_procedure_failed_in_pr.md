---
title: "Upgrade from 11.10 to 12.04 procedure failed in preparation steps"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by snow-runner on 2014-05-21
Hello,

Trying to upgrade Ubuntu version from 11.10 to 12.04. 

Thankx in advance for help.

1. Ran update manager for getting the information on 12.04 packages for network install
2. Then I cklick CHECK button and get following error with the "Failed to download repository information 
                                                                                            Check your internet connection":
      
```
W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://si.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by snow-runner on 2014-05-21
Any help most aprreciated.
According to google sources it suppose to be the problem with lines in /etc/apt/sources.list. But I am not sure which lines are the problem so to be commented or deleted ?
Or any other idea?

---

### Post by snow-runner on 2014-05-21
Still do not get it why in the /etc/apt/sources.list the first line is deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
when my system is ubuntu 11.10 ?

---

### Post by Bashing-om on 2014-05-21
snow-runner; Hi !

Not enough information to this time to make a determination of the source of the problem.
What method are you doing, to do this release upgrade ? (from the 11.10 install -> online upgrade, from a 12.04 liveDVD, else ??)
As 11.10 is now End-Of-Life; maybe the repository has already been turned down (??).
In any event we need to look at the sources.list file and see why the "CD" source is enabled, as generally it is not to be enabled.

Do not know yet what is going on with your system as one of the destinations is reachable:
> 

sysop@1310mini:~$ ping -c3  91.189.88.153
PING 91.189.88.153 (91.189.88.153) 56(84) bytes of data.
64 bytes from 91.189.88.153: icmp_seq=1 ttl=48 time=133 ms
64 bytes from 91.189.88.153: icmp_seq=2 ttl=48 time=132 ms
64 bytes from 91.189.88.153: icmp_seq=3 ttl=48 time=134 ms

--- 91.189.88.153 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 132.661/133.529/134.826/0.934 ms
sysop@1310mini:~$

and will assume all others are also reachable.

Show us your current sources :
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

We will
[INDENT][INDENT]get to the bottom of things
[/INDENT][/INDENT]

---

### Post by snow-runner on 2014-05-21
hello  thanx for response.

Well about update manager strange behaviour !? Yes, guess I could make upgrade from DVD iso image .
But there still will be problem with unstable update manager when trying to make easier upgrading or installing packages that are checked as newest...and beinformed about them through update manager.
So guess to handle problem with update manager is good idea for future clean system work !?!?!

so command cat -n /etc/apt/sources.list is giving me this:  ( attention second command output is at the bottom )

     1    deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric main restricted
     6    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
    11    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric universe
    17    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric universe
    18    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates universe
    19    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric multiverse
    27    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric multiverse
    28    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
    29    deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
    30    
    31    ## Uncomment the following two lines to add software from the 'backports'
    32    ## repository.
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
    39    # deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
    40    
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
    45    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
    46    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
    47    
    48    ## Uncomment the following two lines to add software from Canonical's
    49    ## 'partner' repository.
    50    ## This software is not part of Ubuntu, but is offered by Canonical and the
    51    ## respective vendors as a service to Ubuntu users.
    52    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
    53    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
    54    
    55    ## This software is not part of Ubuntu, but is offered by third-party
    56    ## developers who want to ship their latest software.
    57    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    58    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    59    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
    60    deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe




2. 
cat /etc/apt/sources.list.d/*.list



deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) oneiric main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center
drvaric@drvaric-nb:/etc$ sudo cat /etc/apt/sources.list.d/*.list
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) oneiric main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center

---

### Post by Bashing-om on 2014-05-21
snow-runner; Well;

Like this.
> 
1 deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

The 'natty' release is of no value to you. Comment out that line (place # at start of line); 
Then - if you persist in attempting to  on-line release upgrade - follow the instructions as directed in:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


If you do a clean install -back up all personal data 1st - then all these problems you worry about are non-existent.

[INDENT][INDENT]all in what you want to do
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-05-22
Upgrades from 11.10 to 12.04 do still work, I know because I just performed a test to see what hardware stack was implemented, and upgrades do still use the Precise kernel and xorg versions. You probably should give this a browse:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you opt for a fresh install using the current 12.04.4 image you'll end up with a Saucy hardware enablement stack and need to upgrade to the Trusty stack later this year. I personally prefer using the archived 12.04.1 images for reinstalling:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

I know the header says 12.04.3 but the 12.04.1 and original 12.04 images are there and they use the Precise hardware stack which is supported throughout April 2017.

If you're still considering an upgrade just open the Update Manager and click on Settings in the lower left hand corner. That will open Software Sources, then click on the Ubuntu Software tab and make sure that nothing is checked in Installable from CD/DVD:

[ATTACH=CONFIG]253363[/ATTACH]

Probably also wise to click on the Other Software tab and make sure no CD's are checked there:

[ATTACH=CONFIG]253364[/ATTACH]

Then click on the Updates tab and make sure Notify me of a new version is set properly:

[ATTACH=CONFIG]253365[/ATTACH]

---

