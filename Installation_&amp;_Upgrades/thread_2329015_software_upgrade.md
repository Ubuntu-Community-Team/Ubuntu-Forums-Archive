---
title: "software upgrade"
date: 2016-06-27
forum: Installation &amp; Upgrades
---

### Post by Bigmon on 2016-06-27
Hi.
Trying to upgrade/update my Ubuntu 10.04 but get connection error in the update manager. Connection is fine. Tried to work through some recommendations - changing to main server, unchecking PPA, but still cannot perform any updates. Can anyone suggest anything ?

---

### Post by howefield on 2016-06-27
10.04 is end of life with the repositories moved to old-releases, what is the exact error that you are getting ?

This link might help : [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Bigmon on 2016-06-27
How do I move to a supported version ?

---

### Post by howefield on 2016-06-27
> **Bigmon said:**
> How do I move to a supported version ?

Did you visit the link above ?

It starts with the sentence..
> 
This page will explain how to upgrade an End of Life (EOL) release of Ubuntu to a supported system. 

---

### Post by Bigmon on 2016-06-27
Yes, will give it a go thanks.

---

### Post by howefield on 2016-06-27
OK, give the page a read and then, if you have any doubts or questions, please post back.

---

### Post by Bigmon on 2016-06-27
Managed it all, except updating the sources list. Couldn't work that out. Anyway, it looked good, told me how much extra disc space I would need etc, asked me if I want to continue (y/N). I pressed "Y", then "aborted" came up ? Did it a few times, but same results.

---

### Post by howefield on 2016-06-27
Can you post the output of..

```
cat /etc/apt/sources.list
```

---

### Post by Bigmon on 2016-06-27
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
graham@graham-desktop:~$
```

---

### Post by howefield on 2016-06-27
The sources.list need to reflect the old-releases repositories as mentioned and I'm not sure that you can go straight to 14.04 from 10.04. I'll load up an old 10.04 install and help you through it but it'll take me an hour or so before I have some free time.

---

### Post by grahammechanical on 2016-06-27
> I'm not sure that you can go straight to 14.04 from 10.04.

We can't. Is my opinion. The lines like this in the sources.list should read

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe

> deb [http://old.releases.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") lucid universe

That will allow 10.04 to be updated. Then you should get a notification to upgrade to 12.04 from whatever updater manager 10.04 is using . I hope that you are running on the open source video driver. Of course, if we change the URLs in the sources list file to point to the repositories of newer versions and then update our OS will be upgraded but expect breakage as that is not the planned for way of upgrading Ubuntu to a newer release. Be prepared to re-install.

Regards.

---

### Post by Bigmon on 2016-06-27
OK. Thanks.

---

### Post by howefield on 2016-06-27
Well, that was incredibly painful, to the extent that I'd advise backing up all important data and doing a clean install. Much quicker and easier, especially as you'll need to go firstly to 12.04 (which is well into its final year of support) and then on to 14.04 and possibly on again to 16.04 if you want to be on the latest LTS release.

However, have finally got a 10.04 virgin installation updating to 12.04.

Firstly uninstall any proprietary drivers that you may be using and also disable any PPAs, and back up any important data.

Then edit the /etc/apt/sources.list to reflect..

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse 
```

You can take a copy of your existing sources.list with..

```
sudo cp /etc/apt/sources.list /~/Documents
```

and change the sources.list with

```
gksudo nautilus /etc/apt/sources.list
```

Then..

```
sudo apt-get install update-manager-core update-manager
```
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

May not need a reboot but I did at this point, then...

```
sudo do-release-upgrade
```

If you have problems, then post the exact error messages.

---

### Post by howefield on 2016-06-27
> **howefield said:**
> Well, that was incredibly painful, to the extent that I'd advise backing up all important data and doing a clean install. 

Just to confirm, took a while to finish and whilst painful, it was ultimately successful.

Also, be aware that the desktop environment will change to the Unity interface :)

---

### Post by Bigmon on 2016-07-04
Thanks for all your help. The computer asked me if I wanted to update to 15.04 so I clicked yes but it failed miserably (yes, I know, I was warned). Computer crashed and could no longer boot up. 
Got the wife's laptop, created an ISO disc of 16.04, and ran that from start-up. It gave me options to run alongside 14.04, upgrade from 14.04, but none of them worked. So I did a clean install of 16.04 erasing all existing data. I did manage to save important stuff first though that was on the hard drive. Before installation, ubuntu gives you the opportunity to "try" ubuntu before installation. It was at this time that I copied some existing data on to a USB stick.
Not the most graceful way, but worked.

---

