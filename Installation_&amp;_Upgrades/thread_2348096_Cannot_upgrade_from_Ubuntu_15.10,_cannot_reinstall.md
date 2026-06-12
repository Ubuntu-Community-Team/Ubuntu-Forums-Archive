---
title: "Cannot upgrade from Ubuntu 15.10, cannot reinstall from DVD or USB"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by Tarhawk on 2016-12-31
I am stuck between a rock and a hard place.  

I cannot seem to upgrade from Ubuntu 15.10 to newest LTS.. it says it has failed to fetch repositories.   Nor will it boot from USB or DVD so that I can reinstall to the latest version.  I have been trying to figure out this problem for sometime and have had no luck despite trying every solution I can find on help forums. 

Details:

Computer -  Toshiba Satellite C55 B5196 I have windows and Ubuntu installed side by side and they boot and function normally.. though I rarely log into Windows
Ubuntu 15.10 LTS installed from DVD drive.  DVD drive still functions normally in both Windows and Ubuntu, USB ports still function normally in both windows and ubuntu.

I have tried changing the boot order for to both DVD and USB, and to boot under UEFI and the other setting (cannot remember off the top of my head... though when I switch this from its normal setting it fails to boot at all and goes to an error screen not recognizing or finding the boot location).

Internet and wireless connections work fine, so not a matter of network connectivity.

I have tried to switch the servers that it upgrades from and the repositories it says it cannot fetch and still no luck.  

I greatly appreciate the help or insight!

This is the error I get when I try to upgrade from the software center:


Failed to download repository information 

Check internet connection (though the connection works just fine)

```
W:Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/source/Sources](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/source/Sources](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```


This is the current source list:
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe multiverse restricted main #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe multiverse restricted main #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports restricted universe multiverse main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports restricted universe multiverse main #Added by software-properties


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-security restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-security universe multiverse restricted main #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-proposed universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-proposed universe multiverse restricted main #Added by software-properties
```

---

### Post by grahammechanical on 2016-12-31
Ubuntu 15.10 reached end of life on 4 February 2016. At some point after a release of Ubuntu reaches end of life the repositories for that release are closed and archived. They are moved to another server. The URLs are changed. This is why you are getting "failed to fetch" messages. You need to do an End of Life upgrade. You need to edit that sources lists file and change, for example

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily restricted main

to

> deb http;//old-releases.ubuntu.com/ubuntu wily restricted main

Do something similar for all the repositories. Also disable those PPAs. It is better to reinstall PPA software after an upgrade. Provided the author has upgraded the PPA to 16.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Failure to boot from a DVD or USB stick is another issue. I cannot help  with that as I do not have a UEFI motherboard. Except to say that on my  BIOS motherboard it is not enough to change boot order/priority. The  motherboard sees the USB stick with an OS on it as an external USB  drive. I have to change the order under hard drives. I have to  specifically direct the motherboard to boot from the USB stick as if the  machine had 2 (or in my case, 3) hard drives.

Regards
[URL="https://help.ubuntu.com/community/EOLUpgrades"]
[/URL]

---

### Post by TheFu on 2016-12-31
Did you run **do-release-upgrade**? 
The cmd and output would be helpful - not 500 lines of the same output, just enough to get the point across, please.
Also, please use "code tags" so things are easy to read.

And it should go without saying, but before doing any of this, backup everything so you can put it all back and try again. If you don't already have a backup method that you KNOW 100% can be restored, start there first.

---

### Post by Tarhawk on 2016-12-31
After quite a bit of time trying to work this problem, it finally decided to upgrade to 16.04.  Not gonna try to figure out why, just gonna move on with the new OS.  Mark this as solved.  Thank you for the insights.

---

### Post by TheFu on 2016-12-31
I suspect the EoL date for 15.04 was .... just looked it up ... end of July 2016. Normally there is some overlap between the N and N+1 releases support periods.  LTS gets 5 yrs for most users, but some desktop LTS releases only get 3 yrs.  

However, end of support means just that - end of support. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  Actually, I thought it was forum policy to no help with unsupported releases, though a moderator would need to say it.

**do-release-upgrades** removes all non-standard and PPA sources in hopes of making the upgrade safer.  PPAs sometimes get in the way. After the upgrade to a new release, you can manually add those back, assuming it is still necessary.

---

### Post by Tarhawk on 2016-12-31
I am not sure as to why it decided to complete the upgrade today with no problems.  Thank you for your help though.  I thought I had tried to convert source lists before but it must not have been successful.  The only thing I did differently today was that the software updater prompted me to update a few packages.  I went ahead and updated them with no problems encountered.  I encountered this before but I don´t recall the updates being successful.  After this it prompted me for a distribution upgrade which I went ahead with.  For whatever reason this time it completed the upgrade successfully.  Do not know if it is possible that the software upgrade successfully updated source list.  Whatever happened, after a couple of months trying to work this problem it seems to have resolved itself.  

Did not know about the no commenting on the forums for out of date distributions, my apologies.  

Is there some kind of diagnostic or output I can preform to determine why the upgrade was successful this time (in the event someone else has this problem)?

---

### Post by TheFu on 2016-12-31
a) having all packages up to date is important before doing a release upgrade.
b) using do-release-upgrade handles the "/etc/apt/sources*" stuff. If you manually do it, that could break the expected stuff.
c) support only supported releases is necessary to prevent very old distros causing support spin. Some of us are OCD here and would work for years to solve things, when the common, best answer, is upgrade. 
d) I don't know about any diagnostics besides looking through log files. That is the normal Unix method - check the logs.

---

