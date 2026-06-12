---
title: "Upgrading from Xubunu 14.04 LTS to 16.04 LTS"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by boxcorner on 2016-07-26
What is the best way to upgrade from Xubuntu 14.04 LTS to 16.04 LTS , please?

---

### Post by childsey01 on 2016-07-26
GUI or command line.
GUI follow the software updater

Command line is:
sudo apt-get update
sudo apt-get dist-upgrade

If you have customised the distribution in a way you want to keep you would likely be better replacing dist-upgrade with just upgrade

You will unfortunately have to go through the tedious process of 4 upgrades though 14.04->14.10->15.04->15.10->16.04
You may want to instead just download an image and blow it all away.

---

### Post by boxcorner on 2016-07-26
Many thanks

**Addendum**
Each time I run
sudo apt-get update
I get
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found 
Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2016-07-26
boxcorner; Hello;

One can and does upgrade LTS-LTS (14.04 to 16.04 ) . When the upgrade path is established .. Normally this path is set with the 1st point release . This point release has a bug and the upgrade path has been withheld pending a resolution to the bug . Expected any day now. At that time the update manager will allow - when set to look for LTS release - you to directly upgrade to 16.04

However, the present system must be fully updated and the PPAs should be verified that there is support from the author in the new release. Many times the author of the PPA has not caught up with the new release .

Presently in your case with a 404 error .. we need to correct this;
Please post back the output of terminal commands:
```

sudo apt update
sudo apt upgrade

```

And we get you prepared for the release upgrade.

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by boxcorner on 2016-07-26
Thank you

```
rdh@rdh-Ideapad-Z570:~$ sudo apt update
[sudo] password for rdh: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65.9 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [5,929 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [158 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                   
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_GB            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [280 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                      
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [766 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [365 kB] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_GB                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_GB                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Fetched 1,675 kB in 16s (100 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
rdh@rdh-Ideapad-Z570:~$
```

---

### Post by boxcorner on 2016-07-26
```
rdh@rdh-Ideapad-Z570:~$ 
rdh@rdh-Ideapad-Z570:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
rdh@rdh-Ideapad-Z570:~$
```

---

### Post by QDR06VV9 on 2016-07-26
> **boxcorner said:**
> ```
rdh@rdh-Ideapad-Z570:~$ 
rdh@rdh-Ideapad-Z570:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
rdh@rdh-Ideapad-Z570:~$
```

boxcorner Please use Code Tags for long Out puts easier to read and follow..Thanks

---

### Post by Bashing-om on 2016-07-26
boxcornerl Yeah,

That PPA is no longer supported .. even in trusty;
See:
[http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/)
It has seen no activity since 09-Jun-2012 18:13	- quantal .

As this is a Cannon printer driver .. I do not know that we can ppa-purge to revert to what is in the software repository. But, we do need to get this source off the system.
Maybe a look at the source will shed some light on a means to do this:
Post back - Between code tags - ( maintain formatting and promotes the readability ) the output of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We do have to get this install all squared away prior to even considering a release upgrade to 16.04 - when the path is enabled.
We do this preparation in small steps.

[INDENT][INDENT]we will get there
[/INDENT][/INDENT]

---

### Post by boxcorner on 2016-07-26
Apologies. Wilco.

---

### Post by boxcorner on 2016-07-26
```

rdh@rdh-Ideapad-Z570:~$ 
rdh@rdh-Ideapad-Z570:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://archive.ubuntu.com/ubuntu/ trusty multiverse restricted universe main #Added by software-properties
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse restricted universe main #Added by software-properties
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://archive.ubuntu.com/ubuntu/ trusty universe
    17    deb http://archive.ubuntu.com/ubuntu/ trusty-updates universe
    18    
    19    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20    ## team, and may not be under a free licence. Please satisfy yourself as to 
    21    ## your rights to use the software. Also, please note that software in 
    22    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23    ## security team.
    24    deb http://archive.ubuntu.com/ubuntu/ trusty multiverse
    25    deb http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    26    
    27    ## N.B. software from this repository may not have been tested as
    28    ## extensively as that contained in the main release, although it includes
    29    ## newer versions of some applications which may provide useful features.
    30    ## Also, please note that software in backports WILL NOT receive any review
    31    ## or updates from the Ubuntu security team.
    32    deb http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    33    deb-src http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties
    34    
    35    deb http://archive.ubuntu.com/ubuntu/ trusty-security main restricted
    36    deb-src http://archive.ubuntu.com/ubuntu/ trusty-security multiverse restricted universe main #Added by software-properties
    37    deb http://archive.ubuntu.com/ubuntu/ trusty-security universe
    38    deb http://archive.ubuntu.com/ubuntu/ trusty-security multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    # deb http://archive.canonical.com/ubuntu precise partner
    45    # deb-src http://archive.canonical.com/ubuntu precise partner
    46    
    47    ## This software is not part of Ubuntu, but is offered by third-party
    48    ## developers who want to ship their latest software.
    49    deb http://extras.ubuntu.com/ubuntu trusty main
    50    deb-src http://extras.ubuntu.com/ubuntu trusty main
rdh@rdh-Ideapad-Z570:~$ 


```

