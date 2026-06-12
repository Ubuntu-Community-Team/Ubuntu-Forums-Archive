---
title: "Update Manager Problem"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by gtg on 2008-06-14
When I open Update Manager (either prompted to by a little icon prompt or manually) and hit Check a message comes up stating that:

*******************************************
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
*******************************************

How do I correct this situation?

Thanks.

---

### Post by Pumalite on 2008-06-14
Post:
cat /etc/apt/sources.list

---

### Post by gtg on 2008-06-14
Result of  cat /etc/apt/sources.list

# 
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Pumalite on 2008-06-14
Try changing Server first:
System>Administration>Software Sources>Put a check on CD>Change Server to Main or US>Open up all your repos, including partner, updates, proposed, backports. Except src; unless you have a specific need for them. Try again.

---

### Post by avtolle on 2008-06-14
Be sure to "reload" the sources after making the changes suggested above before trying to upgrade again.

---

### Post by Pumalite on 2008-06-14
With the changes I suggested; you are 'forced' to reload.

---

### Post by gtg on 2008-06-14
I'm a little slow, so you might have to type a little slower. ;)

I opened Software Sources and changed the Download from: location from Server For United States to Main.  I reran Upgrade Manager with the same end result (although it seemed to take a bit longer).  I then went to Download from: Other and hit the button for Select Best Server.  It found one and I tried Upgrade Manager again, but to no avail.

So, what does it mean (and how do I do it) to "Open up all your repos, including partner, updates, proposed, backports. Except src"?  Is this done within Software Sources or via some sort of terminal command line operation?

Thanks for your patience.

---

### Post by avtolle on 2008-06-14
He means to check all the individual boxes before the names of the repositories which show up in Software Sources (except the one for the source code). IIRC, there are two places to look; the main page, and then the update page.

---

### Post by gtg on 2008-06-14
All boxes are (and have been) checked in the Downloadable from the Internet list except for the Source Code check box.  Thus, 4 boxes have check marks: Canonical-supported, Community-maintained, Proprietary drivers, and Software restricted by copyright.

---

### Post by Pumalite on 2008-06-14
In the GUI you get; make sure you have parter, proposed, updates and backports checked.

---

### Post by gtg on 2008-06-14
Under the Updates tab of Software Sources, I added checks to Pre-released updates and Unsupported updates.  Now, all the boxes under that tab are checked.  This resulted in a bunch (> 160 MB) of updates which seemed to install cleanly.  A restart of the system was indicated and performed.  

But, back in Update Manager, the original problem is still there.  :(

---

### Post by gtg on 2008-06-14
Here's what else is indicated in the Update Manager error screen:


****************************
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
****************************

---

### Post by avtolle on 2008-06-14
To cure the CD-ROM message, uncheck it as a source. I thought you were upgrading to 7.10, not 8.04, so the Hardy messages are not making any sense to me at the moment.

---

### Post by gtg on 2008-06-14
That's the key!!!    :)

No more error message.  I should provide more complete error information the first time.

I wasn't upgrading from/to 7.10 and/or 8.04.  When Hardy came out in April, I simply did a clean install and have been happily motoring along since (after a memory upgrade - Hardy seems more thirsty than Gutsy).  I've just been getting my updates as-expected and recently started getting this particular error message.  As you can tell from my questions, I'm not sophisticated enough to have changed anything on purpose - the error just kinda showed up one day.

But, thanks are extended to Pumalite and avtolle for patient guidance.

---

### Post by avtolle on 2008-06-14
Glad that suggestion helped you out; my apologies, however, for confusing your problem with another that I've been attempting to help with almost simultaneously (now, to the other thread to see if I posted something there meant for your problem). :-)

---

### Post by Dale Sexton on 2008-06-15
> **avtolle said:**
> To cure the CD-ROM message, uncheck it as a source. I thought you were upgrading to 7.10, not 8.04, so the Hardy messages are not making any sense to me at the moment.

Where do you uncheck it at?

Dale

---

### Post by Pumalite on 2008-06-15
System>Administration>Software Sources

---

