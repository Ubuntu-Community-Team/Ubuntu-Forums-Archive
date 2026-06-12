---
title: "Upgrade to 16.04 failed"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2016-11-14
Here is the screens I saw and (partial) wrote down (different popped windows are separated in the list with ----):

Welcome to Ubuntu 16.04 LTS 'Xenial Xerus'

The Ubuntu team is proud to announce Ubuntu 16.04 LTS 'Xenial Xerus'.

To see what's new in this release, visit:

  [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
Ubuntu is a Linux distribution for your desktop or server, with a fast and easy install, regular releases, a tight selection of excellent applications installed by default, and almost any other software you can imagine available through the network.

We hope you enjoy Ubuntu.

Feedback and Helping

If you would like to help shape Ubuntu, take a look at the list of ways you can participate at

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)
Your comments, bug reports, patches and suggestions will help ensure that our next release is the best release of Ubuntu ever. If you feel that you have found a bug please read:

  [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)
Then report bugs using apport in Ubuntu. For example:

  ubuntu-bug linux
will open a bug report in Launchpad regarding the linux package.

If you have a question, or if you think you may have found a bug but aren't sure, first try asking on the #ubuntu or #ubuntu-bugs IRC channels on Freenode, on the Ubuntu Users mailing list, or on the Ubuntu forums:

  [http://help.ubuntu.com/community/InternetRelayChat](http://help.ubuntu.com/community/InternetRelayChat)
  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
More Information

You can find out more about Ubuntu on our website, IRC channel and wiki. If you're new to Ubuntu, please visit:

  [http://www.ubuntu.com/](http://www.ubuntu.com/)
To sign up for future Ubuntu announcements, please subscribe to Ubuntu's very low volume announcement list at:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)



===========================================================
Upgrading Ubuntu to version 16.04
	Preparing to upgrade
	Setting new software channels
	Getting new packages
	Installing the upgrades
	Cleaning up
	Restarting the computer

-------------------------------
Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

-------------------------------
Do you want to start the upgrade?
69 packages not anymore supported by Canonical
37 packages removed
240 new packages to install
2161 packages going to be upgraded
45 min to download 1828 MB
Upgrade takes several hours


-------------------------------

Could not install '/var/cache/apt/archives/systemd_229-4ubuntu12_amd64.deb'

The upgrade will continue but the '/var/cache/apt/archives/systemd_229-4ubuntu12_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.

subprocess installed pre-removal script returned error exit status 2

-------------------------------

Could not install '/var/cache/apt/archives/systemd_229-4ubuntu12_amd64.deb'

The upgrade will continue but the '/var/cache/apt/archives/systemd_229-4ubuntu12_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.

pre-dependency problem - not installing systemd-sysv

--------------------------------

Could not install 'systemd-sysv'

The upgrade will continue but the 'systemd-sysv' package may not be in a working state. Please consider submitting a bug report about it.
package systemd-sysv is already installed and configured

--------------------------------

Configuring phpmyadmin
Perform upgrade on database for phpmyadmin with dbconfig-common

applying upgrade sql fo 4:4.4.13.1-1 -> 4:4.5.0.2-1

Error 1060 at line 28: Duplicate column name 'input_transformation'

untick Perform ...
Replacing config file /etc/dbconfig-common/phpmyadmin.conf with new version

--------------------------------

Could not install the upgrades
The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)

Processing was halted because there were too many errors.

---------------------------------

Upgrade complete
The upgrade has completed but there were errors during the upgrade process

---------------------------------


lsb_release -a
```
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
```

uname -a
```
Linux ronald-desktop 4.2.0-42-generic #49-Ubuntu SMP Tue Jun 28 21:26:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


So, how can we proceed???

---

### Post by Bashing-om on 2016-11-14
ELMIT; Ouch !

Sad that these things happen, generally because of getting in a hurry and the system not fully updated at the time of the release -upgrade.
> 
The upgrade has completed but there were errors during the upgrade process


Let's see what condition the condition is in.
Post back the outputs - Between Code Tags - of terminal commands:
```

cat /etc/issue
uname -r
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see where we go from here .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ELMIT on 2016-11-14
Thank you for replying, ... 

cat /etc/issue
```
Ubuntu 16.04.1 LTS \n \l

```

uname -r
```
4.2.0-42-generic

```

cat -n /etc/apt/sources.list
```
     1	# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://archive.ubuntu.com/ubuntu xenial main restricted
     6	deb-src http://archive.ubuntu.com/ubuntu xenial main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
    11	deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://archive.ubuntu.com/ubuntu xenial universe
    17	deb-src http://archive.ubuntu.com/ubuntu xenial universe
    18	deb http://archive.ubuntu.com/ubuntu xenial-updates universe
    19	deb-src http://archive.ubuntu.com/ubuntu xenial-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://archive.ubuntu.com/ubuntu xenial multiverse
    27	deb-src http://archive.ubuntu.com/ubuntu xenial multiverse
    28	deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
    29	deb-src http://archive.ubuntu.com/ubuntu xenial-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
    37	deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
    38	
    39	deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
    40	deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted
    41	deb http://archive.ubuntu.com/ubuntu xenial-security universe
    42	deb-src http://archive.ubuntu.com/ubuntu xenial-security universe
    43	deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
    44	deb-src http://archive.ubuntu.com/ubuntu xenial-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu wily partner
    51	# deb-src http://archive.canonical.com/ubuntu wily partner
    52	# deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main # disabled on upgrade to xenial
    53	# deb http://us.archive.ubuntu.com/ubuntu vivid main universe

```

tail -v -n +1 /etc/apt/sources.list.d/*
```
==> /etc/apt/sources.list.d/bitcoin-ubuntu-bitcoin-wily.list <==
# deb http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu wily main

==> /etc/apt/sources.list.d/bitcoin-ubuntu-bitcoin-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu wily main
# deb-src http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu wily main

==> /etc/apt/sources.list.d/dropbox.list <==
# deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-wily.list <==
# deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/eugenesan/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/eugenesan/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-wily.list.save <==
deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/eugenesan/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/giuspen-ubuntu-ppa-wily.list <==
# deb http://ppa.launchpad.net/giuspen/ppa/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/giuspen/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/giuspen-ubuntu-ppa-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/giuspen/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/giuspen/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/giuspen-ubuntu-ppa-wily.list.save <==
deb http://ppa.launchpad.net/giuspen/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/giuspen/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list <==
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list.distUpgrade <==
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list.save <==
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/talkplugin/deb/ stable main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/google-talkplugin.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/nemh-ubuntu-systemback-wily.list <==
# deb http://ppa.launchpad.net/nemh/systemback/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu wily main

==> /etc/apt/sources.list.d/nemh-ubuntu-systemback-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu wily main
# deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu wily main

==> /etc/apt/sources.list.d/nemh-ubuntu-systemback-wily.list.save <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu wily main
# deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu wily main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-wily.list <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-wily.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-wily.list <==
# deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main

==> /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-wily.list.save <==
deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-wily.list <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-wily.list.save <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/umang-ubuntu-indicator-stickynotes-wily.list <==
# deb http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu wily main

==> /etc/apt/sources.list.d/umang-ubuntu-indicator-stickynotes-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu wily main
# deb-src http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu wily main

==> /etc/apt/sources.list.d/umang-ubuntu-indicator-stickynotes-wily.list.save <==
deb http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu wily main
# deb-src http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu wily main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
```


sudo apt update
```
[sudo] password for elmit: 
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:8 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]                                                                                                                           
Get:10 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                                                                                                                      
Get:11 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                                                                                          
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [334 kB]                                                                                                                     
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [199 kB]                                                                                                                        
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                                                                                                
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [107 kB]                                                                                                                 
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [126 kB]                                                                                                                    
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,473 B]                                                                                                              
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [2,699 B]                                                                                                                 
Get:19 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [196 B]                                                                                                                    
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]                                                                                                              
Get:21 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [199 B]                                                                                                                
Get:22 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [194 B]                                                                                                              
Get:23 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [82.9 kB]                                                                                                                   
Get:24 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.9 kB]                                                                                                                      
Get:25 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]                                                                                                               
Get:26 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [7,406 B]                                                                                                               
Get:27 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [16.4 kB]                                                                                                                  
Get:28 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [200 B]                                                                                                               
Fetched 13.3 MB in 18s (718 kB/s)                                                                                                                                                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
```


apt list --upgradable
```
Listing... Done
systemd/xenial-updates 229-4ubuntu12 amd64 [upgradable from: 225-1ubuntu9.1]
systemd-sysv/xenial-updates 229-4ubuntu12 amd64 [upgradable from: 225-1ubuntu9.1]

```


sudo apt upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ifupdown : Breaks: systemd (< 228-3~)
            Breaks: systemd:i386 (< 228-3~)
 initscripts : Breaks: systemd (< 228-5ubuntu3)
               Breaks: systemd:i386 (< 228-5ubuntu3)
 libpam-systemd : Depends: systemd (= 229-4ubuntu12)
 systemd : Depends: libsystemd0 (= 225-1ubuntu9.1) but 229-4ubuntu12 is installed
 xserver-xorg-core : Breaks: systemd (< 226-4~)
                     Breaks: systemd:i386 (< 226-4~)
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2016-11-14
ELMITl over all;

Not as bad as I might have anticipated.
Keep in mind that the updater DID NOT enable your 3rd party PPAs, but that is not a factor at this time.

What is of concern is the version miss-matches .
Let's take the package manager's advise and see if we can eliminate a couple of these miss-matches .
See what results:
```

sudo apt update
sudo apt -f install

```

What ever the system will not fix for us, well we got to give the system a helping hand.

[INDENT][INDENT]make the system understand
[INDENT][INDENT][INDENT]what we want it to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ELMIT on 2016-11-14
Done!

One question came up, which /etc/apt/apt.conf.d/50unattended-upgrades I should use. I selected the new one.

apt list --upgradable
```
Listing... Done
systemd-sysv/xenial-updates 229-4ubuntu12 amd64 [upgradable from: 225-1ubuntu9.1]
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: There are 3 additional versions. Please use the '-a' switch to see them.
```

---

### Post by Bashing-om on 2016-11-14
ELMIT; Ho Kay;

As to that :
> 
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

run the system for a few days, and if no problems with the package management system then delete this old no longer needed file .
So presently what results with a new look?
```

sudo apt update
sudo apt upgrade

```
If all is clean then is time to go back at look at the PPAs and see what you might still want and see if they are still supported in xenial.

[INDENT][INDENT]it be over
[INDENT][INDENT][INDENT]when it is over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ELMIT on 2016-11-14
sudo apt update
```
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Fetched 95.7 kB in 1s (48.4 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

```

sudo apt upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  checkbox-ng gcc-4.9-base gcj-4.9-jre-lib gstreamer1.0-clutter heirloom-mailx iproute libamd2.3.1 libatk-wrapper-java libatk-wrapper-java-jni libbasicusageenvironment0 libbind9-90 libcamd2.3.1
  libcamel-1.2-52 libccolamd2.8.0 libcholmod2.1.2 libcolamd2.8.0 libcr0 libcuda1-352 libcuda1-361 libdns100 libebook-contacts-1.2-1 libecal-1.2-18 libedata-cal-1.2-27 libedataserver-1.2-20 libept1.4.16
  libgcj15 libgconf2-4 libgee2 libgif4 libgif4:i386 libglewmx1.10 libgnutls-deb0-28:i386 libgroupsock1 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtop2-10 libimobiledevice4 libisc95
  libisccc90 libisccfg90 libisl13 libjsoncpp0v5 liblinear1 liblivemedia23 libllvm3.6v5 libllvm3.6v5:i386 liblouis2 liblwres90 libnl-route-3-200 liborc-0.4-0:i386 libpgm-5.1-0 libpod-plainer-perl
  libpoppler52 libpth20 libqpdf13v5 libraw10 libsctp1 libsexy2 libsodium13 libumfpack5.6.2 libusageenvironment1 libusbmuxd2 libvpx2:i386 libvte-2.90-9 libvte-2.90-common libx265-59 libzmq3 lksctp-tools
  lsb-cxx lsb-desktop lsb-graphics lsb-languages lsb-multimedia nvidia-opencl-icd-352 nvidia-opencl-icd-361 php5-gd php5-json php5-mcrypt python-cffi python-characteristic python-colorama python-dbus-dev
  python-distlib python-ply python-pycparser python-requests python3-cffi python3-checkbox-ng python3-ply python3-pycparser qml-module-qtquick-dialogs qml-module-qtquick-localstorage
  qml-module-qtquick-privatewidgets qtdeclarative5-localstorage-plugin qtdeclarative5-qtfeedback-plugin qtdeclarative5-ubuntu-web-plugin telepathy-indicator unity-scope-audacious unity-scope-clementine
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque unity-scope-musique xchat-common
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  systemd-sysv
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/12.7 kB of archives.
After this operation, 11.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
(Reading database ... 355984 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_229-4ubuntu12_amd64.deb ...
Unpacking systemd-sysv (229-4ubuntu12) over (225-1ubuntu9.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu12) ...
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

```


The upgrade was (maybe) necessary for the wacom tablet. To see if the tablet is now recognized I click on System and then onto Wacom Tablet. However System does not open, and gives me these lines in syslog:
```

Nov 15 03:45:48 desktop kernel: [71128.897659] unity-control-c[23062]: segfault at 0 ip 00007fc3185a9549 sp 00007ffcfd44ea60 error 4 in libcogl.so.20.4.1[7fc318578000+b2000]
Nov 15 03:46:16 desktop kernel: [71157.129403] unity-control-c[23080]: segfault at 0 ip 00007f2ca53a9549 sp 00007ffc97cc49a0 error 4 in libcogl.so.20.4.1[7f2ca5378000+b2000]

```

I moved 50unattended-upgrades.ucf-old into a directory in my home folder and used sudo apt autoremove to get rid of the message. 

What are the next steps?

---

### Post by Bashing-om on 2016-11-14
ELMIT; Well !

Look'n good .
As to the wacom tablet; that is a subject for a new thread .

Let's take the package manager's advise and remove those "no longer required" :
```

sudo apt autoremove

```

Reboot the system a couple of times and see what the booting kernel is ( uname -r ) :
I do expect to see:
> 
4.4.0.47.50

Still stable and all happy ? ->
And next is for you to examine that list of PPAs and decide on what you want to keep, and then see if they are still supported.
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]oh happy times
[INDENT][INDENT][INDENT]clean up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

