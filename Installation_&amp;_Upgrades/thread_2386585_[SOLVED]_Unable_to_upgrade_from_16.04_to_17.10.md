---
title: "[SOLVED] Unable to upgrade from 16.04 to 17.10?"
date: 2018-03-07
forum: Installation &amp; Upgrades
---

### Post by eezacque on 2018-03-07
The process ends at "Could no calculate the upgrade".

The file   /var/log/dist-upgrade/apt.log reports 332 broken packages, starting with:

Broken python3:amd64 Depends on python3.6 [ amd64 ] < none -> 3.6.3-1ubuntu1 > ( python ) (>= 3.6.3-1~)
Broken libdouble-conversion1:amd64 Breaks on libdouble-conversion1v5 [ amd64 ] < 2.0.1-3ubuntu2 > ( libs )
Broken python3-gi:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.3-0ubuntu2 > ( python ) (< 3.7)
Broken systemd-sysv:amd64 Conflicts on systemd-shim [ amd64 ] < 9-1bzr4ubuntu1 > ( admin )
Broken dh-python:amd64 Depends on python3:any [ any ] < none ->  > ( none ) (>= 3.3.2-2~)
Broken python3-minimal:amd64 Depends on python3.6-minimal [ amd64 ] < none -> 3.6.3-1ubuntu1 > ( python ) (>= 3.6.3-1~)
Broken lsb-release:amd64 Depends on python3:any [ any ] < none ->  > ( none ) (>= 3.4~)
Broken python3-dbus:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.3-0ubuntu2 > ( python ) (< 3.7)
Broken python3-apt:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.3-0ubuntu2 > ( python ) (< 3.7)

I don't even see where to start, so any help is appreciated.

---

### Post by Bashing-om on 2018-03-07
eezacque; Hummm ...

Something stinks .
16.04 python3 versioning:
> 
sysop@x1604:~$ apt policy python3
python3:
  Installed: 3.5.1-3
  Candidate: 3.5.1-3
  Version table:
 *** 3.5.1-3 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
sysop@x1604:~$

