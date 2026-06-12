---
title: "Update from APT repository doesn't work in fresh 10.04 install"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by phpfour on 2010-09-30
Hi Guys,

I've installed a fresh Ubuntu 10.04 in a new dev machine and have been trying to update the package list only to be frustrated. After the install, I went to terminal and did:

```
sudo apt-get update
```

with this result:

```

rbsadmin@daredevil:/var/log$ sudo apt-get update
[sudo] password for rbsadmin: 
Err http://us.archive.ubuntu.com lucid Release.gpg     
  Unknown date format [IP: 91.189.88.40 80]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Unknown date format [IP: 91.189.88.45 80]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Err http://us.archive.ubuntu.com lucid-security Release.gpg
  Unknown date format [IP: 91.189.88.46 80]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:1 http://us.archive.ubuntu.com lucid Release [57.2kB]
Ign http://us.archive.ubuntu.com lucid-updates Release   
Get:2 http://us.archive.ubuntu.com lucid-security Release [38.5kB]                                                                                          
Ign http://us.archive.ubuntu.com lucid/main Packages                                                                                                        
Ign http://us.archive.ubuntu.com lucid/restricted Packages                                                                                                  
Ign http://us.archive.ubuntu.com lucid/main Sources                                                                                                         
Ign http://us.archive.ubuntu.com lucid/restricted Sources                                                                                                   
Ign http://us.archive.ubuntu.com lucid/universe Packages                                                                                                    
Ign http://us.archive.ubuntu.com lucid/universe Sources                                                                                                     
Ign http://us.archive.ubuntu.com lucid/multiverse Packages                                                                                                  
Ign http://us.archive.ubuntu.com lucid/multiverse Sources                                                                                                   
Ign http://us.archive.ubuntu.com lucid-updates/main Packages                                                                                                
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com lucid-security/restricted Packages
Ign http://us.archive.ubuntu.com lucid-security/main Sources
Ign http://us.archive.ubuntu.com lucid-security/restricted Sources
Ign http://us.archive.ubuntu.com lucid-security/universe Packages
Ign http://us.archive.ubuntu.com lucid-security/universe Sources
Ign http://us.archive.ubuntu.com lucid-security/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-security/multiverse Sources
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com lucid-security/restricted Packages
Ign http://us.archive.ubuntu.com lucid-security/main Sources
Ign http://us.archive.ubuntu.com lucid-security/restricted Sources
Ign http://us.archive.ubuntu.com lucid-security/universe Packages
Ign http://us.archive.ubuntu.com lucid-security/universe Sources
Ign http://us.archive.ubuntu.com lucid-security/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-security/multiverse Sources
Err http://us.archive.ubuntu.com lucid/main Packages
  Unknown date format [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid/restricted Packages
  Unknown date format [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com lucid/main Sources
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com lucid/restricted Sources
  Unknown date format [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/universe Packages
  Unknown date format [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid/universe Sources
  Got a single header line over 360 chars [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid/multiverse Packages
  Bad header line [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid/multiverse Sources
  Bad header line [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid-updates/main Packages
  Bad header line [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid-updates/restricted Packages
  Bad header line [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid-updates/main Sources
  Bad header line [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid-security/main Packages
  Unknown date format [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com lucid-security/restricted Packages
  Got a single header line over 360 chars [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com lucid-security/main Sources
  Bad header line [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com lucid-security/restricted Sources
  Bad header line [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com lucid-security/universe Packages
  Connection failed [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com lucid-security/universe Sources
  Unknown date format [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com lucid-security/multiverse Packages
  Unknown date format [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com lucid-security/multiverse Sources
  Connection failed [IP: 91.189.88.46 80]
Fetched 95.7kB in 8min 52s (180B/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Unknown date format [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unknown date format [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Unknown date format [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unknown date format [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Got a single header line over 360 chars [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Bad header line [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Bad header line [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Bad header line [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  Got a single header line over 360 chars [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Unknown date format [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz  Unknown date format [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Connection failed [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.



```

I've tried to change servers but without any luck. At this moment my sources.list looks like this:

```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://bd.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse


```

I have:

[LIST]
[*] Tried different server
[*] Tried apt-get update && apt-get upgrade
[*] active Internet connection and there is no proxy involved (writing from the same machine)
[/LIST]

Can anybody help me out please ?

Regards,

**Emran**

---

### Post by sikander3786 on 2010-09-30
You've posted for the 1st time since you joined UF back in Jan 2008. Welcome! You seem to be the most satisfied Ubuntu user I've even seen on the forums. :-)

Did you try the Main server? Also check the time and date on your PC. Is it correctly synchronized? I am stumped by the error you received "Unknown date format".

---

### Post by phpfour on 2010-09-30
Hi Sikander,

Yes, I've been a satisfied user so far - it has been a very smooth road. I'm using Ubuntu as well as the Linux Mint variant successfully for around 2 years now.

Regarding the issue, I've tried the Main server but without any luck. The date/time won't synchronize as it can't install NTP for the same reason. I've set the timezone and made one date adjustment on the time settings.

Thanks 

Emran

---

