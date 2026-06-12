---
title: "apt-get update - Failed to fetch/Some index files failed to download"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by toyoder on 2008-03-05
Greetings

This has been occurring for sometime now on a system I use.
My question is, why do I see the following after running apt-get update?
pawn@castle:~$ sudo su root
root@castle:~# apt-get update

<snipped>
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg
Hit [http://www.linuxmint.com](http://www.linuxmint.com) cassandra/ Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
302 Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
302 Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
<snipped>
Fetched 1335B in 2s (534B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists](http://medibuntu.sos-sts.com/repo/dists) ... ackages.gz <http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz> 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists](http://medibuntu.sos-sts.com/repo/dists) ... ackages.gz <http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz> 302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@castle:~#

Even better, how should I fix it??

Thx in advance!

---

### Post by taurus on 2008-03-05
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
And just so you know, you do not need to log in as root to update your machine.  Run it from your regular account as

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by toyoder on 2008-03-05
pawn@castle:~# cat /etc/apt/sources.list
## UBUNTU REPOSITORIES
## -------------------
##
## Feisty (Ubuntu 7.04)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
##
## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted universe multiverse
##
## Bug Fixes
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
##
## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
##
## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

                                   
## LINUX MINT REPOSITORIES
## -----------------------
##
## Cassandra (Linux Mint 3.0)
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) cassandra/
##
## Romeo (Linux Mint Unstable)
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/


## OTHER REPOSITORIES
## ------------------
##
## Canonical (RealPlayer10, Opera, DesktopSecure etc...) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
##
## Medibuntu (Codecs and extra applications)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
##
##Last.FM .deb apt repository 
deb [http://apt.last.fm/](http://apt.last.fm/) debian stable

---

### Post by taurus on 2008-03-05
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of this line.

```
**[COLOR="Blue"]#[/COLOR]**deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Save it and close gedit window.  Then run

```

sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
You should be good now.

---

