---
title: "all http repositories get 403 forbidden when downloading indexes"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by zzanzare on 2007-11-19
please help me, i am desperate. i have read about 100 other threads about 403 forbidden error, but nothing seems like what i am experiencing.. 

every time i go to System -> Administration -> Software Sources  and do whatever there, close it and hit Reload, i get this error message:

Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 403 Forbidden
http://cz.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 403 Forbidden

```

i have unchecked all third party repos, tried several other download servers, but still the same. this problem is troubling me since i upgraded to gutsy. i have read one opinion it could be caused by my ISP - not my case - tried on three different places

it only works when i choose an FTP download server. but a lot of third party repos dont have an ftp server..only http.

i am realy desperate.

this is my sources.list:
```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://cz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://cz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://cz.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://cz.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

deb http://cz.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

# deb http://ppa.launchpad.net/cschieli/ubuntu gutsy restricted multiverse #vmWare Player http://ppa.launchpad.net/cschieli/ubuntu
# deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse

```

thiis is output of apt-get update: (weird - no error here)
```

pete@ubuntu:~$ sudo apt-get update
Get:1 http://cz.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://cz.archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Get:2 http://cz.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://cz.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:3 http://cz.archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://cz.archive.ubuntu.com gutsy-security/main Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:4 http://cz.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://cz.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://cz.archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://cz.archive.ubuntu.com gutsy-backports Release
Hit http://cz.archive.ubuntu.com gutsy-updates Release                         
Hit http://cz.archive.ubuntu.com gutsy-security Release                        
Hit http://cz.archive.ubuntu.com gutsy Release                                 
Hit http://cz.archive.ubuntu.com gutsy-backports/main Packages                 
Hit http://cz.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://cz.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://cz.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://cz.archive.ubuntu.com gutsy-updates/main Packages
Hit http://cz.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://cz.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://cz.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://cz.archive.ubuntu.com gutsy-security/main Packages
Hit http://cz.archive.ubuntu.com gutsy-security/restricted Packages
Hit http://cz.archive.ubuntu.com gutsy-security/universe Packages
Hit http://cz.archive.ubuntu.com gutsy-security/multiverse Packages
Hit http://cz.archive.ubuntu.com gutsy/main Packages       
Hit http://cz.archive.ubuntu.com gutsy/restricted Packages 
Hit http://cz.archive.ubuntu.com gutsy/universe Packages   
Hit http://cz.archive.ubuntu.com gutsy/multiverse Packages 
Fetched 4B in 1s (2B/s)                                    
Reading package lists... Done

```

can someone please tell me what should i do? thank you for opinions..

---

### Post by Pumalite on 2007-11-19
Did you notice that all the refusals are for 'binary-i386'?
Post:
uname -r

---

### Post by zzanzare on 2007-11-20
hmm.. its not in the uname- mine is :
```

pete@ubuntu:~$ uname -r
2.6.22-14-generic

```

BUT.. (i am stupid i am stupid i am stupid).. you know how it works.. you are looking for solutions for two weeks and as soon as you start a new thread in the forum, you find a mistake in you synaptics settings.. :redface: i had a proxy set up in synaptics.. but the proxy only allows me to connect when i am at school. so these messages were not from repositories, but from the proxy. (i found out 10 minutes ago) sorry for the fuss..

---

### Post by Pumalite on 2007-11-20
Godspeed.

---

