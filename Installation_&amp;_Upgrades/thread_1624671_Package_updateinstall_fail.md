---
title: "Package update/install fail"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by Trevski13 on 2010-11-18
So I've been looking around the web and haven't found anything very conclusive...

long story short, I can't install ***anything*** which sucks.

I'm currently running Ubuntu 8.10 (I didn't upgrade for various reasons)

Here's my what I know:

If I run sudo apt-get update I get
```
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com intrepid Release.gpg                                                                                                       
Ign http://wine.budgetdedicated.com intrepid Release.gpg                                                                                                    
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US                        
Ign http://archive.canonical.com intrepid/partner Translation-en_US                        
Ign http://us.archive.ubuntu.com intrepid Release.gpg                                      
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                           
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US                     
Hit http://archive.canonical.com intrepid Release                                          
Ign http://wine.budgetdedicated.com intrepid Release                                       
Hit http://deb.opera.com stable Release.gpg                                                
Ign http://deb.opera.com stable/non-free Translation-en_US                                 
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US                       
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security Release.gpg
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US                                
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US              
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com intrepid Release                                          
Ign http://wine.budgetdedicated.com intrepid/main Packages                                                       
Ign http://dl.google.com stable/main Translation-en_US                                                           
Hit http://archive.canonical.com intrepid/partner Packages                                 
Ign http://us.archive.ubuntu.com intrepid-updates Release                                  
Ign http://us.archive.ubuntu.com intrepid-security Release                                 
Hit http://deb.opera.com stable Release                                                    
Err http://wine.budgetdedicated.com intrepid/main Packages                                 
  404 Not Found
Ign http://us.archive.ubuntu.com intrepid/main Sources               
Ign http://us.archive.ubuntu.com intrepid/restricted Sources         
Get:2 http://dl.google.com stable Release [2544B]
Ign http://us.archive.ubuntu.com intrepid/main Packages
Ign http://us.archive.ubuntu.com intrepid/restricted Packages
Ign http://us.archive.ubuntu.com intrepid/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid/universe Sources
Ign http://us.archive.ubuntu.com intrepid/universe Packages
Ign http://us.archive.ubuntu.com intrepid/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-updates/main Packages      
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://deb.opera.com stable/non-free Packages                    
Ign http://us.archive.ubuntu.com intrepid-updates/main Sources       
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-updates/universe Sources
Ign http://us.archive.ubuntu.com intrepid-updates/universe Packages
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-security/main Packages
Ign http://us.archive.ubuntu.com intrepid-security/restricted Packages
Get:3 http://dl.google.com stable/main Packages [1082B]              
Ign http://us.archive.ubuntu.com intrepid-security/restricted Sources
Ign http://us.archive.ubuntu.com intrepid-security/main Sources
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-security/universe Sources
Ign http://us.archive.ubuntu.com intrepid-security/universe Packages
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Packages
Err http://us.archive.ubuntu.com intrepid/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Hit http://deb.opera.com stable/non-free Packages
Err http://us.archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Fetched 3815B in 1s (3752B/s)
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and if I write... sudo apt-get install mplayer (for example) I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  scim-modules-table libticonv2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ttf-dejavu ttf-dejavu-extra
Suggested packages:
  w32codecs libdvdcss mplayer-doc ladspa-sdk
The following NEW packages will be installed:
  mplayer ttf-dejavu ttf-dejavu-extra
0 upgraded, 3 newly installed, 0 to remove and 8 not upgraded.
Need to get 7349kB of archives.
After this operation, 16.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ttf-dejavu-extra ttf-dejavu mplayer
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com intrepid/main ttf-dejavu-extra 2.25-1
  404 Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com intrepid/main ttf-dejavu 2.25-1
  404 Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com intrepid/multiverse mplayer 2:1.0~rc2-0ubuntu17
  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.25-1_all.deb  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.25-1_all.deb  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc2-0ubuntu17_i386.deb  404 Not Found [IP: 91.189.88.30 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

The contents of my /ect/apt/sources.list is:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
```

Any help would be greatly appreciated.

Just let me know if there's anything else you need and I'll get it right to you.

---

### Post by sikander3786 on 2010-11-18
You are using 8.10 and support for that ended long time ago.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The repositories have been shut down.

Go for clean install of some newer version of Ubuntu, 10.04 or 10.10.

Good Luck!

---

### Post by rondackcpu on 2010-11-18
Well, not completely shut down.  Just not being upgraded any more. they are available as last updated in a section called "old releases".  Best to google for information about "ubuntu old releases".

CRS

---

### Post by Trevski13 on 2010-11-18
> Well, not completely shut down. Just not being upgraded any more. they are available as last updated in a section called "old releases". Best to google for information about "ubuntu old releases".

Yeah I finally found it, basically you just have to replace all instances of
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
with 
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

in /etc/apt/sources.list

easy enough

Thanks,

> Go for clean install of some newer version of Ubuntu, 10.04 or 10.10
Oh I'd love to, but I don't have enough free time at the moment to fiddle and get everything to work correctly (it took long enough with this version)

Edit: corrected typo "ect" instead of "etc"

---

### Post by jefelex on 2010-11-21
> **Trevski13 said:**
> Yeah I finally found it, basically you just have to replace all instances of
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
with 
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

in /etc/apt/sources.list

easy enough

Thanks,


Oh I'd love to, but I don't have enough free time at the moment to fiddle and get everything to work correctly (it took long enough with this version)

Edit: corrected typo "ect" instead of "etc"

I have various computers at my home - one with 8.10, one with 8.04, one with 9.04, one with 10.04 (this computer - my main one) and one with 10.10 - I actually like 8.10 the best out of all of them, for the configurability applications and user interface.  I know that Gnome hasn't changed much, but the administration apps are much much better in 8.10 than in any other release of Ubuntu (IMHO) (I've been using Ubuntu since 7.10)  The whole issue is that new newest and greatest Ubuntu is getting just like MSDOS winderz 7 etc - the latest release assumes that more and more processing power is available - take the system monitor applet for instance - the newest one in 10.10 is great, but it could never run on my old compaq laptop, since it would require too much resource.  now I could just shut it off, but then I wouldn't have access to it (on the laptop) The old 8.10 basic system monitor applet works great on the old laptop

I think the old is not necessarily inferior, nor do I think the new is superior since it is new! :-)

my 2 cents!
John

---

