---
title: "Failed to fetch ... Unable to find expected entry  partner/binary-i386/Packages in Me"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by Harry66 on 2010-09-25
Hi all,

Recently I have started to get these errors from the Update Manager, and I've had no more updates.

[SIZE="1"][FONT="Courier New"]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror01.th.ifl.net/ubuntu/dists/lucid/Release](http://mirror01.th.ifl.net/ubuntu/dists/lucid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror01.th.ifl.net/ubuntu/dists/lucid-updates/Release](http://mirror01.th.ifl.net/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror01.th.ifl.net/ubuntu/dists/lucid-proposed/Release](http://mirror01.th.ifl.net/ubuntu/dists/lucid-proposed/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.[/FONT][/SIZE]


Looking at other posts, I can't quite see how the solutions relate to my problem. /etc/apt/sources/list looks fine - I've attached it as sources.list.txt

My system (i386) had Jaunty installed, which has been upgraded to Karmic, then Lucid.

I've tried several update servers (default, UK, and find best) all with the same result.

My new system (amd64), which has a fresh install of Lucid, has no problem.
Comparing /etc/apt/sources.list for the 2 systems gives me no hints..

Any ideas? (Thanks in advance)

---

### Post by sikander3786 on 2010-09-25
Did you setup an apt-mirror for creating a local update server?

If not, you can generate a new sources.list here and see if it works.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I am in such a position that I can't use text editor otherwise I'd have gone through your file. The easiest option I can recommend from here is to generate a new sources.list. Some fellow might be able to point out some other solution later.

---

### Post by Harry66 on 2010-09-25
> **sikander3786 said:**
> Did you setup an apt-mirror for creating a local update server?

If not, you can generate a new sources.list here and see if it works.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I am in such a position that I can't use text editor otherwise I'd have gone through your file. The easiest option I can recommend from here is to generate a new sources.list. Some fellow might be able to point out some other solution later.

Cheers, I will look into setting up a mirror, as I have a couple of systems now.

In the meantime, I'll also have a look at your link.

**my sources.list inline is:**

[FONT="Courier New"][SIZE="1"]# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid main restricted
deb-src [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid universe
deb-src [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid multiverse
deb-src [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security partner restricted main multiverse universe
deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid-updates partner restricted main multiverse universe
deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid-proposed partner restricted main multiverse universe
deb [http://mirror01.th.ifl.net/ubuntu/](http://mirror01.th.ifl.net/ubuntu/) lucid partner[/SIZE][/FONT]

---

