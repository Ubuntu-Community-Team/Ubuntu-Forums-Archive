---
title: "Update Manager problems"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by fiver22 on 2008-10-27
Hello,
       My Update notification keeps showing me a triangle w/ an exclamation mark: I click it and check for updates and it gives me the following error messages:

--“The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.”
--“Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs”
--“Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs”
--“Some index files failed to download, they have been ignored, or old ones used instead.”

What can I do to fix this? -what might I have done to cause this? (I recently used Synaptic to completely remove some software -could that be it?)
Thanks very much for your time,
                                                     fiver22.

---

### Post by oldos2er on 2008-10-27
Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by fiver22 on 2008-10-27
> **oldos2er said:**
> Can you post the output of "cat /etc/apt/sources.list"?

Wow,
    Thanks for the quick reply, oldos2er. Here is what you asked for (I hope):

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy main restricted
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates main restricted
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy universe
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy universe
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates universe
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy multiverse
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy multiverse
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates multiverse
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security main restricted
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security main restricted
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security universe
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security universe
deb [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security multiverse
deb-src [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) hardy-security multiverse

---

### Post by oldos2er on 2008-10-27
Go to System, Administration, Software Sources, under the 'Third party software' tab uncheck the box in front of 'cdrom:'. Then reload, and try checking for updates again.

---

