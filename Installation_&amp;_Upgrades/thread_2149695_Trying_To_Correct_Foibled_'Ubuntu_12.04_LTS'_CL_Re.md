---
title: "Trying To Correct Foibled 'Ubuntu 12.04 LTS' CL Release Upgrade"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by odoncaoa on 2013-05-29
Greetings,

I've been modifying a '**Ubuntu 12.04 (Precise Pangolin) LTS**' system for a while now. Always interested in the insight gained over the years when executing an *ux 'upgrade', I managed to to wander off into cross distibution conflicting territory. Not having gained total oversight of a manual release upgrade via 'apt', I've managed to partially upgrade the system to a workable '**Ubuntu 12.10 (Quantal Quetzal)**' runtime. The partially upgraded system was accomplished by adding lines which include '**quantal**' referrences to '**/etc/apt/sources.list**', (the final 2 lines) and executing 'sudo apt-get update', etc.

After a bit more investigation, I sense that it may be possible to actually correct this 'faux pas' via the execution of a '***Release Downgrade***'. That is, change any '***quantal***' referrences to '***precise***' in '**/etc/apt/sources.list**', and then: *  $ sudo apt-get update && apt-get dist-upgrade*

in order to make everything '**precise**' *_only_* again. Would it make sense to work with the existing '*/etc/apt/sources.list*', or do a similar operation with the  referrence '**sources.list**' presented at '*[http://ubuntuforums.org/showthread.php?t=1997718](http://ubuntuforums.org/showthread.php?t=1997718)*' ?

Cheers,
odoncaoa

