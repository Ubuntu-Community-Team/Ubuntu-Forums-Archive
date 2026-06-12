---
title: "Torproject PPA"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by jrmchess on 2014-02-07
I have been getting this error ```
E: GPG error: http://deb.torproject.org precise Release: The following signatures were invalid: NODATA 1 NODATA 2
``` whenever I try to upgrade or update. I have the following thread [http://ubuntuforums.org/showthread.php?t=2202787](http://ubuntuforums.org/showthread.php?t=2202787) open for this issue but have not got any satisfactory response so I would like to reinstall or repair ubuntuto take it back to its initial settings. How do I do this? Thanks

---

### Post by TheFu on 2014-02-07
[https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) explains how to install the PPA and signatures.
I would check where the current PPA line is under /etc/apt/ . It is there somewhere.

---

### Post by jrmchess on 2014-02-07
> **TheFu said:**
> [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) explains how to install the PPA and signatures.
I would check where the current PPA line is under /etc/apt/ . It is there somewhere.

I am new to ubuntu and I really don't know what ppa and signatures are. Can u please explain it step by step? thanks

---

### Post by TheFu on 2014-02-07
> **jrmchess said:**
> I am new to ubuntu and I really don't know what ppa and signatures are. Can u please explain it step by step? thanks

I can't explain it any better than that web link does.  You want option 2.

---

### Post by jrmchess on 2014-02-07
> **TheFu said:**
> I can't explain it any better than that web link does.  You want option 2.

but the link u gave me has information on the tor browser...:confused:

---

### Post by TheFu on 2014-02-07
The PPA giving you the error is coming from that project. Follow those instructions to fix it.
OR
remove the PPA line from your system. The line/file is somewhere under /etc/apt/.  Only you know where it is since it was most likely manually added.

---

### Post by jrmchess on 2014-02-07
> **TheFu said:**
> The PPA giving you the error is coming from that project. Follow those instructions to fix it.
OR
remove the PPA line from your system. The line/file is somewhere under /etc/apt/.  Only you know where it is since it was most likely manually added.

below is the output from the following: ```
cat /etc/apt/sources.list
```. Is it possible for u to tell me what exactly I have to delete. I had previosuly tried to install the tor browser using instuctions from the this website: [http://nithinaneeshsct06bt.blogspot.ae/2012/07/installing-vidalia-tor-in-ubuntu-1204.html](http://nithinaneeshsct06bt.blogspot.ae/2012/07/installing-vidalia-tor-in-ubuntu-1204.html) but was unsuccessful. I have now installed tor directly by downloading the setup files from the tor site and tor is working fine now. I am a little concerned that if I delete entries my tor browser would stop working. thanks


```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise universe
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise multiverse
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-backports main restricted universe multiverse

deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-security main restricted
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-security universe
deb http://ftp.tudelft.nl/archive.ubuntu.com/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://deb.torproject.org/torproject.org precise main
deb-src http://deb.torproject.org/torproject.org precise main



```

---

### Post by jrmchess on 2014-02-07
> **TheFu said:**
> The PPA giving you the error is coming from that project. Follow those instructions to fix it.
OR
remove the PPA line from your system. The line/file is somewhere under /etc/apt/.  Only you know where it is since it was most likely manually added.

Thanks. I went to software centre and unchecked the options for the tor browser. updates are working now.

---

