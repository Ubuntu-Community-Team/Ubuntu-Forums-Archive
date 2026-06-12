---
title: "Damaged/non-working source.list"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by BlueKnight84 on 2008-07-29
Hello all.

I am running Ubuntu 6.10 and trying to upgrade.  I can't do anything as it relates to upgrading, from update manager, apt-get, network boot upgrade, and the alternative CD.

At some point for each of those, they obviously have to talk to a mirror site, and I always get an error.  Even the alternative CD gives me a "Failed to fetch" because it encounters a problem talking to a server.

I am a total noob, I'm talking in all meanings of the term.  I'm pretty sure if I were to just update my sources.list, it would solve all my problems.  Here it is as current:

```
$ cat /etc/apt/sources.list
 deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
 deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
 deb http://us.archive.ubuntu.com/ubuntu edgy-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

Anyone have a working sources.list or have any idea as to what I can do?  Again, I'm running Ubuntu Desktop 6.10, if it matters.

Thanks for reading!

---

### Post by Pumalite on 2008-07-29
Sorry; I think 6.10 is not supported any longer

---

### Post by SkonesMickLoud on 2008-07-29
6.10 is no longer supported by Canonical, so you'll have to upgrade to 7.04.

```
sudo aptitude update && sudo aptitude dist-upgrade
```

You may want to consider --especially if you plan on going to 8.04 -- getting a disk or .iso and doing a clean install, as the upgrade process will take a lot longer than a clean install.

---

### Post by BlueKnight84 on 2008-07-29
Thanks guys for the response!

I'll see about doing a clean install, then.

---

### Post by avtolle on 2008-07-29
For anyone who is in the same position as BlueKnight84, and wants to try to do a "network upgrade" from 6.10 to 7.04, see [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) and pay special attention to the changes to be made in the sources.list and the need to have the current update manager installed.

---

### Post by Pumalite on 2008-07-29
Or you might want to do this:
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade

---

### Post by BlueKnight84 on 2008-08-16
Thanks to everyone for their help.  I'm sorry for just now updating all of you, as I went on vacation and have just now been able to resume tackling this issue.

Well I have good news!  I updated my sources.list to:

```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

...then I ran "sudo apt-get update" and voila!- it worked!  Now I shouldn't have any problems simply "upgrading" my Ubuntu installation.

Thanks again to all of you who helped me!!!

---

### Post by aka_bigred on 2008-08-27
> **BlueKnight84 said:**
> Thanks to everyone for their help.  I'm sorry for just now updating all of you, as I went on vacation and have just now been able to resume tackling this issue.

Well I have good news!  I updated my sources.list to:

```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

...then I ran "sudo apt-get update" and voila!- it worked!  Now I shouldn't have any problems simply "upgrading" my Ubuntu installation.

Thanks again to all of you who helped me!!!


Thanks for the tip.  I don't have time right now to do a full system rebuild, so with this new sources.list I can limp along on my 6.10 build until winter rolls around and I can rebuild.  Sure staying on 6.10 is not optimal and updating to 8.04 would be best, but this is great a short-term hack :)

---

