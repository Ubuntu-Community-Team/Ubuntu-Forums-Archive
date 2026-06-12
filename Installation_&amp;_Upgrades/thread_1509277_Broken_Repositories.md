---
title: "Broken Repositories"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2010-06-14
Some repositories disappeared today.  Where did they go?

[INDENT]Failed to fetch [http://archive.cononical.cam/ubuntu/dists/lucic/Release.gpg](http://archive.cononical.cam/ubuntu/dists/lucic/Release.gpg)  Something wicked happened resolving 'archive.cononical.cam:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.cononical.cam/ubuntu/dists/lucic/commercial/source/Sources.gz](http://archive.cononical.cam/ubuntu/dists/lucic/commercial/source/Sources.gz)  Something wicked happened resolving 'archive.cononical.cam:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

_._

---

### Post by plucky on 2010-06-14
> Failed to fetch [http://archive.cononical.cam/ubuntu/...rce/Sources.gz](http://archive.cononical.cam/ubuntu/...rce/Sources.gz)  Something wicked happened resolving 'archive.cononical.cam:http' (-5 - No address associated with hostname)

Open a terminal and ```
cat /etc/apt/sources.list
``` and post the output to the forum.Your sources.list seems to be corrupt.

There is no **cononical.cam**

---

### Post by arvevans on 2010-06-14
But how did it get corrupted?

And, why did it not recover?

As Requested:
[INDENT]arv@arv-desktop:~$ sudo cat /etc/apt/sources.list
[sudo] password for arv: 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to karmic disabled on upgrade to lucid
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to karmic disabled on upgrade to lucid


# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu](http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu](http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu) lucid main

# Adding Canonical's Commercial Repositories
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid commercial
deb-src [http://archive.cononical.cam/ubuntu](http://archive.cononical.cam/ubuntu) lucic commercial

arv@arv-desktop:~$ 
[/INDENT]

---

### Post by arvevans on 2010-06-14
Just now tried to do System-Administration-Update Manager and am getting indications that some repositories (the old .cam ones) cannot be accessed.

[INDENT]Failed to fetch [http://archive.cononical.cam/ubuntu/dists/lucic/Release.gpg](http://archive.cononical.cam/ubuntu/dists/lucic/Release.gpg)  Something wicked happened resolving 'archive.cononical.cam:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.cononical.cam/ubuntu/dists/lucic/commercial/source/Sources.gz](http://archive.cononical.cam/ubuntu/dists/lucic/commercial/source/Sources.gz)  Something wicked happened resolving 'archive.cononical.cam:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

When I look at System-Administration-Software Sources-Other Software I see this:

      [IMG]http://qrp.webhop.net/Ubuntu.html[/IMG]

      <http://qrp.webhop.net/Ubuntu.html>

Thanks,

---

### Post by wojox on 2010-06-14
The very last line says

**deb-src [http://archive.cononical](http://archive.cononical).[COLOR="Red"]cam[/COLOR]/ubuntu  [COLOR="Red"]lucic[/COLOR] commercial**

It should be 

```
deb-src http://archive.cononical.com/ubuntu  lucicd commercial
```

---

### Post by plucky on 2010-06-14
> # Adding Canonical's Commercial Repositories
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid commercial
deb-src [http://archive.cononical.cam/ubuntu](http://archive.cononical.cam/ubuntu) lucic commercial


Where did you get the information about this repository?
Does it actually exist?

---

### Post by arvevans on 2010-06-14
OK...Sources file edited to change Lucic to Lucid.

Still wondering how this got changed or replaced?  There has been no recent activity in this area for at least 8 months, but the problem showed up yesterday.

[INDENT]arv@arv-desktop:~$ sudo vi /etc/apt/sources.list
arv@arv-desktop:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to karmic disabled on upgrade to lucid
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to karmic disabled on upgrade to lucid


# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu](http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu](http://ppa.launchpad.net/gezakovacs/pyaudio/ubuntu) lucid main

# Adding Canonical's Commercial Repositories
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid commercial
deb-src [http://archive.cononical.cam/ubuntu](http://archive.cononical.cam/ubuntu) lucid commercial

arv@arv-desktop:~$ 
[/INDENT]

Still have a problem though:

    <http://qrp.webhop.net/Screenshot.jpg>

Thanks,

Arv
_._

---

### Post by plucky on 2010-06-15
> # Adding Canonical's Commercial Repositories
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid commercial
deb-src [http://archive.cononical.cam/ubuntu](http://archive.cononical.cam/ubuntu) lucid commercial

Remove those two lines by putting a # in front of them and see if your problem goes away.As far as I know those are not repositories.

p.s If you put your link between [noparse][]()[/noparse] blocks,it is easier to click on. 

Example [http://qrp.webhop.net/Screenshot.jpg](http://qrp.webhop.net/Screenshot.jpg)

Good Luck

---

### Post by wilee-nilee on 2010-06-15
> **wojox said:**
> The very last line says

**deb-src [http://archive.cononical](http://archive.cononical).[COLOR="Red"]cam[/COLOR]/ubuntu  [COLOR="Red"]lucic[/COLOR] commercial**

It should be 

```
deb-src http://archive.cononical.com/ubuntu  **_lucicd_ **commercial
```

I love your webpage it is quite helpful.;)

---

### Post by wilee-nilee on 2010-06-15
These are commented out but should they be jaunty.
```
# deb http://us.archive.ubuntu.com/ubuntu/  jaunty-backports main restricted universe multiverse
```
```
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```

The canonical repo has no key if thats part of the problem.

I would go to software sources choose other from the 1st tab then select best one for repos then choose the one that pings the quickest. I was having a similar problem and just changed to a NZ repo.

---

### Post by wojox on 2010-06-15
> **arvevans said:**
> OK...Sources file edited to change Lucic to Lucid.

St
deb-src [http://archive.cononical.cam/ubuntu](http://archive.cononical.cam/ubuntu) lucid commercial

arv@arv-desktop:~$ 
[/INDENT]

Still have a problem though:

Thanks,

Arv
_._


You still having a problem because you need to change .cam to .com

---

### Post by wojox on 2010-06-15
> **wilee-nilee said:**
> I love your webpage it is quite helpful.;)

Thanks wilee-nilee :p

---

### Post by arvevans on 2010-06-16
Thanks everybody for the help.  I'm not sure why my first edit of the sources list didn't take, but the second edit did the job.  This morning I was able to check for updates, install an update, and re-check for updates without any errors.

Thanks again for the help.  This one is SOLVED, or at least...FIXED.

Arv
_._

---