---

### Post by boxcorner on 2016-07-26
```

rdh@rdh-Ideapad-Z570:~$ 
rdh@rdh-Ideapad-Z570:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dhor-myway-trusty.list <==
deb http://ppa.launchpad.net/dhor/myway/ubuntu trusty main

==> /etc/apt/sources.list.d/dhor-myway-trusty.list.save <==
deb http://ppa.launchpad.net/dhor/myway/ubuntu trusty main

==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main

==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main

==> /etc/apt/sources.list.d/dimula73-krita-trusty.list <==
deb http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main

==> /etc/apt/sources.list.d/dimula73-krita-trusty.list.save <==
deb http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list <==

==> /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.save <==

==> /etc/apt/sources.list.d/inameiname-stable-trusty.list <==
deb http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/inameiname-stable-trusty.list.save <==
deb http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/inameiname/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main

==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list.save <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main

==> /etc/apt/sources.list.d/michael-gruz-canon-trusty.list <==
deb http://ppa.launchpad.net/michael-gruz/canon/ubuntu trusty main
# deb-src http://ppa.launchpad.net/michael-gruz/canon/ubuntu trusty main
# deb-src http://ppa.launchpad.net/michael-gruz/canon/ubuntu trusty main

==> /etc/apt/sources.list.d/michael-gruz-canon-trusty.list.save <==
deb http://ppa.launchpad.net/michael-gruz/canon/ubuntu trusty main
# deb-src http://ppa.launchpad.net/michael-gruz/canon/ubuntu trusty main

==> /etc/apt/sources.list.d/msylwester-digikam-trusty.list <==
deb http://ppa.launchpad.net/msylwester/digikam/ubuntu trusty main

==> /etc/apt/sources.list.d/msylwester-digikam-trusty.list.save <==
deb http://ppa.launchpad.net/msylwester/digikam/ubuntu trusty main

==> /etc/apt/sources.list.d/nvbn-rm-ppa-precise.list <==

==> /etc/apt/sources.list.d/nvbn-rm-ppa-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/nvbn-rm-ppa-precise.list.save <==

==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list <==
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main

==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list.save <==
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main

==> /etc/apt/sources.list.d/philip5-extra-trusty.list <==
deb http://ppa.launchpad.net/philip5/extra/ubuntu trusty main

==> /etc/apt/sources.list.d/philip5-extra-trusty.list.save <==
deb http://ppa.launchpad.net/philip5/extra/ubuntu trusty main

==> /etc/apt/sources.list.d/philip5-kubuntu-backports-trusty.list <==
deb http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main

==> /etc/apt/sources.list.d/philip5-kubuntu-backports-trusty.list.save <==
deb http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_linux-disk-cleaner_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/linux-disk-cleaner/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_linux-disk-cleaner_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/linux-disk-cleaner/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/ricotz-testing-precise.list <==

==> /etc/apt/sources.list.d/ricotz-testing-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/ricotz/testing/ubuntu precise main
deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu precise main

==> /etc/apt/sources.list.d/ricotz-testing-precise.list.save <==

==> /etc/apt/sources.list.d/tsbarnes-indicator-keylock-precise.list <==

==> /etc/apt/sources.list.d/tsbarnes-indicator-keylock-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu precise main
deb-src http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu precise main

==> /etc/apt/sources.list.d/tsbarnes-indicator-keylock-precise.list.save <==

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
rdh@rdh-Ideapad-Z570:~$ 



```

---

### Post by Bashing-om on 2016-07-26
boxcorner; Ouch;

