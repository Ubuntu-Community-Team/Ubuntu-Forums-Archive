---
title: "Lucid update issues"
date: 2009-11-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-11-10
I did a clean reinstall of Karmic Via CD and when that was all finished I planned to upgrade to lucid.  It didn't go well:confused: 

update-manager -d: does not notify me of an upgrade.   Any advice?

---

### Post by alphacrucis2 on 2009-11-10
> **sox fan Matt said:**
> I did a clean reinstall of Karmic Via CD and when that was all finished I planned to upgrade to lucid.  It didn't go well:confused: 

update-manager -d: does not notify me of an upgrade.   Any advice?


Edit your /etc/apt/sources.list file. Change all occurrences of karmic -> lucid. Then 

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by sports fan Matt on 2009-11-10
Apparently I switched everything over in my sources list but still have karmic entries even after updating..hmm.  

Fetched 10.5MB in 13s (762kB/s)                                                
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

---

### Post by whoop on 2009-11-10
> **sox fan Matt said:**
> Apparently I switched everything over in my sources list but still have karmic entries even after updating..hmm.  

Fetched 10.5MB in 13s (762kB/s)                                                
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

These look like specific karmic entries, they just have been changed to lucid (but they don't exist). You can comment them out in sources.

---

### Post by alphacrucis2 on 2009-11-10
> **sox fan Matt said:**
> Apparently I switched everything over in my sources list but still have karmic entries even after updating..hmm.  

Fetched 10.5MB in 13s (762kB/s)                                                
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]

1. Remove all PPA's
2. Change to use the main server. Looks like your us.archive.ubuntu.com doesn't have the lucid packages on it yet.

---

### Post by ranch hand on 2009-11-10
Mine works fine on the "us" setting.

---

### Post by sports fan Matt on 2009-11-10
I'll get there..latest round of not founds: 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by xebian on 2009-11-10
> **sox fan Matt said:**
> I'll get there..latest round of not founds: 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Comment out these.  Think for a moment.  There is no such thing as lucid-backports yet.  This makes relevance only when master..monkeys is released.

---

### Post by LKjell on 2009-11-10
> **sox fan Matt said:**
> I'll get there..latest round of not founds: 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/lucid-backports/dists/main/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.134 80]
Some index files failed to download, they have been ignored, or old ones used instead.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://archive.ubuntu.com/ubuntu/ lucid-security multiverse

```

---

### Post by sports fan Matt on 2009-11-10
I now copied, saved the above list: sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found


and update-manager -d does not show the upgrade..perhaps checking for lts since it is 10.04 under release upgrade would help?

---

### Post by LKjell on 2009-11-10
Do to check what you have.
```
lsb_release -a
```

---

### Post by alphacrucis2 on 2009-11-10
> **sox fan Matt said:**
> I now copied, saved the above list: sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found


and update-manager -d does not show the upgrade..perhaps checking for lts since it is 10.04 under release upgrade would help?

Just do 

sudo apt-get dist-upgrade

That should be enough to get you onto Lucid now you have manually changed your sources and run sudo apt-get update. Nothing more should be needed.

---

### Post by sports fan Matt on 2009-11-10
Heh...I am running lucid.  I wonder why there wasn't a prompt to restart my system.  Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

---

### Post by alphacrucis2 on 2009-11-10
> **sox fan Matt said:**
> Heh...I am running lucid.  I wonder why there wasn't a prompt to restart my system.  Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

It should have installed kernel 2.6.32-2 unless you were already running that under karmic I would have expected it to want to reboot.

---

### Post by ranch hand on 2009-11-10
Update Manager knows nothing about this yet.  It would be great to forget Update mangler for the rest of testing.

To get this thing going though, is easy;
```

sudo apt-get update

