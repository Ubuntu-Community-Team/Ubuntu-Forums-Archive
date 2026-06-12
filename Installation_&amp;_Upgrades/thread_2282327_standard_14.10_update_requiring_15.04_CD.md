---
title: "standard 14.10 update requiring 15.04 CD"
date: 2015-06-13
forum: Installation &amp; Upgrades
---

### Post by Aero_Nexcom on 2015-06-13
why does the latest 14.10 updates require the 15.04 CD.
I have not made any attempt to upgrade to 15.04 on this machine.
In doing my standard updates on 14.10, the system wants to install 2 pkg that both require 15.04.
the update pkgs are 

Broadcom 802.11 Linux STA wireless driver source
Dynamic Kernel Module Support Framework

Is this an error in the update routines?

---

### Post by coffeecat on 2015-06-13
The answer is - 14.10 does not require the 15.04 CD unless you have made a change to your sources. It looks as though you may have used the 15.04 CD to install the Broadcom wireless driver. Did you do this at any time?

Let's have a look at your sources.list. Post the output of this terminal command:

```
cat /etc/apt/sources.list
```

You can copy and paste the lengthy output by highlighting the output in the terminal with the mouse -> right-click -> copy, and then paste. Please post the output between [noparse]```
 and 
```[/noparse] tags. You can do this in the advanced editor by highlighting all the output and clicking on the toolbar icon that looks similar to a #.

---

### Post by Aero_Nexcom on 2015-06-13
this is the output from the command cat /etc/apt/sources.list
this machine has been thru multiple upgrades of operating system.

```
 # deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)]/ vivid main restricted
deb http://us.archive.ubuntu.com/ubuntu/ utopic main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic main restricted universe


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ utopic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted multiverse universe


deb http://security.ubuntu.com/ubuntu utopic-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu utopic-security main restricted universe
deb http://security.ubuntu.com/ubuntu utopic-security multiverse
deb-src http://security.ubuntu.com/ubuntu utopic-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu utopic partner
deb-src http://archive.canonical.com/ubuntu utopic partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main
deb http://www.ubnt.com/downloads/unifi/distros/deb/ubuntu ubuntu ubiquiti # disabled on upgrade to saucy disabled on upgrade to trusty disabled on upgrade to utopic


## adds the SUSI OBS for cross compilation of Bareos to windows
##Tizen Tools (13.10 exists for first but not OBS light below
##deb http://download.tizen.org/tools/latest-release/Ubuntu_12.04/ ./
##OBS Light
##deb http://download.opensuse.org/repositories/devel:/OBS:/Light:/Stable/xUbuntu_12.04/ ./



```

---

### Post by Aero_Nexcom on 2015-06-13
Thanks coffeecat for the hint.
Appearently I hit upgrade one time and then stopped the upgrade. It left the first line 
deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)]/ vivid main restricted
I have commented this line and it seems to have fixed the request and no longer wants to update those pkgs.

not sure how to indicate this is solved

Thanks again.

---

### Post by ajgreeny on 2015-06-13
Go to the **Thread Tools** menu at the top for a **Mark as solved** option.

---

