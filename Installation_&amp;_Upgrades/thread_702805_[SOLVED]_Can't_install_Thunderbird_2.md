---
title: "[SOLVED] Can't install Thunderbird 2"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by auddin2 on 2008-02-20
Hi, I'm using Gutsy and I can't install Thunderbird
I tried using Add/Remove Applications, but it said: 
"Mozilla Thunderbird Mail/News cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
I tried using Synaptic Package Manager, but it did not appear in the list
I tried downloading the archive from mozilla.com and running in the terminal, but it said: 
./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
Any other options I have?

Thanks

---

### Post by aysiu on 2008-02-20
**Step 1**
Close Add/Remove, Synaptic, and any other open programs.

**Step 2**
Open [a terminal](http://www.psychocats.net/ubuntu/terminal)

**Step 3**
In the terminal, paste these commands, one at a time: ```
cat /etc/issue
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install thunderbird
```

**Step 4**
Highlight everything in the terminal and paste the output of all the commands back in this thread. If you want to make it readable, put the output in [noparse]```
terminal output
```[/noparse] tags.

---

### Post by auddin2 on 2008-02-20
> **aysiu said:**
> cat /etc/issue
```
Ubuntu 7.10 \n \l
```

> cat /etc/apt/sources.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://www.getautomatix.com/apt gutsy main
```

> sudo apt-get update
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                
Ign http://www.getautomatix.com gutsy/main Translation-en_US
Get:2 http://www.getautomatix.com gutsy Release [6738B]
Hit http://www.getautomatix.com gutsy/main Packages
Fetched 6739B in 0s (20.0kB/s)
Reading package lists... Done
```


> sudo apt-get install thunderbird
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate
```

---

### Post by aysiu on 2008-02-20
The only two repositories you have enabled are the CD-ROM and Automatix. Neither repository set has Thunderbird in it.

I would suggest [getting a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#key) and then trying again.

---

### Post by auddin2 on 2008-02-20
Thanks.
I think what might have happened is, that my network connection went down for a while, and when I tried to do apt-get, it commented out of all the repository locations because it couldn't resolve them.

Now my hope in Ubuntu is restored....hopefully it will become more and more user-friendly as releases continue.  Once it minimizes the terminal aspect, then more and more users will be flocking to Ubuntu.

---

### Post by aysiu on 2008-02-20
I'm glad it worked out for you.

By the way, you don't really need the terminal to install Thunderbird. It's just that in a text-based forum where I am not standing over your shoulder, the terminal is the easiest way to solve the problem at hand. Can you imagine instead of you copying and pasting commands, you having to upload screenshots of System > Administration > Software Sources in order for me to see what repositories you have enabled? That would be ridiculous.

---

