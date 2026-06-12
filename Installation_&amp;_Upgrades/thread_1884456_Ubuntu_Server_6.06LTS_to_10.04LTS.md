---
title: "Ubuntu Server 6.06LTS to 10.04LTS"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by root.kev on 2011-11-21
Hi All,

I have recently been tasked with preparing the necessary steps to upgrade one of our older Ubuntu servers from its current 6.06LTS OS to 10.04 LTS.  I know that in order to do this upgrade I need to go to version 8 then then to 10, but since both 6, and 8 are now EOL, I'm having a bit of difficulty getting it to upgrade.  To prepare the upgrade I have done a P2V into an esxi vmserver.

I have modified my /etc/apt/sources.list to the folowing:

```
deb cdrom:[Ubuntu-Server 8.04.4 _Hardy Heron_ - Release i386 (20100121.3)]/ hardy main restricted

#EOL upgrade sources.list
#required
 deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
 deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
 deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

#optional
# deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```I have done an apt-get update and apt-get upgrade and now receive no needed updates for the packages that are installed.

The first thing that I tried was to do the cdrom upgrade.  I tried mounting both the alternate CD and the normal server CD.  When I do the sh /cdrom/cdromupgrade

I get an error at:
```
Calculating the changes

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

```My /var/log/dist-update/apt.log states the following:
```
Starting
Starting 2
Investigating initscripts
Package initscripts has broken dep on sysvinit
  Considering sysvinit 5102 as a solution to initscripts 106
  Holding Back initscripts rather than change sysvinit
 Try to Re-Instate initscripts
Done
Installing upstart as dep of system-services
Installing upstart-compat-sysv as dep of system-services
Starting
Starting 2
Investigating evms-ncurses
Package evms-ncurses has broken dep on evms
  Considering evms 10001 as a solution to evms-ncurses -2
  Removing evms-ncurses rather than change evms
Done
Installing tasksel as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing tasksel-data as dep of tasksel
Installing util-linux-locales as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)

Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop,
xubuntu-desktop or edubuntu-desktop package and it was not possible
to detect which version of Ubuntu you are running.
Please install one of the packages above first using synaptic or
apt-get before proceeding.

```Since this is a server install, with the server install disk(s) I an unsure as to why it is looking for a desktop package.

The main.log says basically the same thing:

```

2011-11-21 10:08:30,941 DEBUG entry '# deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse' was disabled (unknown mirror)
2011-11-21 10:08:30,941 DEBUG examining: 'deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse'
2011-11-21 10:08:30,943 DEBUG entry '# deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse' was disabled (unknown mirror)
2011-11-21 10:08:30,943 ERROR No valid mirror found
2011-11-21 10:08:35,884 DEBUG rewriteSourcesList()
2011-11-21 10:08:35,884 DEBUG examining: 'deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse'
2011-11-21 10:08:35,887 DEBUG entry '# deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse' was disabled (unknown dist)
2011-11-21 10:08:35,887 DEBUG examining: 'deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse'
2011-11-21 10:08:35,889 DEBUG entry '# deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse' was disabled (unknown dist)
2011-11-21 10:08:35,889 DEBUG examining: 'deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse'
2011-11-21 10:08:35,891 DEBUG entry '# deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse' was disabled (unknown dist)
2011-11-21 10:08:35,900 DEBUG AptCdrom.add() called with '/cdrom'
2011-11-21 10:08:36,043 DEBUG AptCdrom.add() returned: 1
2011-11-21 10:08:36,045 DEBUG running doUpdate() (showErrors=True)
2011-11-21 10:08:36,045 DEBUG doUpdate() will not use the network because self.useNetwork==false
2011-11-21 10:08:36,474 DEBUG Installing 'system-services' (priority in required set 'required' but not scheduled for install)
2011-11-21 10:08:36,506 DEBUG Installing 'startup-tasks' (priority in required set 'required' but not scheduled for install)
2011-11-21 10:08:36,521 DEBUG Installing 'upstart-logd' (priority in required set 'required' but not scheduled for install)
2011-11-21 10:08:36,533 DEBUG Running KeepInstalledSection rules
2011-11-21 10:08:36,536 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2011-11-21 10:08:36,536 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2011-11-21 10:08:36,536 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2011-11-21 10:08:36,536 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2011-11-21 10:08:36,536 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2011-11-21 10:08:36,536 DEBUG running hardyQuirks handler
2011-11-21 10:08:36,536 DEBUG running _checkAndRemoveEvms
2011-11-21 10:08:36,643 DEBUG Kernel uname: '2.6.24-26-server'
2011-11-21 10:08:36,744 DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'edubuntu-desktop', 'xubuntu-desktop', 'ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'gobuntu-desktop']' meta-pkgs installed
2011-11-21 10:08:36,768 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'

```If I just run a do-release-upgrade, it goes and gets the lucid.tar.gz file.  Not the required version 8 edition.  As well as failing as well:

```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be
caused by held packages.

```Has anyone tried to do this upgrade recently?  If so, how did you get it to work?  Thanks for any help!

---

### Post by zvacet on 2011-11-22
I don´t use server,but I think you can not skip releases.In your case it is about Hardy 8.04.So afaik your upgrade should look like this

6.06 > 8.04 > 10.04

---

### Post by root.kev on 2011-11-24
Was able to get the system updated using the steps laid out here: [http://ubuntuforums.org/showpost.php?p=11136745&postcount=1](http://ubuntuforums.org/showpost.php?p=11136745&postcount=1)

---

### Post by zvacet on 2011-11-29
Now you can upgrade to Lucid if you want to. :) See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

