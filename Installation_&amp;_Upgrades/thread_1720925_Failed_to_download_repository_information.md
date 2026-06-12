---
title: "Failed to download repository information"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Mordac85 on 2011-04-03
For a few weeks I've been ignoring an error about updates from my sources (error below)
```
Failed to fetch [http://archive.ubuntu.com/dists/maverick/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/dists/maverick/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/maverick/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
```

If I actually browse to [http://archive.ubuntu.com]("http://archive.ubuntu.com") the folder off the root is **ubuntu** not **dists**.  I was set to download from the US server and I tried a few other specific servers just in case the one I was going to was messed up and I got the same thing.

Is there a way to change this or did someone just make a subfolder and not propagate the change properly?

---

### Post by plucky on 2011-04-04
> **Mordac85 said:**
> For a few weeks I've been ignoring an error about updates from my sources (error below)
```
Failed to fetch [http://archive.ubuntu.com/dists/maverick/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/dists/maverick/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/maverick/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
```

If I actually browse to [http://archive.ubuntu.com]("http://archive.ubuntu.com") the folder off the root is **ubuntu** not **dists**.  I was set to download from the US server and I tried a few other specific servers just in case the one I was going to was messed up and I got the same thing.

Is there a way to change this or did someone just make a subfolder and not propagate the change properly?

The address in your sources.list is not pointing to the correct address.

Please post output from a terminal for ```
cat /etc/apt/sources.list
```

---

### Post by Mordac85 on 2011-04-04
Sorry, I forgot to include that.
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.us.kernel.org/ubuntu/ maverick main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.us.kernel.org/ubuntu/ maverick-updates main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.us.kernel.org/ubuntu/ maverick universe
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick universe
deb http://mirrors.us.kernel.org/ubuntu/ maverick-updates universe
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.us.kernel.org/ubuntu/ maverick multiverse
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick multiverse
deb http://mirrors.us.kernel.org/ubuntu/ maverick-updates multiverse
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://mirrors.us.kernel.org/ubuntu/ maverick-security main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-security main restricted
deb http://mirrors.us.kernel.org/ubuntu/ maverick-security universe
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-security universe
deb http://mirrors.us.kernel.org/ubuntu/ maverick-security multiverse
deb-src http://mirrors.us.kernel.org/ubuntu/ maverick-security multiverse

deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu maverick main
deb http://archive.ubuntu.com maverick main universe

```

---

### Post by matt_symes on 2011-04-04
Hi

Open a terminal ant type

```
sudo nano /etc/apt/sources.list
```

Enter your password. It will not be echoed to the screen.

Scroll down to the last line that reads

```
deb http://archive.ubuntu.com maverick main universe
```

and  change to 

```
deb http://archive.ubuntu.com/ubuntu maverick main universe
```

Press Ctrl + o to save and Ctrl + x to exit.

Kind regards

---

### Post by Mordac85 on 2011-04-04
Worked like a charm, thanks.  I was going to try that but I wasn't sure why my system that was built 3 wks ago ran into this issue.  Shouldn't a change like that be able to be picked up by existing clients in some manner?

---

### Post by matt_symes on 2011-04-04
Hi

> **Mordac85 said:**
> Worked like a charm, thanks.  I was going to try that but I wasn't sure why my system that was built 3 wks ago ran into this issue.  Shouldn't a change like that be able to be picked up by existing clients in some manner?

I'm glad it's fixed. :D Please mark this thread as solved.

Kind regards

---

### Post by Mordac85 on 2011-04-05
I will, once it's actually solved.  This is a hack/workaround and not a solution to the root cause.

Does anyone know WHY this default repo has either changed or my sources.list not updated to reflect the change?

I could understand it if it was some 3rd party repo and I admit I don't understand how they normally update an entry in the sources.list, but if the path in one of their repo's changes shouldn't part of Canonical's process be to get this change distributed to the community?  Or did I just point out that someone screwed up by changing the path and NOT pushing the change out to us?

---

