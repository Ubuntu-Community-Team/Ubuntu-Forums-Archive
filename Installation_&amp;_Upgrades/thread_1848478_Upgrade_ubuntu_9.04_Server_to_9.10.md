---
title: "Upgrade ubuntu 9.04 Server to 9.10"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by dankdave on 2011-09-22
Hi all.  I'm beginning the long process of upgrading my server from 9.04 to a current release, starting with 9.04 -> 9.10.  I don't have graphics installed on my computer, nor do I want them.

I have tried following a few different wikis, starting with:

[HTML]https://help.ubuntu.com/community/UpgradeNotes[/HTML]

and followed by

[HTML]https://help.ubuntu.com/community/KarmicUpgrades[/HTML]

I changed my /etc/apt/sources.list file to include archived sources.  When I run do-release, the error I receive is

```
dankdave@IMBThinkCentre:~/upgrade_stuff$ sudo do-release-upgrade 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'jaunty' to 'lucid' is not supported with this tool. 

dankdave@IMBThinkCentre:~/upgrade_stuff$ 

```

Running 'sudo aptitude dist-upgrade' does nothing:

```

dankdave@IMBThinkCentre:~/upgrade_stuff$ sudo aptitude dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

dankdave@IMBThinkCentre:~/upgrade_stuff$ 

```

I downloaded an iso for 9.10 server, and tried following this wiki:

[HTML]http://askubuntu.com/questions/47807/how-do-i-upgrade-from-9-04-to-10-04-2[/HTML]

The problem with these directions are that I can't run gksu.

```

dankdave@IMBThinkCentre:~/upgrade_stuff$ sudo /media/cdrom/cdromupgrade 
can't load DistUpgradeViewGtk (No module named gtk)
can't load DistUpgradeViewKDE (No module named PyQt4.QtCore)

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Include latest updates from the Internet? 

The upgrade system can use the internet to automatically download the 
latest updates and install them during the upgrade. If you have a 
network connection this is highly recommended. 

The upgrade will take longer, but when it is complete, your system 
will be fully up to date. You can choose not to do this, but you 
should install the latest updates soon after upgrading. 
If you answer 'no' here, the network is not used at all. 

Continue [Yn] y
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Removing leading `/' from member names
can't load DistUpgradeViewGtk (No module named gtk)
can't load DistUpgradeViewKDE (No module named PyQt4.QtCore)

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'jaunty' to 'lucid' is not supported with this tool. 

dankdave@IMBThinkCentre:~/upgrade_stuff$

```

Any suggested reading or something simple I am missing?  Thanks in advance.

---

### Post by zvacet on 2011-09-22
See if [this]("https://help.ubuntu.com/community/EOLUpgrades") can be of any help to you.

---

### Post by dankdave on 2011-09-22
> **zvacet said:**
> See if [this]("https://help.ubuntu.com/community/EOLUpgrades") can be of any help to you.

I forgot to mention I updated my /etc/apt/sources.list to point to legit repositories.  The current contents of that file are:

```

# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ jaunty universe
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty universe
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://old-releases.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

#deb http://old-releases.security.ubuntu.com/ubuntu jaunty-security main restricted
#deb-src http://old-releases.security.ubuntu.com/ubuntu jaunty-security main restricted
#deb http://old-releases.security.ubuntu.com/ubuntu jaunty-security universe
#deb-src http://old-releases.security.ubuntu.com/ubuntu jaunty-security universe
#deb http://old-releases.security.ubuntu.com/ubuntu jaunty-security multiverse
#deb-src http://old-releases.security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by dankdave on 2011-09-25
I've decided to perform a clean install from a new disk, so I'd like to close this thread.

I'm not sure if I'm supposed to mark this as "solved", because reinstalling the OS doesn't count as a "solution".  I was however, impressed that the new server had an option of keeping the old partition, which included saving my entire home directory.  Props to the development team!  This saves me the time of moving the files I  backed up back into my home directory.

---

### Post by oldos2er on 2011-09-25
Thread closed at OP's request.

---