P.S. Here are relevant statistics:

	Release:	Ubuntu 12.10 (quantal)
	Kernel:		3.2.0-44-generic-pae (#69-Ubuntu SMP Thu May 16 18:50:07 UTC 2013)
	gnome:		Unknown  (3.4.2 ?)
	CPU Model:	Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz x 4
	Frequency:	800 MHz
	L2 Cache:	3072

$ **uname -p -i**
   i686 i686

$ **lsb_release -cs**
   quantal

```
**/etc/apt/sources.list**

   # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
   
   # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
   # newer versions of the distribution.
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted multiverse
   
   ## Major bug fix updates produced after the final release of the
   ## distribution.
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse
   
   ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   ## team. Also, please note that software in universe WILL NOT receive any
   ## review or updates from the Ubuntu security team.
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
   
   ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   ## team, and may not be under a free licence. Please satisfy yourself as to 
   ## your rights to use the software. Also, please note that software in 
   ## multiverse WILL NOT receive any review or updates from the Ubuntu
   ## security team.
   
   ## N.B. software from this repository may not have been tested as
   ## extensively as that contained in the main release, although it includes
   ## newer versions of some applications which may provide useful features.
   ## Also, please note that software in backports WILL NOT receive any review
   ## or updates from the Ubuntu security team.
   
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted multiverse
   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
   
   ## Uncomment the following two lines to add software from Canonical's
   ## 'partner' repository.
   ## This software is not part of Ubuntu, but is offered by Canonical and the
   ## respective vendors as a service to Ubuntu users.
   deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
   deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
   
   ## This software is not part of Ubuntu, but is offered by third-party
   ## developers who want to ship their latest software.
   # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
   # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
   
   # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
   # newer versions of the distribution.
   
   ## Major bug fix updates produced after the final release of the
   ## distribution.
   
   ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   ## team. Also, please note that software in universe WILL NOT receive any
   ## review or updates from the Ubuntu security team.
   
   ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   ## team, and may not be under a free licence. Please satisfy yourself as to 
   ## your rights to use the software. Also, please note that software in 
   ## multiverse WILL NOT receive any review or updates from the Ubuntu
   ## security team.
   
   ## N.B. software from this repository may not have been tested as
   ## extensively as that contained in the main release, although it includes
   ## newer versions of some applications which may provide useful features.
   ## Also, please note that software in backports WILL NOT receive any review
   ## or updates from the Ubuntu security team.
   
   
   ## Uncomment the following two lines to add software from Canonical's
   ## 'partner' repository.
   ## This software is not part of Ubuntu, but is offered by Canonical and the
   ## respective vendors as a service to Ubuntu users.
   # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
   # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
   
   ## This software is not part of Ubuntu, but is offered by third-party
   ## developers who want to ship their latest software.
   
   ## Last.fm APT Repository
   ## If you use Ubuntu 12.04 ("precise"), please use:
   deb [http://apt.last.fm/debian](http://apt.last.fm/debian) precise main
   
   # [http://www.jedit.org/index.php?page=download](http://www.jedit.org/index.php?page=download)
   # To install jEdit via Debian Linux apt-get (this is also for any Debian based 
   # Distros like Ubuntu), add the following line to your /etc/apt/sources.list:
   deb [http://switch.dl.sourceforge.net/project/jedit](http://switch.dl.sourceforge.net/project/jedit) /
   
   # [http://packages.debian.org/sid/amd64/nodejs/download](http://packages.debian.org/sid/amd64/nodejs/download)
   # use a package manager like aptitude or synaptic to download and install
   # packages, instead of doing so manually via this website.
   # deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main
   
   # [http://slopjong.de/2012/10/31/how-to-install-the-latest-nodejs-in-ubuntu/](http://slopjong.de/2012/10/31/how-to-install-the-latest-nodejs-in-ubuntu/)
   # Installing the latest node.js on Ubuntu
   # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe
   # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted universe
   # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe
   # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main universe restricted
 
-----
  $ **pg /etc/apt/sources.list.d/medibuntu.list**
   ## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
   deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
   # deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
    
-----
**$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update**

   [sudo] password for odoncaoa: 
   --2013-05-29 12:35:05--  [http://www.medibuntu.org/sources.list.d/quantal.list](http://www.medibuntu.org/sources.list.d/quantal.list)
   Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
   Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
   HTTP request sent, awaiting response... 200 OK
   Length: 282 [text/plain]
   Saving to: `/etc/apt/sources.list.d/medibuntu.list'
   
   100%[======================================>] 282         --.-K/s   in 0s      
   2013-05-29 12:35:06 (16.9 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [282/282]
   
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
   Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
   Hit [http://apt.last.fm](http://apt.last.fm) precise Release.gpg
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net)  Release.gpg
   Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
   Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]
   Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal** Release.gpg [198 B]
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
   Hit [http://apt.last.fm](http://apt.last.fm) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net)  Release
   Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
   Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://apt.last.fm](http://apt.last.fm) precise/main i386 Packages
   Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net)  Packages
   Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [49.6 kB]
   Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
   Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Ign [http://apt.last.fm](http://apt.last.fm) precise/main Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
   Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
   Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg
   Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [631 kB]
   Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal** Release [7833 B]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net)  Translation-en
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
   Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal**/free i386 Packages [3237 B]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
   Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
   Get:13 [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal**/non-free i386 Packages [7196 B]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [206 kB]
   Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [14.9 kB]
   Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [23.6 kB]
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
   Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [3921 B]
   Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [4534 B]
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
   Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal**/free Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
   Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [279 kB]
   Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) **quantal**/non-free Translation-en
   Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
   Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
   Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages [4620 B]
   Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages [2375 B]
   Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [77.0 kB]
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en
   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en
   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en
   Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en [47.1 kB]
   Fetched 1460 kB in 20s (72.0 kB/s)
   Reading package lists...
   Reading package lists...
   Building dependency tree...
   Reading state information...
   medibuntu-keyring is already the newest version.
   0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
   1 not fully installed or removed.
   After this operation, 0 B of additional disk space will be used.
   Setting up js2-mode (0~20090723b-2) ...
   Install emacsen-common for emacs
   Install emacsen-common for emacs23
   install/js2-mode: Handling install for emacsen flavor emacs23
   Loading 00debian-vars...
   Loading /etc/emacs/site-start.d/20apel.el (source)...
   Loading /etc/emacs/site-start.d/50auto-complete-el.el (source)...
   Loading /etc/emacs/site-start.d/50autoconf.el (source)...
   Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
   Loading debian-ispell...
   Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
   Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
   Loading /etc/emacs/site-start.d/50flim.el (source)...
   Loading /etc/emacs/site-start.d/50js2-mode.el (source)...
   Loading /etc/emacs/site-start.d/50psvn.el (source)...
   Loading /etc/emacs/site-start.d/50python-docutils.el (source)...
   Loading /etc/emacs/site-start.d/50twittering-mode.el (source)...
   Loading /etc/emacs/site-start.d/50w3m-el.el (source)...
   Loading /etc/emacs/site-start.d/50wget-el.el (source)...
   Loading w3m-wget...
   Symbol's value as variable is void: export
   ERROR: install script from emacsen-common package failed
   dpkg: error processing js2-mode (--configure):
    subprocess installed post-installation script returned error exit status 1
   Errors were encountered while processing:
    js2-mode
   E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by sudo san on 2013-05-29
Why have you only changed so few repositories to quantal? The trick is to change them all to upgrade. You can do this easily with the command:
```
sudo sed -i 's/precise/quantal/g' '/etc/apt/sources.list'
```

From there you can then do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I dont think that you can actually downgrade Ubuntu through installing different packages as I experimented with a raring kernel in a quantal system. After changing the repos and installing the 3.8 development kernel, I changed the repos back and apt did not allow the downgrade of packages, because it is a lower version. That is why the command is called apt-get upgrad as it upgrades current packages to newer ones.

---

### Post by odoncaoa on 2013-05-30
> Why have you only changed so few repositories to quantal? The trick is to change them all to upgrade. You can do this easily with the command:

I modified only intended '**sources.list**' records, previous to intended upgrade of local repository because:

   1) I hadn't yet mastered the overall apt (et. al) approach admin procedure, 
   2) Was trying to avoid having to do so at this time, (to the degree possible)
   3) And wanted to walk as lightly as could be possible; having been
        bitten in the past whenever acquiescing to a '***balls to the wall***'
        **ux admin commitment*, whenever 1), and 2) WERE true ;^)

The idea was to just '*tip a toe in the commit*', try to just '*get over the committ line'*, and see what happened in the event the system wasn't absolutely in the state that '*it needed to be*' afterward. I hadn't enough **apt** (et. al) info prior to the change, still wanted to modify the system, (but for reasons other than 'official upgrade'); however in liue of, upgrades the WERE ACTUALLY BEING COMITTED TO (mplayer, cinammon, Windoze7 co-function), and weren't even on the *Official* upgrade procedural *map*!

Bottom line, I didn't have enough release upgrade admin info before the attempted procedure.

However, does it make sense to adopt the referrence '**sources.list**' presented at **[http://ubuntuforums.org/showthread.php?t=1997718](http://ubuntuforums.org/showthread.php?t=1997718)**, updating it for new stuff, and using it after 'normalizing' this system (killincoole) to either **precise**, _or_ **quantal** (in total)? It seems to hold referrences that this system might need for future attemped extensions, and currently is lacking.

Thanks for sharing your valuable experience, that's why the question was posed (again, I probably know) here. This is a '*top of the list*' place to acquire such insight; appreciated ;^)

Cheers,
odoncaoa

---

### Post by sudo san on 2013-05-31
Glad to help with information and also glad to hear that you are starting to 'open the hood' on apt to see what happens when an upgrade goes wrong. And of course, remember for next time that it is not possible to downgrade Ubuntu.
Sudo San

---