```and 
[code]
sudo apt-get dist-upgrade
[code]
EDIT
A Little late I see.  Good we have another victim.

---

### Post by sports fan Matt on 2009-11-10
one thing im wondering though...About ubuntu says: im using 9.10.  Weird

---

### Post by LKjell on 2009-11-10
That is because nobody has written a new documentation.

If it bother you much you can edit the /etc/lsb-release file to karmic...

Which makes me think that lucid and karmic is the same at this state.

---

### Post by alphacrucis2 on 2009-11-10
> **LKjell said:**
> That is because nobody have written a new documentation.

Yep. We are not even at alpha yet.

---

### Post by VMC on 2009-11-10
> **sox fan Matt said:**
> one thing im wondering though...About ubuntu says: im using 9.10.  Weird

sox fan, Read this [link]("http://ubuntuforums.org/showthread.php?t=1308574"). There is one more file to edit. Especially this [post]("http://ubuntuforums.org/showpost.php?p=8215796&postcount=6").

---

### Post by LKjell on 2009-11-10
> **VMC said:**
> sox fan, Read this [link]("http://ubuntuforums.org/showthread.php?t=1308574"). There is one more file to edit. Especially this [post]("http://ubuntuforums.org/showpost.php?p=8215796&postcount=6").
He is one of the lucky that does not need to edit that file. It was fixed last Thursday.

---

### Post by papangul on 2009-11-10
Isn't dist-upgrade supposed to be used in a "stable release to stable release" scenario only?

Think of it, if you are running lucid and the state of archive at certain point of time is such that dist-upgrade will create problems(like the problem with the pulseaudio package that occured recently) then dist upgrading from karmic to lucid at that point of time is bound to create the exactly same problem.

---

### Post by 23meg on 2009-11-10
> **papangul said:**
> Isn't dist-upgrade supposed to be used in a "stable release to stable release" scenario only?

Think of it, if you are running lucid and the state of archive at certain point of time is such that dist-upgrade will create problems(like the problem with the pulseaudio package that occured recently) then dist upgrading from karmic to lucid at that point of time is bound to create the exactly same problem.

Which is why it's generally a better idea, especially for less experienced testers, to begin testing with a milestone release.

---

### Post by LKjell on 2009-11-10
You need a strong gut feeling or read through the change logs to be certain when to do dist-upgrade,  partial-upgrade..

---

### Post by alphacrucis2 on 2009-11-10
> **papangul said:**
> Isn't dist-upgrade supposed to be used in a "stable release to stable release" scenario only?

Think of it, if you are running lucid and the state of archive at certain point of time is such that dist-upgrade will create problems(like the problem with the pulseaudio package that occured recently) then dist upgrading from karmic to lucid at that point of time is bound to create the exactly same problem.

Yeah but you just read what is says it is going to do and if you don't like it you say no and do an aptitude safe-upgrade first. Then check the changes log for whatever a dist-upgrade wanted to trash to see if it is legit.

---

### Post by papangul on 2009-11-10
> **23meg said:**
> Which is why it's generally a better idea, especially for less experienced testers, to begin testing with a milestone release.
It would be nice if there was a freeze on the repos for a period of 12 hours or so during the release of milestone releases.

---

### Post by ranch hand on 2009-11-10
> **papangul said:**
> It would be nice if there was a freeze on the repos for a period of 12 hours or so during the release of milestone releases.
You are no FUN at ALL.

---

### Post by papangul on 2009-11-10
> **ranch hand said:**
> You are no FUN at ALL.
I need a break from all the fun I am having with karmic.

---

### Post by ranch hand on 2009-11-10
Ah, that could be it.  Your own problems or forum problems?

My Kinky Kitten install is just purring along very nicely.

---

### Post by VMC on 2009-11-11
> **papangul said:**
> It would be nice if there was a freeze on the repos for a period of 12 hours or so during the release of milestone releases.

Why stop there. Just freeze until first alpha.

---

### Post by 23meg on 2009-11-11
> **papangul said:**
> It would be nice if there was a freeze on the repos for a period of 12 hours or so during the release of milestone releases.

There's a soft freeze lasting more than *four days* before milestone releases, during which only very high priority uploads go through.

---

### Post by VMC on 2009-11-11
> **23meg said:**
> There's a soft freeze lasting more than *four days* before milestone releases, during which only very high priority uploads go through.

Ok, I see now what he meant by that freeze statement, My bad.

---

### Post by papangul on 2009-11-11
> **23meg said:**
> There's a soft freeze lasting more than *four days* before milestone releases, during which only very high priority uploads go through.
Strange, I came across many milestone releases of karmic but the daily updates never seemed to slow down, even for a single day. Thats how I gathered the idea that milestone releases are non event for the repos!

---