where your system is screaming about " < none -> 3.6.3-1ubuntu1 > ( python ) (>= 3.6.3-1~)".
Which is 17.10:
[https://packages.ubuntu.com/search?keywords=python3&searchon=names&suite=artful&section=all](https://packages.ubuntu.com/search?keywords=python3&searchon=names&suite=artful&section=all)

Now that begs the question of the procedure you used to do the release upgrade - as will have to go through the End_Of_Life release 17.04.

What now is the current condition of the install ?
Post back- Between Code Tags -  the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
cat /etc/issue
lsb_release -a

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As a place to start to determine the state of affairs .

[INDENT][INDENT]haste makes waste
[/INDENT][/INDENT]

---

### Post by eezacque on 2018-03-07
```

$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://mirror.transip.net/ubuntu/ubuntu/ xenial main restricted universe multiverse
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb http://mirror.transip.net/ubuntu/ubuntu/ xenial-updates main restricted universe multiverse
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team. Also, please note that software in universe WILL NOT receive any
    13	## review or updates from the Ubuntu security team.
    14	
    15	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    16	## team, and may not be under a free licence. Please satisfy yourself as to 
    17	## your rights to use the software. Also, please note that software in 
    18	## multiverse WILL NOT receive any review or updates from the Ubuntu
    19	## security team.
    20	
    21	## N.B. software from this repository may not have been tested as
    22	## extensively as that contained in the main release, although it includes
    23	## newer versions of some applications which may provide useful features.
    24	## Also, please note that software in backports WILL NOT receive any review
    25	## or updates from the Ubuntu security team.
    26	deb http://mirror.transip.net/ubuntu/ubuntu/ xenial-backports main restricted universe multiverse
    27	
    28	deb http://mirror.transip.net/ubuntu/ubuntu/ xenial-security main restricted universe multiverse
    29	
    30	## Uncomment the following two lines to add software from Canonical's
    31	## 'partner' repository.
    32	## This software is not part of Ubuntu, but is offered by Canonical and the
    33	## respective vendors as a service to Ubuntu users.
    34	# deb http://archive.canonical.com/ubuntu trusty partner
    35	# deb-src http://archive.canonical.com/ubuntu trusty partner
    36	
    37	# deb http://deb.torproject.org/torproject.org xenial main
    38	# deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main

$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list.save <==

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-xenial.list <==
# deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/eugenesan-ubuntu-ppa-xenial.list.save <==
# deb http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-earth.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/irie-ubuntu-blender-utopic.list <==
# deb http://ppa.launchpad.net/irie/blender/ubuntu utopic main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/irie-ubuntu-blender-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/irie/blender/ubuntu utopic main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/irie-ubuntu-blender-utopic.list.save <==
# deb http://ppa.launchpad.net/irie/blender/ubuntu utopic main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-utopic.list <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-utopic.list.save <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-xenial.list <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/jfi-ubuntu-ppa-xenial.list.save <==
# deb http://ppa.launchpad.net/jfi/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/jonathonf-ubuntu-python-3_6-xenial.list <==
deb http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial main
# deb-src http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial main

==> /etc/apt/sources.list.d/jonathonf-ubuntu-python-3_6-xenial.list.distUpgrade <==
deb http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial main
# deb-src http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-wily.list <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main
# deb-src http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-wily.list.distUpgrade <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main
# deb-src http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-wily.list.save <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main
# deb-src http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu wily main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-xenial.list <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu xenial main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu xenial main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-oldstable-xenial.list.save <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-oldstable/ubuntu xenial main

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-wily.list <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-wily.list.distUpgrade <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-wily.list.save <==
# deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-pan-xenial.list <==
# deb http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main
# deb-src http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-pan-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main
# deb-src http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-pan-xenial.list.save <==
# deb http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main
# deb-src http://ppa.launchpad.net/klaus-vormweg/pan/ubuntu xenial main

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-ppa-vivid.list <==
# deb http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-ppa-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/klaus-vormweg-ubuntu-ppa-vivid.list.save <==
# deb http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/kritalime-ubuntu-ppa-xenial.list <==
# deb http://ppa.launchpad.net/kritalime/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/kritalime-ubuntu-ppa-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/kritalime/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/kritalime-ubuntu-ppa-xenial.list.save <==
# deb http://ppa.launchpad.net/kritalime/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.save <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

==> /etc/apt/sources.list.d/opera.list <==
# deb http://deb.opera.com/opera-stable/ stable non-free

==> /etc/apt/sources.list.d/opera.list.distUpgrade <==
# deb http://deb.opera.com/opera-stable/ stable non-free

==> /etc/apt/sources.list.d/opera.list.save <==
# deb http://deb.opera.com/opera-stable/ stable non-free

==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/sunab-ubuntu-kdenlive-release-vivid.list <==
# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu vivid main

==> /etc/apt/sources.list.d/sunab-ubuntu-kdenlive-release-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu vivid main

==> /etc/apt/sources.list.d/sunab-ubuntu-kdenlive-release-vivid.list.save <==
# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu vivid main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-utopic.list <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-utopic.list.save <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu utopic main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-vivid.list <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-vivid.list.save <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-wily.list <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu xenial main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-wily.list.distUpgrade <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu xenial main

==> /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-wily.list.save <==
# deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu xenial main

==> /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-vivid.list <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-vivid.list.save <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ubuntu-mozilla-daily-ubuntu-firefox-aurora-xenial.list <==
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial main

==> /etc/apt/sources.list.d/ubuntu-mozilla-daily-ubuntu-firefox-aurora-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial main

==> /etc/apt/sources.list.d/ubuntu-mozilla-daily-ubuntu-firefox-aurora-xenial.list.save <==
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial main

==> /etc/apt/sources.list.d/videolan-ubuntu-stable-daily-vivid.list <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/videolan-ubuntu-stable-daily-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/videolan-ubuntu-stable-daily-vivid.list.save <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu vivid main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.save <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid

==> /etc/apt/sources.list.d/xenial-partner.list <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
# deb http://archive.canonical.com/ubuntu xenial partner

==> /etc/apt/sources.list.d/xenial-partner.list.distUpgrade <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
# deb http://archive.canonical.com/ubuntu xenial partner

==> /etc/apt/sources.list.d/xenial-partner.list.save <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
# deb http://archive.canonical.com/ubuntu xenial partner


$ cat /etc/issue
Ubuntu 16.04.4 LTS \n \l


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial


```

---

### Post by Bashing-om on 2018-03-07
eezacque; HoKay .. not yet !

The python culprit:
> 
==> /etc/apt/sources.list.d/jonathonf-ubuntu-python-3_6-xenial.list <==
deb [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial main



But not sure how this  one
> 
==> /etc/apt/sources.list.d/jonathonf-ubuntu-python-3_6-xenial.list.distUpgrade <==
deb [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial main

is going to play out - yet.

Let's try and revert python back to xenial's version:
```

sudo apt install ppa-purge
sudo ppa-purge ppa:jonathonf/python-3.6

```

If that runs clean then:
I will be interested to see if ppa-purge now removes the source(s)
OR if still required to manually remove the entries:
show a new:
```

tail -v -n +1 /etc/apt/sources.list.d/*

```
and we see what the next step is to be.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2018-03-07
For "upgrade" to work you have to first restore the system to its prestine state by first puring all your ppas with ppa-purge (not just disabling them but to downgrade all packages to their repository version) and you have to get rid of third party programs including proprietary drivers (if any), then wait for a few hours if you are lucky that nothing goes wrong (like you lose internet connection or the cat trips over the power cable) 

Instead of trying to trouble shoot an "upgrade" I suggest the MUCH easier way of  just backing up your data and do a fresh install.  A lot faster and safer.

---

### Post by eezacque on 2018-03-08
> **Bashing-om said:**
> eezacque; HoKay .. not yet !

The python culprit:


Don't think this is the problem: when I found that there was a problem with python, I added this ppa to the system to install 3.6, only to conclude this didn't solve anything, and the problem sits deeper, probably. Should have mentioned this. Anyways, I didn't know about ppa purge, so I'll work through this first and then get back to you.

EDIT: How awkward. Purging the python 3.6 ppa caused blender to be removed, after which the update process successfully calculated the changes. Looks like the blender installation introduced something rotten. I haven't yet tried to continue the install, will let you know.

---

### Post by eezacque on 2018-03-08
Solved. Looks like a recent blender upgrade seriously screwed up package structure where python 3.6 is involved. The upgrade to 17.10 finished without problems! 

Bashing-om: thanks an awful lot for sorting me out!

---

### Post by monkeybrain20122 on 2018-03-08
You can just download a binary from blender's website, extract, click blender and that's it. No installation required, no need to complicate life and install an old version from the package system. ;)

---

### Post by Bashing-om on 2018-03-08
eezacque; Yo !

> **eezacque said:**
> Solved. Looks like a recent blender upgrade seriously screwed up package structure where python 3.6 is involved. The upgrade to 17.10 finished without problems! 

Bashing-om: thanks an awful lot for sorting me out!

You do good work -
Glad to assist

[INDENT][INDENT][INDENT]help is what we do
[/INDENT][/INDENT][/INDENT]

---