A bunch of PPAs and several that are no longer supported and/or a precise source enabled ..
[http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu)
[http://ppa.launchpad.net/msylwester/digikam/ubuntu/dists/](http://ppa.launchpad.net/msylwester/digikam/ubuntu/dists/)
[http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/dists/](http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/dists/)
[http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu) precise
[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
[http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu) precise main

With this such an old install .. and with a lot of old config files, and non-support of some PPAs and the work to remove these;
I would give serious consideration of a fresh clean install of 16.04 and start all over from a clean slate. A fresh install in all likely hood would be much faster and easier than fixing this present install and preping to release upgrade.

However, it is your call - your system - as to what you want to do ..

[INDENT][INDENT]a long hard road ?
[/INDENT][/INDENT]

---

### Post by boxcorner on 2016-07-26
Understood. When I installed 16.04 on a Toshiba, from a USB key recently, it recognized that Windows was already there, created a partition for itself and all worked relatively smoothly, apart from having to to do a chdsk and re-establish wireless connectivity via Windows, before I could get it working in Xubuntu. 

However, when I tried to upgrade to 16.04 LTS my Lenovo it didn't recognize the existing dual-boot for Windows and wanted to reformat the entire drive, hence I backed out. I am willing to do a fresh install, but would need help to avoid destroying my Windows installation. I rarely use it, but some apps such as Garmin GPS don't offer a Linux variant. Also, I will need to back up my data from Xubunu, particularly Thunderbird emails, Arduino code, Krita artwork, etc. I recently saw a page which gave sensible advice on what to back up prior to doing a fresh install. Can't remember whether I bookmarked it. In any case, any advice on how to do a fresh install without destroying my Windows dual-boot configuration would be most welcome. Thank you.

---

### Post by Bashing-om on 2016-07-26
boxcorner; Yuk on me.

I am no longer Windows literate, and would not want to miss lead you in any respect.
This box is EFI endowed I "assume" and Again, I have no experience with such systems.

Let's await the guidance of those here on the forum who do have the experience to assist .

I still believe in your case, you are the better served with a clean fresh install.

[INDENT][INDENT]if I know it all
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by boxcorner on 2016-07-26
Thank you for your understanding. I'm definitely not a fan of Windows, but unfortunately some apps still aren't available in Linux flavour. Roll-on the day when I can ditch Windows altogether :~)

---

### Post by Bashing-om on 2016-07-26
boxcorner; K;

I am fortunate in that I left Windows back in XP SP2, and have never had the need to look back.

I will continue to keep an eye on this thread, see what others advise and how I might be of help.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by boxcorner on 2016-07-26
That's when I switched from Windows to Ubuntu, and what I left on my old desktop PC. My only regret is that I didn't do so earlier. This Lenovo laptop happened to have Windows 7 on it, hence I configured it for multi-booting. I stumbled across Xubuntu when trying to get Krita working satisfactorily with a Wacom Intuos pen tablet. Once again, late to the party, I wish I had discovered Xubuntu sooner.

---

### Post by QIII on 2016-07-26
Just a note, as I don't see it mentioned after some incorrect advice was given:  neither upgrade nor dist-upgrade will upgrade to a new release.  Neither command is appropriate for upgrading from 14.04 to 16.04.

Each of those commands upgrades packages within the current release.

Cheers!

---

### Post by QDR06VV9 on 2016-07-26
> **QIII said:**
> Just a note, as I don't see it mentioned after some incorrect advice was given:  neither upgrade nor dist-upgrade will upgrade to a new release.  Neither command is appropriate for upgrading from 14.04 to 16.04.

Each of those commands upgrades packages within the current release.

Cheers!

+1
It’s also worth remembering that **you don’t have to upgrade right away. A new release doesn’t make an old one obsolete. **Ubuntu 14.04 LTS is supported until 2019, remember. If your current system is ticking along nicely **ask yourself if you really need to rock the boat.**
If stability matters more than shiny new features, you can always wait a few months for the (inevitable) early kinks to get worked out and upgrade then.

Trigger The Upgrade: **and you have now become a tester for the Upgrade Process.**
With updates installed open the Terminal. Type the following command:

```
sudo update-manager -d
```
Here is just a Taste of what you will see....and worth mentioning here it did disable all 3rd party PPA's

---

### Post by boxcorner on 2016-07-27
Thank you. Yes, I know I don't *have to* upgrade and I do understand what LTS signifies. 
This thread, about upgrading Xubuntu from 14.04 LTS to 16.04 LTS, stems from another thread
[https://ubuntuforums.org/showthread.php?t=2331727](https://ubuntuforums.org/showthread.php?t=2331727)
which is about being unable to switch off wireless hotspot in Xubuntu 14.04 LTS on my Lenovo Z570 laptop.
So, I'm still a tester for that version :~) 
In my experience, the same applies to all versions of software.
Microsoft is world-renowned for getting people to pay for the privilege of testing their software.
While trying to fix the hotspot problem on my Lenovo, I installed Xubuntu 16.04 on my Toshiba ND550D notebook.
The only reason for considering upgrading Xubuntu on my Lenovo was so I could stick to using one version.
I gave up being an early adopter long ago, but nowadays I find adapting mentally to different versions frustrating.
My wife uses Ubuntu 14.04 LTS with Unity, which I find irritating, so the prospect of maintaining 3 different GUIs doesn't appeal much.
Currently, she is having difficulty accessing her webmail and now wants my help, and so it goes on :~\

---

