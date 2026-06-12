---
title: "Sources.list questions"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by hackle577 on 2008-04-27
I'm curious about my sources.list. In Software Sources I have security, updates, proposed, and backports all checked. But my sources.list looks like this:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://mirror.anl.gov/pub/ubuntu/ hardy universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://mirror.anl.gov/pub/ubuntu/ hardy multiverse
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://mirror.anl.gov/pub/ubuntu/ hardy-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security multiverse
deb http://mirror.anl.gov/pub/ubuntu/ hardy-backports restricted main multiverse universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-proposed restricted main multiverse universe
```

As you can see, the backports lines appear to be commented out. I guess I'm just not quite sure how to read this file... help?

Thanks!

---

### Post by Pumalite on 2008-04-27
Your sources.list looks fine.

---

### Post by Perpetual on 2008-04-27
Here is mine with backports...

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
```

---

### Post by Pumalite on 2008-04-28
Here is mine, with other goodies:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb  [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

### Post by Glaxed on 2008-04-28
Are there seveas and morgoth etc repos for hardy yet?
Edit >>> Translated from german->Eng with Google's help;[http://oshelpdesk.org/?page_id=355](http://oshelpdesk.org/?page_id=355)
I love google.
[http://vminch.googlepages.com/hardyoshelpdesksrc.list](http://vminch.googlepages.com/hardyoshelpdesksrc.list)

I'm on Windows. One of you dare devils try this list out and tell me if it's any good.

---

### Post by Glaxed on 2008-04-28
edit>> double post - sorry

---

### Post by Pumalite on 2008-04-28
Try it yourself and tell us about it.

---

### Post by lemming465 on 2008-04-28
If you do *grep hardy-backports /etc/apt/sources.list* you will see that you have another entry at mirror.anl.gov toward the bottom which is **not** commented out.

Try *man sources.list* for more details on the possible syntax options.

---

### Post by Glaxed on 2008-04-28
There are a gazzilion errors with the original list that i am scrambling to fix. The one on my site works - but moans and whines about 404s, IGNs, and Errs.. I'll remove those entries later - however, the pros are very good: 
```

The following packages will be upgraded:
  compiz-fusion-plugins-main foomatic-filters gtk2-engines-pixbuf gvfs gvfs-backends lftp
  libavcodec1d libavformat1d libavutil1d libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtk2.0-dev libgvfscommon0 libpostproc1d lshw
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives.
After this operation, 439kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  lftp libavutil1d libavcodec1d libavformat1d libpostproc1d

```
And nothing broke - safe packages so far.

---

