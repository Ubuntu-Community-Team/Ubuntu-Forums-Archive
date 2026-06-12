---
title: "Ubuntu Software Center Not Allowing Downloads"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Kondry on 2011-04-05
I'm trying to install new programs from the Ubuntu Software Center, but I always get errors such as "Check your internet connection"

I have tried these steps :
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the  first place, but whatever. Hope it helps somebody browsing, since at  this moment, this is google's #1 result for the error message.

Didn't work, all that did was replace the download button, with "Use This Source"

Can anyone help me?

---

### Post by mörgæs on 2011-04-05
If you boot the machine, can you install the same packages through Synaptic?

---

### Post by Kondry on 2011-04-05
> **mörgæs said:**
> If you boot the machine, can you install the same packages through Synaptic?

No, I am not able to install the packages through Synaptic.

---

### Post by Kondry on 2011-04-07
BUMP, still need help with this guys.

---

### Post by oldos2er on 2011-04-07
What type of internet connection do you have? Is it working correctly? Can you run **cat /etc/apt/sources.list** and post the output here?

---

### Post by shimrodmimir on 2011-04-07
I've been having exactly the same problem for a couple of days now, can't even update properly. Other PPA's work fine, but the amd64 PPA for ubuntu does not.

cat /etc/apt/sources.list gives me:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by Inferius on 2011-08-26
I recently had the same problem, but solved it by changing the download mirror that the Ubuntu Software Center was using. 

With Software Center opened, go to Edit > Software Sources... (you will be asked for Admin password). In the proceeding window, from the "Download from:" drop-down menu, select "Other". Choose a new mirror yourself, or select the option to test them all and automatically select the best.

---

