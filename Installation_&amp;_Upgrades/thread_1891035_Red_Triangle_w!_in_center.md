---
title: "Red Triangle w/! in center"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by gulmer on 2011-12-04
This appears on the top panel and when I click on check all updates I get a fail with this:W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Nothing gets installed because there isn't anything to install, so why does the triangle pop up on the panel?

---

### Post by Old_Grey_Wolf on 2011-12-04
Those are all trying to get updates from the Karmic (9.10) repositories. Karmic has not been supported for a while, it is End-Of-Life. The 9.10 repositories have been moved to old-releases. You should upgrade to a supported release, 10.04 or newer.

Your profile shows that you are using 10.10. If that is the case on the computer you are trying to update then post the output of ```
cat /etc/apt/sources.list
```

Someone should be able to help you remove the lines referencing Karmic. 

I am about to go to sleep so I leave you with the other members of this forum to help you.

---

### Post by oldtimer7777 on 2011-12-04
> **gulmer said:**
> This appears on the top panel and when I click on check all updates I get a fail with this:W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.179 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Nothing gets installed because there isn't anything to install, so why does the triangle pop up on the panel?

End-Of-Life

Out with the old. In with the new! 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Old_Grey_Wolf on 2011-12-04
> **oldtimer7777 said:**
> End-Of-Life

Out with the old. In with the new! 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is possible that is it a bad sources.list file and not EOL, as I posted 30 minutes ago!

---

### Post by gulmer on 2011-12-06
> **Old_Gray_Wolf said:**
> Those are all trying to get updates from the Karmic (9.10) repositories. Karmic has not been supported for a while, it is End-Of-Life. The 9.10 repositories have been moved to old-releases. You should upgrade to a supported release, 10.04 or newer.

Your profile shows that you are using 10.10. If that is the case on the computer you are trying to update then post the output of ```
cat /etc/apt/sources.list
```

Someone should be able to help you remove the lines referencing Karmic. 

I am about to go to sleep so I leave you with the other members of this forum to help you.

 Sorry about getting back to this so late. I'm running Ubuntu 11.10 Oneiric Ocelot. This is what I get after running your code:
gene@gene-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

Not sure what this all is saying, My computer is working OK, I just get this triangle w/! popping up on the panel and needed to figure out what it wants.

---

### Post by bluexrider on 2011-12-06
the big red triangle with /! = issues.

your 
cat /etc/apt/sources.list

did you move from Karmic to Oneiric via upgrades?

It would appear some leftover sources need to be flushed.

---

### Post by gulmer on 2011-12-06
> **bluexrider said:**
> the big red triangle with /! = issues.

your 
cat /etc/apt/sources.list

did you move from Karmic to Oneiric via upgrades?

It would appear some leftover sources need to be flushed.

I upgrade to each new distro that comes out, every 6 months, since I started with 6.06 Ubuntu. The triangle hasn't come back today, after a update from yesterday. Maybe it's fixed. This is the first time for the triangle to appear, after all the distro upgrades after Karmic and since the upgrade to 11.10 last month.

---

### Post by bluexrider on 2011-12-06
there is one entry I would #comment out or remove in your list

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

no longer needed

Remove this one 

 # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

its up to you

---

