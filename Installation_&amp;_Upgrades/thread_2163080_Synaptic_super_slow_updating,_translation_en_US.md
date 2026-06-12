---
title: "Synaptic super slow updating, translation_en_US"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2013-07-17
I'm trying to update packages in Synaptic.  I get big delays, and fails on anything that says Translation-en_US.  The delays aren't always on the translations, but I'm actually trying to do something with this box now, and I'm getting grouchy.

This has been going on for awhile now, but it hasn't hugely bothered me because I don't update all that often.

I have a hard ethernet connection, and it's working because I can go to web sites.

It takes about 5 minutes to click the "reload" button.


I'm also trying to load 'mdadm' so I can install a RAID array on the existing system, but it's saying it's an untrusted package.  Might this have something to do with the problem?

This is something I've never had to mess with.  I've used Ubuntu Server over and over, and I know it loads mdadm no problem.

I have Ubuntu Server 13.04 also, and I'm wondering if I can just copy /etc/apt/trust* onto the Xubuntu installation without problems?

Thanks.

---

### Post by newbie-user on 2013-07-17
What is in your /etc/sources.list file? I suspect you might have to choose different repositories to download from.

---

### Post by 1clue on 2013-07-17
```

# deb cdrom:[Xubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130423.1)]/ raring main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
######deb http://extras.ubuntu.com/ubuntu raring main
# deb-src http://extras.ubuntu.com/ubuntu raring main

```

---

### Post by newbie-user on 2013-07-17
I've always found the mirror at archive.ubuntu.com to be slow. Try using a mirror that is closer to you:
[http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror](http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror)

---

### Post by 1clue on 2013-07-17
Thanks.  That worked.

---

