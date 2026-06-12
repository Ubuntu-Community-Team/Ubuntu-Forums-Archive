---
title: "Problems with sudo aptitude update"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by markusg on 2008-05-20
Hi, just recently I have experienced problem in updating
and upgrading my Ubuntu 7.10 dist. This is the output when
running "sudo aptitude update"

```
sudo aptitude update 
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_AU
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_AU
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_AU
Ign http://archive.ubuntu.com gutsy/universe Translation-en_AU
Get:2 http://archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_AU
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_AU
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_AU
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_AU
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-security Release
Get:3 http://archive.ubuntu.com gutsy/main Packages [1075kB]
99% [3 Packages bzip2 0] [Waiting for headers]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy/main Packages
  Sub-process bzip2 returned an error code (1)
Get:4 http://archive.ubuntu.com gutsy/restricted Packages [7664B]
Get:5 http://archive.ubuntu.com gutsy/multiverse Packages [158kB]
92% [4 Packages bzip2 0] [5 Packages 53262/158kB 33%]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy/restricted Packages
  Sub-process bzip2 returned an error code (1)
Get:6 http://archive.ubuntu.com gutsy/universe Packages [4065kB]
27% [5 Packages bzip2 0] [6 Packages 108284/4065kB 2%]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy/multiverse Packages
  Sub-process bzip2 returned an error code (1)
Get:7 http://archive.ubuntu.com gutsy-security/main Packages [94.9kB]
98% [6 Packages bzip2 0] [7 Packages 2166/94.9kB 2%]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy/universe Packages
  Sub-process bzip2 returned an error code (1)
Get:8 http://archive.ubuntu.com gutsy-security/restricted Packages [14B]
Get:9 http://archive.ubuntu.com gutsy-security/multiverse Packages [2880B]
Get:10 http://archive.ubuntu.com gutsy-security/universe Packages [64.3kB]
99% [7 Packages bzip2 0]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy-security/main Packages
  Sub-process bzip2 returned an error code (1)
99% [8 Packages bzip2 0]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy-security/restricted Packages
  Sub-process bzip2 returned an error code (1)
99% [9 Packages bzip2 0]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy-security/multiverse Packages
  Sub-process bzip2 returned an error code (1)
99% [10 Packages bzip2 0]bzip2: File 'myisam.log' not found (Errcode: 2)
Err http://archive.ubuntu.com gutsy-security/universe Packages
  Sub-process bzip2 returned an error code (1)
Fetched 5468kB in 5s (1015kB/s)
Reading package lists... Done

```

Has anybody had the same problem or know how so solve this one?

---

### Post by PmDematagoda on 2008-05-20
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Kevbert on 2008-05-20
Try using a different download server.  Go to System-Administration-Software Sources and select a server near you location.  Have you tried ```
sudo apt-get update
``` instead.  Hopefully this should help.

---

### Post by markusg on 2008-05-20
Thanks for the replyes. I have tried different servers, and also
used the "Select best server" feature in Sys-admin-sw sources.

This is my sources.list
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe


```

---

### Post by markusg on 2008-05-22
Anymore ideas, someone?

---

### Post by markusg on 2008-05-25
Bumping this again. Seems like theres something wrong
with my mysql or bzip2. Just running 'bzip2' gives me this:
```
bzip2: File 'myisam.log' not found (Errcode: 2)
```

---

### Post by PmDematagoda on 2008-05-26
Try and reinstall bzip2 with:-
```
sudo apt-get install --reinstall bzip2
```

---

### Post by markusg on 2008-05-26
> **PmDematagoda said:**
> Try and reinstall bzip2 with:-
```
sudo apt-get install --reinstall bzip2
```

Hey, thanks for the tip!
Had to manually install the bzip2 deb file, and fix some
broken packages in synaptic. Now i can upgrade again!

---

