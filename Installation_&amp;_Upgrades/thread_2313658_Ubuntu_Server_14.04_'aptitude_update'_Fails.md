---
title: "Ubuntu Server 14.04 'aptitude update' Fails"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by accounts0 on 2016-02-14
Hi,

When I run 'aptitude update' I get the following error:
```

[FONT=monospace][COLOR=#000000]# aptitude update && aptitude upgrade[/COLOR]
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://security.ubuntu.com trusty-security Release.gpg
Ign http://security.ubuntu.com trusty-security Release
Ign http://security.ubuntu.com trusty-security/main amd64 Packages/DiffIndex
Err http://security.ubuntu.com trusty-security/main amd64 Packages
Err http://security.ubuntu.com trusty-security/main amd64 Packages
Err http://security.ubuntu.com trusty-security/main amd64 Packages
Err http://security.ubuntu.com trusty-security/main amd64 Packages                                                                      
Err http://security.ubuntu.com trusty-security/main amd64 Packages                                                                      
  Undetermined Error [IP: 91.189.91.24 80]                                                                                              
48% [Working]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages: Undetermined Error 
[IP: 91.189.91.24 80]                                                                                                                   
E: Some index files failed to download. They have been ignored, or old ones used instead.                                               
E: Couldn't rebuild package cache  [/FONT]
```

[FONT=monospace]Is there something going on right now? Why is this happening?
[/FONT]

---

### Post by accounts0 on 2016-02-14
Here's my sources.list:

```
# 

# deb cdrom:[Ubuntu-Server 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted


#deb cdrom:[Ubuntu-Server 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
#deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main


# AIRTIME:
deb http://apt.sourcefabric.org/ trusty main
```

---

### Post by accounts0 on 2016-02-14
And I can ping it:

```
[FONT=monospace][COLOR=#000000] ping -c3 security.ubuntu.com[/COLOR]
PING security.ubuntu.com (91.189.92.201) 56(84) bytes of data.
64 bytes from urayuli.canonical.com (91.189.92.201): icmp_seq=1 ttl=53 time=77.9 ms
```
[/FONT]

---

### Post by accounts0 on 2016-02-14
Hi,

I have problems with aptitude, as detailed in this [1] post. Apparently it's causing such problems that I'm unable to install anything.

I need help to resolve these errors [2].

Here's my 'sources.list': [3]

Please can someone help?

Thanks.



[1]
[http://ubuntuforums.org/showthread.php?t=2313658&p=13440067#post13440067](http://ubuntuforums.org/showthread.php?t=2313658&p=13440067#post13440067)

[2]

```

[COLOR=#000000][FONT=Consolas]Ign [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty ReleaseErr [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty/main amd64 
PackagesErr [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty/main amd64 
PackagesErr [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty/main amd64 
PackagesErr [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty/main amd64 
PackagesErr [/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#000000][FONT=Consolas] trusty/main amd64 
Packages  Undetermined Error [IP: 91.189.92.152 80]
46% [Working]W: Failed to fetch [/FONT][/COLOR][http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages:](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages:)[COLOR=#000000][FONT=Consolas] Undetermined Error [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache
root@SteelDeck:/srv/airtime/stor# aptitude install mc
The following NEW packages will be installed:  
libssh2-1{a} mc mc-data{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 1,653 kB of archives. After unpacking 7,166 kB will be used.
Do you want to continue? [Y/n/?] 
Err [/FONT][/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000][FONT=Consolas] trusty/universe libssh2-1 amd64 1.4.3-2  
server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
0% [Working]E: Failed to fetch [/FONT][/COLOR][http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libssh2/libssh2-1_1.4.3-2_amd64.deb:](http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libssh2/libssh2-1_1.4.3-2_amd64.deb:)[COLOR=#000000][FONT=Consolas] server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none[/FONT][/COLOR]
```

[3]
```

# 


# deb cdrom:[Ubuntu-Server 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted


#deb cdrom:[Ubuntu-Server 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
#deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main


# AIRTIME:
deb http://apt.sourcefabric.org/ trusty main
```

---

### Post by lisati on 2016-02-14
Threads merged.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by accounts0 on 2016-02-14
> **lisati said:**
> Threads merged.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

sorry, thanks

---

