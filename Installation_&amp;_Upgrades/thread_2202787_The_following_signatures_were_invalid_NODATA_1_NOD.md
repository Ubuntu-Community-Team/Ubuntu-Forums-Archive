---
title: "The following signatures were invalid: NODATA 1 NODATA 2"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by jrmchess on 2014-01-31
I get this error ```
E: GPG error: http://deb.torproject.org precise Release: The following signatures were invalid: NODATA 1 NODATA 2
```

whenever I run this command: 
```
sudo apt-get update
```

I want to install the below software but always fail to do so:

1. ubuntu tweak
2. a world clock 
3. vb6 to run excel macros

I am really feeling frustrated using ubuntu and thinking of reverting to windows but I don't want to. Someboby please help me. Thanks

---

### Post by claracc on 2014-01-31
You problem is that the GPG key for the repository [http://deb.torproject.org](http://deb.torproject.org) precise Release you have added is incorrect.

Please, see this thread: [http://ubuntuforums.org/showthread.php?t=2053051](http://ubuntuforums.org/showthread.php?t=2053051) with workarounds and explanations why you obtain the GPG Key error.

---

### Post by fantab on 2014-01-31
I am not sure what causes that error but a possible fix is to enable 'Source code' in 'repositories'. 

Open Software Center-> Edit -> Software Sources -> enable (check) 'Source code'.

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jrmchess on 2014-02-01
> **fantab said:**
> I am not sure what causes that error but a possible fix is to enable 'Source code' in 'repositories'. 

Open Software Center-> Edit -> Software Sources -> enable (check) 'Source code'.

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

when I check 'source code' I get the message: 

> failed to download repository information
check your internet connection

E:GPG error: [http://deb.torproject.org](http://deb.torproject.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2 

---

### Post by fantab on 2014-02-01
Try changing the 'Server' to 'Main' in 'Software Sources' and try 'sudo apt-get update' again.

If that doesn't help either then try:
```
sudo apt-get install deb.torproject.org-keyring
```

---

### Post by jrmchess on 2014-02-02
> **fantab said:**
> Try changing the 'Server' to 'Main' in 'Software Sources' and try 'sudo apt-get update' again.

If that doesn't help either then try:
```
sudo apt-get install deb.torproject.org-keyring
```

I changed the server to main but got the this error, > failed to download repository information
check your internet connection

E:GPG error: [http://deb.torproject.org](http://deb.torproject.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2                       

I then did sudo apt-get update and got > Get:1 [http://deb.torproject.org](http://deb.torproject.org) precise Release.gpg [141 B]
Get:2 [http://deb.torproject.org](http://deb.torproject.org) precise Release [141 B]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://deb.torproject.org](http://deb.torproject.org) precise Release                                  
E: GPG error: [http://deb.torproject.org](http://deb.torproject.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

so I tried: 
sudo apt-get install deb.torproject.org-keyring but got > Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package deb.torproject.org-keyring
E: Couldn't find any package by regex 'deb.torproject.org-keyring'




My friend today told me that he had tried changing some settings some days back to install the tor browser on my computer but was unsuccessful. He realised this when I showed him your post containing > sudo apt-get install deb.torproject.org-keyring. He doesn't remember what settings he had tried to change but he is sure he followed exactly what was there on this site: [http://nithinaneeshsct06bt.blogspot.ae/2012/07/installing-vidalia-tor-in-ubuntu-1204.html](http://nithinaneeshsct06bt.blogspot.ae/2012/07/installing-vidalia-tor-in-ubuntu-1204.html)

Now I am too afraid to touch any of those settings. Can u please advise me what I can do to revert back? Thanks

---

### Post by jrmchess on 2014-02-06
can anyone help me please? Thanks

---

### Post by fantab on 2014-02-07
Post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by jrmchess on 2014-02-07
> **fantab said:**
> Post the output of:

```
cat /etc/apt/sources.list
```

here it is:

> # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise universe
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise multiverse
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-backports main restricted universe multiverse

deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-security main restricted
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-security universe
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main



---

### Post by fantab on 2014-02-07
For now, disable 'torproject' repository. You can do this from either 'Software Center' or by editing the above file directly...
'Software Center-> Edit-> Sources -> Other Software -> uncheck/deselect 
> deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main

Run:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by jrmchess on 2014-02-07
> **fantab said:**
> For now, disable 'torproject' repository. You can do this from either 'Software Center' or by editing the above file directly...
'Software Center-> Edit-> Sources -> Other Software -> uncheck/deselect 


Run:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

yes I have already tried this and it resolved the issue. Thanks

---

### Post by fantab on 2014-02-09
If you have disabled 'tor repository' and have 'tor' installed then you will not get any updates or fixes for it. The above is only a temporary fix....

---

### Post by jrmchess on 2014-02-09
> **fantab said:**
> If you have disabled 'tor repository' and have 'tor' installed then you will not get any updates or fixes for it. The above is only a temporary fix....

so what's the solution?

---

### Post by Claus7 on 2014-12-17
Hello,

I had the same problem with the OP, receiving the messages NO DATA 1 NO DATA 2 and similar.

I changed servers, repositories, I downloaded other keys, changed the sources.list file under the /etc/apt
to no avail.

Sometimes I was able to see that it started loading, yet sooner or later it stopped reporting this issue.

I order to solve it at that box I was (using wubi), the system administrator had to change some firewall options in order not to keep blocking the apt-get command.

Hope it helps for future reference,
Regards!

---

