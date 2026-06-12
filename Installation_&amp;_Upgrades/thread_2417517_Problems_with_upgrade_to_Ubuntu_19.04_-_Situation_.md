---
title: "Problems with upgrade to Ubuntu 19.04 - Situation deteriorating."
date: 2019-04-23
forum: Installation &amp; Upgrades
---

### Post by carlo-sanguineti on 2019-04-23
After 5 days out of home, today I was back, and the PC, after suggesting me an update (done without problem), proposed me the 19.04 upgrade. I tried to do this but the upgrade failed with these two warnings:


E:Repository 'http://deb.opera.com/opera stable InRelease' changed its 'Origin' value from 'Opera Software ASA' to 'Opera Software AS', W:This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
E:The repository 'http://archive.canonical.com/ubuntu saucy Release' no longer has a Release file.


At first I removed Opera, I don't use it anymore since it was amazingly slow to start. I removed also Skype that I had installed twice.
the second message was still making me fail the upgrade:


E:The repository 'http://archive.canonical.com/ubuntu saucy Release' no longer has a Release file.


I did what is suggested oon the link:
[https://askubuntu.com/questions/973520/apt-update-error-the-repository-http-us-archive-ubuntu-com-ubuntu-saucy-rele](https://askubuntu.com/questions/973520/apt-update-error-the-repository-http-us-archive-ubuntu-com-ubuntu-saucy-rele)
despite it is not quite new. It was the only suggestion I found on the net.


I restarted the computer and I received again a suggestion for an update. This update failed with the following message:


Ubuntu The installation or removal of a software package failed. It is something so fast that I was unable to copy the details.


No way, now to reach the request to upgrade the System.


I reinstalled Opera, and Skype, and disinstalled them again with no success.


I am non a skillful Ubuntu user, so I would like to have a step-by-step help to clean the problems in my computer and upgrade Ubuntu to 19.04.


Many thanks in advance,


Carlo

---

### Post by cruzer001 on 2019-04-23
Saucy?  If your install is that old you should really consider a fresh install and not a upgrade.

But let us have a look at what you have for a sources list.   Please post the output of...
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by Bashing-om on 2019-04-23
cruzer001; Hello -

Let's "suppose" those problematic sources are still in the system and still in effect,
Post back - between code tags - the out puts of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and we see what it is going to take to make it not so.

[INDENT][INDENT]clean - we like clean :)
[/INDENT][/INDENT]

---

### Post by carlo-sanguineti on 2019-04-24
Hi Thank you first for your kind help.
My current Ubuntu version is 18.10, I really have no idea why I have this reference to SAUCY.

The command you ask me to do gave the following output:

[COLOR=#000000]```
[/COLOR]~$ cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed restricted main universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed restricted main universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
/etc/apt/sources.list.d/behda-ppa-trusty.list
/etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list
/etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list
/etc/apt/sources.list.d/canonical_partner.list
/etc/apt/sources.list.d/diesch-testing-trusty.list
/etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list
/etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/jd-team-jdownloader-saucy.list
/etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list
/etc/apt/sources.list.d/opera.list
/etc/apt/sources.list.d/opera-stable.list
/etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list
/etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list
/etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list
/etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list
/etc/apt/sources.list.d/skype-stable.list
/etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list
/etc/apt/sources.list.d/strukturag-libde265-trusty.list
/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list
/etc/apt/sources.list.d/videolan-master-daily-saucy.list
/etc/apt/sources.list.d/vivaldi-beta.list
/etc/apt/sources.list.d/vivaldi.list
/etc/apt/sources.list.d/vivaldi-snapshot.list
/etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list
/etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list
[COLOR=#000000]
```[/COLOR]

The second command gave this output:

[COLOR=#000000]```
[/COLOR]~$ cat -n /etc/apt/sources.list
     1    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
     2    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
     3    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
     4    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
     7    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
     8    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
     9    #deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed restricted main universe multiverse
    10    #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed restricted main universe multiverse
    11    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    12    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
[COLOR=#000000]
```[/COLOR]~$

Finally, this is the third output

[COLOR=#000000]```
[/COLOR]~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/behda-ppa-trusty.list <==


==> /etc/apt/sources.list.d/behda-ppa-trusty.list.save <==


==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list <==
# deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) saucy main


==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list.distUpgrade <==
# deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) saucy main


==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list.save <==
# deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) saucy main


==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <==
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.distUpgrade <==
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <==
# deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/canonical_partner.list <==
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner


==> /etc/apt/sources.list.d/canonical_partner.list.distUpgrade <==
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner


==> /etc/apt/sources.list.d/canonical_partner.list.save <==
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) bionic partner


==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==
# deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list.distUpgrade <==
# deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==
# deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main


==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list <==
# deb [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main


==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list.distUpgrade <==
# deb [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main


==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list.save <==
# deb [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main
# deb-src [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu) utopic main


==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list <==
# deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) utopic main


==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list.distUpgrade <==
# deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) utopic main


==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list.save <==
# deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) utopic main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 


==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list <==
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) saucy main


==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list.distUpgrade <==
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) saucy main


==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list.save <==
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) saucy main


==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list <==
# deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) utopic main


==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list.distUpgrade <==
# deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) utopic main


==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list.save <==
# deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) utopic main


==> /etc/apt/sources.list.d/opera.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases)


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.


# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases)


==> /etc/apt/sources.list.d/opera.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases)


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.


# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases)


==> /etc/apt/sources.list.d/opera.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases)


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.


# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases)


==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to xenial


==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to xenial


==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to xenial


==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list <==
# deb [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) xenial main


==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list.distUpgrade <==
# deb [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) xenial main


==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list.save <==
# deb [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) xenial main


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list.distUpgrade <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list.save <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list.distUpgrade <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list.save <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list <==
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list.distUpgrade <==
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list.save <==
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) artful main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list <==
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) bionic main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list.distUpgrade <==
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) bionic main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list <==
# deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) cosmic main # disabled on upgrade to artful disabled on upgrade to bionic disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list.distUpgrade <==
# deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) cosmic main # disabled on upgrade to artful disabled on upgrade to bionic disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main


==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list.save <==
# deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) bionic main # disabled on upgrade to artful disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main
# deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) zesty main


==> /etc/apt/sources.list.d/skype-stable.list <==
# deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/skype-stable.list.distUpgrade <==
# deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/skype-stable.list.save <==
# deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list <==
# deb [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) utopic main


==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list.distUpgrade <==
# deb [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) utopic main


==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list.save <==
# deb [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu](http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu) utopic main


==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list <==
# deb [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main


==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.distUpgrade <==
# deb [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main


==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.save <==
# deb [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) utopic main # disabled on upgrade to utopic
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu) trusty main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.distUpgrade <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.save <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) yakkety main # disabled on upgrade to yakkety
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) vivid main # disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.distUpgrade <==
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) vivid main # disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) vivid main # disabled on upgrade to utopic disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list <==
# deb [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) saucy main


==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list.distUpgrade <==
# deb [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) saucy main


==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list.save <==
# deb [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) trusty main # disabled on upgrade to trusty disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) saucy main


==> /etc/apt/sources.list.d/vivaldi-beta.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/beta/deb/](http://repo.vivaldi.com/beta/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/vivaldi-beta.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/beta/deb/](http://repo.vivaldi.com/beta/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/vivaldi-beta.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/beta/deb/](http://repo.vivaldi.com/beta/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/vivaldi.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main


==> /etc/apt/sources.list.d/vivaldi.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main


==> /etc/apt/sources.list.d/vivaldi.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main


==> /etc/apt/sources.list.d/vivaldi-snapshot.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/snapshot/deb/](http://repo.vivaldi.com/snapshot/deb/) stable main


==> /etc/apt/sources.list.d/vivaldi-snapshot.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/snapshot/deb/](http://repo.vivaldi.com/snapshot/deb/) stable main


==> /etc/apt/sources.list.d/vivaldi-snapshot.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://repo.vivaldi.com/snapshot/deb/](http://repo.vivaldi.com/snapshot/deb/) stable main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) utopic main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.distUpgrade <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) utopic main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.save <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) vivid main # disabled on upgrade to vivid
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) utopic main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) wily main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.distUpgrade <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) wily main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.save <==
# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) wily main
[COLOR=#000000]
```[/COLOR]~$ 

Many thanks again

One more thing:
Since you will be my "doctor" in this session, I must tell you I live in Italy, so my time is GMT+1 (+Legal Time). And... I was born in 1956, but still willing to learn!
I deeply dislike Windows (I am obliged to use it at work, until July, then I will go in retirement :-) ) and at home I have only Ubuntu.

Carlo

---

### Post by cruzer001 on 2019-04-24
You say that your on 18.10, but your sources.list says your running Xenial 16.04.

You have a tall stack of inactive PPAs in sources.list.d and a few active ones that do not belong there.

I would suggest removing all PPAs and then trying another upgrade, but lets wait and see what Bashing-om has to say.

Italy!  I lived in Vicarello for a few years :)

---

### Post by carlo-sanguineti on 2019-04-24
Just now I did
lsb_release -a
```
lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.10
Release:	18.10
Codename:	cosmic

```

And the screenshot of my ubuntu is:[ATTACH=CONFIG]283097[/ATTACH]

I did all the upgrades since I have Ubuntu. It maybe the first version on THIS computer was on 2016.

---

### Post by Impavidus on 2019-04-24
Something weird is going on. The only explanantion I can think of right now is that you upgraded to 18.10, then restored the software sources for 16.04 from a backup (leading to almost no updates at all, as the updated packages for 16.04 have earlier version numbers than the outdated packages on 18.10). Actually, I can imagine a failed upgrade doing such a thing when a backup of the 16.04 sources.list was still around.

Just to check this theory, what do you get from```
apt-cache policy base-files
```Version 9.4ubuntu4.8 is the one belonging to your software sources, version 10.1ubuntu7 the one that should tell you that you're running Ubuntu 18.10.

---

### Post by #&amp;thj^% on 2019-04-24
Well I at this point agree with Impavidus something very wonky here >> If you don't show the correct version Impavidus is showing like:
```
apt policy base-files
base-files:
  Installed: 10.1ubuntu9
  Candidate: 10.1ubuntu9
  Version table:
 *** 10.1ubuntu9 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status

```
I have used **"sed"** for a number of years now changing my source lists, with very few problems. **I don't use "do-release-upgrade -d"** any more.
```
 sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
```
Update and Upgrade again:
```
sudo apt update 
sudo apt full-upgrade
```
Before enabling all your PPA's first check they are supported for (19.04)

---

### Post by Bashing-om on 2019-04-24
carlo-sanguineti - Hey 

In addition to the ups excellent advisements will be good to know the gpg-key situation. There is a 40 key limit,
```

ls /etc/apt/trusted.gpg.d | wc -l

```

Pending what "apt-cache policy base-files" reveals for which direction we take off in.

takes a lot to clean up a big mess

---

### Post by carlo-sanguineti on 2019-04-24
Hello,

the output is:
```
:~$ apt-cache policy base-filesbase-files:
  Installed: 10.1ubuntu7
  Candidate: 10.1ubuntu7
  Version table:
 *** 10.1ubuntu7 100
        100 /var/lib/dpkg/status
     9.4ubuntu4.8 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     9.4ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```
Thank You for your help
Carlo

---

### Post by carlo-sanguineti on 2019-04-24
the outpus is 
```

:~$ ls /etc/apt/trusted.gpg.d | wc -l
31

```

---

### Post by carlo-sanguineti on 2019-04-24
I did then 
```

sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list

```
No output


The I did
sudo apt update 
The outpus was:
```

~$ sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
[sudo] password for carlos: 
carlos@carlo-All-Series:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]       
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:5 http://archive.canonical.com/ubuntu cosmic InRelease                     
Get:6 http://deb.opera.com/opera stable InRelease [2,591 B]                    
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                     
Get:8 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [254 kB]
Get:11 http://deb.opera.com/opera stable/non-free amd64 Packages [1,802 B]     
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [335 kB]   
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [945 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [819 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [378 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 48x48 Icons [14.6 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [229 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [683 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [746 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [310 kB]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [252 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [350 kB]
Get:25 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,968 B]
Get:26 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]
Get:27 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:28 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,104 B]
Get:29 http://archive.ubuntu.com/ubuntu xenial-security/universe Sources [105 kB]
Get:30 http://archive.ubuntu.com/ubuntu xenial-security/main Sources [145 kB]
Get:31 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages [530 kB]
Get:32 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages [638 kB]
Get:33 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.9 kB]
Get:34 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 48x48 Icons [14.6 kB]
Get:35 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [67.1 kB]
Get:36 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [378 kB]
Get:37 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [434 kB]
Get:38 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en [176 kB]
Get:39 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [116 kB]
Get:40 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [173 kB]
Get:41 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 8,839 kB in 2s (4,250 kB/s)                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```


Immediately after this I was requested by the system to perform an update, that failed again.


After this I did


sudo apt full-upgrade


The outpus was:
```

:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core gnome-exe-thumbnailer icoutils
  libgsf-1-114 libgsf-1-common libmsi0 libp11-kit-gnome-keyring:i386
  libpng12-0:i386 msitools wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  wine
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Since it was requested, I did a sudo apt autoremove

The output was:
```

:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fonts-horai-umefont fonts-unfonts-core gnome-exe-thumbnailer icoutils
  libgsf-1-114 libgsf-1-common libmsi0 libp11-kit-gnome-keyring:i386
  libpng12-0:i386 msitools wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
0 upgraded, 0 newly installed, 13 to remove and 1 not upgraded.
After this operation, 208 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 296478 files and directories currently installed.)
Removing fonts-horai-umefont (590-1) ...
dpkg: warning: while removing fonts-horai-umefont, directory '/usr/share/fonts/truetype/horai-umefont' not empty so not removed
Removing fonts-unfonts-core (1.0.3.is.1.0.2-080608-10ubuntu1) ...
Removing gnome-exe-thumbnailer (0.9.3-2ubuntu0.16.04.1) ...
Removing icoutils (0.31.0-3) ...
Removing msitools (0.95-1) ...
Removing libmsi0:amd64 (0.95-1) ...
Removing libgsf-1-114:amd64 (1.14.36-1) ...
Removing libgsf-1-common (1.14.36-1) ...
Removing libp11-kit-gnome-keyring:i386 (3.18.3-0ubuntu2.1) ...
Removing libpng12-0:i386 (1.2.54-1ubuntu1.1) ...
Removing wine-gecko2.21:amd64 (2.21-0ubuntu1) ...
Removing wine-gecko2.21:i386 (2.21-0ubuntu1) ...
Removing wine-mono0.0.8 (0.0.8-0ubuntu1) ...
Processing triggers for libc-bin (2.28-0ubuntu1) ...
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directory
Processing triggers for man-db (2.8.4-2) ...
Processing triggers for fontconfig (2.13.0-5ubuntu3) ...

```

---

### Post by Bashing-om on 2019-04-24
carlo-sanguineti; Ouch !

My output for 18.04 base-files:
> 
sysop@x1804mini:~$ apt-cache policy base-files
base-files:
  Installed: 10.1ubuntu2.4
  Candidate: 10.1ubuntu2.4
  Version table:
 *** 10.1ubuntu2.4 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     10.1ubuntu2.2 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-security/main amd64 Packages
     10.1ubuntu2 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic/main amd64 Packages
sysop@x1804mini:~$ 


I feel at this point my skill levels to address fixing this install is very lacking.
I will be most happy to lurk, wait and learn here :)

[INDENT][INDENT]this time, not what is
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2019-04-24
> **carlo-sanguineti said:**
> the outpus is 
```

:~$ ls /etc/apt/trusted.gpg.d | wc -l
31

```

Yike's Good Grief :confused:
 Bashing-om is taking you in safe direction as per:

```
ls /etc/apt/trusted.gpg.d
brandonsnider_ubuntu_cdrtools.gpg  ubuntu-keyring-2012-archive.gpg
brave-browser-release.gpg          ubuntu-keyring-2012-cdimage.gpg
tn-6_ubuntu_xcdroast.gpg           ubuntu-keyring-2018-archive.gpg

```
I do a lot and I have only six (6)

---

### Post by carlo-sanguineti on 2019-04-24
Thank you a lot anyway...
Carlo

---

### Post by carlo-sanguineti on 2019-04-24
Hi 1fallen!

My outpus was longer:

```

:~$ ls /etc/apt/trusted.gpg.d
caffeine-developers-ppa.gpg           starws-box_ubuntu_deadbeef-player.gpg
caffeine-developers-ppa.gpg~          starws-box_ubuntu_deadbeef-player.gpg~
diesch-testing.gpg                    strukturag-libde265.gpg
diesch-testing.gpg~                   strukturag-libde265.gpg~
djcj_ubuntu_vlc-stable.gpg            team-xbmc_ubuntu_ppa.gpg
djcj_ubuntu_vlc-stable.gpg~           team-xbmc_ubuntu_ppa.gpg~
flacon_ubuntu_ppa.gpg                 ubuntu-keyring-2012-archive.gpg
flacon_ubuntu_ppa.gpg~                ubuntu-keyring-2012-cdimage.gpg
jd-team-jdownloader.gpg               ubuntu-keyring-2018-archive.gpg
jd-team-jdownloader.gpg~              ubuntu-wine-ppa.gpg
mc3man_ubuntu_trusty-media.gpg        ubuntu-wine-ppa.gpg~
mc3man_ubuntu_trusty-media.gpg~       videolan-master-daily.gpg
plushuang-tw_ubuntu_uget-stable.gpg   videolan-master-daily.gpg~
plushuang-tw_ubuntu_uget-stable.gpg~  webupd8team_ubuntu_java.gpg
rvm_ubuntu_smplayer.gpg               webupd8team_ubuntu_java.gpg~
rvm_ubuntu_smplayer.gpg~

```

---

### Post by #&amp;thj^% on 2019-04-24
> **carlo-sanguineti said:**
> I did then 
```

sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list

```

Yep that would of failed, we seem to be working with 16.04 xenial here so:
```
 sudo sed -i 's/xenial/disco/g' /etc/apt/sources.list
```
Update and Upgrade:
```
sudo apt update 
sudo apt full-upgrade
```
EDIT: If this works at all, it will be a Bloody Miracle.:roll: You need to weed through those and slim down to the only needed PPA's.

---

### Post by carlo-sanguineti on 2019-04-24
Ok,

on
```

sudo sed -i 's/xenial/disco/g' /etc/apt/sources.list

```
no output

On sudo apt update
```

:~$ sudo apt update
Hit:1 http://deb.opera.com/opera stable InRelease
Get:2 http://archive.canonical.com/ubuntu disco InRelease [10.9 kB]            
Hit:3 http://archive.canonical.com/ubuntu cosmic InRelease                     
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:5 http://archive.ubuntu.com/ubuntu disco InRelease [257 kB]          
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Get:7 http://archive.canonical.com/ubuntu disco/partner Sources [1,404 B]      
Get:8 http://archive.canonical.com/ubuntu disco/partner amd64 Packages [1,596 B]
Get:9 http://archive.canonical.com/ubuntu disco/partner i386 Packages [1,592 B]
Get:10 http://archive.canonical.com/ubuntu disco/partner Translation-en [708 B]
Get:12 http://archive.ubuntu.com/ubuntu disco-updates InRelease [88.4 kB]      
Get:13 http://archive.ubuntu.com/ubuntu disco-backports InRelease [66.2 kB]
Get:14 http://archive.ubuntu.com/ubuntu disco-security InRelease [79.7 kB]
Get:15 http://archive.ubuntu.com/ubuntu disco/restricted Sources [6,412 B]
Get:16 http://archive.ubuntu.com/ubuntu disco/universe Sources [9,688 kB]
Get:17 http://archive.ubuntu.com/ubuntu disco/main Sources [838 kB]            
Get:18 http://archive.ubuntu.com/ubuntu disco/multiverse Sources [187 kB]
Get:19 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages [995 kB]
Get:20 http://archive.ubuntu.com/ubuntu disco/main i386 Packages [981 kB]
Get:21 http://archive.ubuntu.com/ubuntu disco/main Translation-en [509 kB]
Get:22 http://archive.ubuntu.com/ubuntu disco/main amd64 DEP-11 Metadata [499 kB]
Get:23 http://archive.ubuntu.com/ubuntu disco/main DEP-11 48x48 Icons [97.2 kB]
Get:24 http://archive.ubuntu.com/ubuntu disco/main DEP-11 64x64 Icons [179 kB]
Get:25 http://archive.ubuntu.com/ubuntu disco/main amd64 c-n-f Metadata [30.0 kB]
Get:26 http://archive.ubuntu.com/ubuntu disco/restricted amd64 Packages [14.0 kB]
Get:27 http://archive.ubuntu.com/ubuntu disco/restricted i386 Packages [11.1 kB]
Get:28 http://archive.ubuntu.com/ubuntu disco/restricted Translation-en [4,960 B]
Get:29 http://archive.ubuntu.com/ubuntu disco/restricted amd64 c-n-f Metadata [348 B]
Get:30 http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages [9,065 kB]
Get:31 http://archive.ubuntu.com/ubuntu disco/universe i386 Packages [9,008 kB]
Get:32 http://archive.ubuntu.com/ubuntu disco/universe Translation-en [5,251 kB]
Get:33 http://archive.ubuntu.com/ubuntu disco/universe amd64 DEP-11 Metadata [3,546 kB]
Get:34 http://archive.ubuntu.com/ubuntu disco/universe DEP-11 48x48 Icons [2,759 kB]
Get:35 http://archive.ubuntu.com/ubuntu disco/universe DEP-11 64x64 Icons [8,369 kB]
Get:36 http://archive.ubuntu.com/ubuntu disco/universe amd64 c-n-f Metadata [277 kB]
Get:37 http://archive.ubuntu.com/ubuntu disco/multiverse i386 Packages [145 kB]
Get:38 http://archive.ubuntu.com/ubuntu disco/multiverse amd64 Packages [157 kB]
Get:39 http://archive.ubuntu.com/ubuntu disco/multiverse Translation-en [112 kB]
Get:40 http://archive.ubuntu.com/ubuntu disco/multiverse amd64 DEP-11 Metadata [51.3 kB]
Get:41 http://archive.ubuntu.com/ubuntu disco/multiverse DEP-11 48x48 Icons [10.8 kB]
Get:42 http://archive.ubuntu.com/ubuntu disco/multiverse DEP-11 64x64 Icons [221 kB]
Get:43 http://archive.ubuntu.com/ubuntu disco/multiverse amd64 c-n-f Metadata [9,348 B]
Get:44 http://archive.ubuntu.com/ubuntu disco-updates/main Sources [6,976 B]   
Get:45 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages [15.4 kB]
Get:46 http://archive.ubuntu.com/ubuntu disco-updates/main i386 Packages [15.4 kB]
Get:47 http://archive.ubuntu.com/ubuntu disco-updates/main Translation-en [5,836 B]
Get:48 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 DEP-11 Metadata [21.9 kB]
Get:49 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 48x48 Icons [1,024 B]
Get:50 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 64x64 Icons [948 B]
Get:51 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 c-n-f Metadata [804 B]
Get:52 http://archive.ubuntu.com/ubuntu disco-updates/restricted amd64 c-n-f Metadata [116 B]
Get:53 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 Packages [7,340 B]
Get:54 http://archive.ubuntu.com/ubuntu disco-updates/universe i386 Packages [7,340 B]
Get:55 http://archive.ubuntu.com/ubuntu disco-updates/universe Translation-en [3,456 B]
Get:56 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 c-n-f Metadata [304 B]
Get:57 http://archive.ubuntu.com/ubuntu disco-updates/multiverse amd64 c-n-f Metadata [116 B]
Get:58 http://archive.ubuntu.com/ubuntu disco-security/main Sources [4,920 B]  
Get:59 http://archive.ubuntu.com/ubuntu disco-security/main amd64 Packages [10.8 kB]
Get:60 http://archive.ubuntu.com/ubuntu disco-security/main i386 Packages [10.9 kB]
Get:61 http://archive.ubuntu.com/ubuntu disco-security/main Translation-en [4,780 B]
Get:62 http://archive.ubuntu.com/ubuntu disco-security/main amd64 c-n-f Metadata [588 B]
Get:63 http://archive.ubuntu.com/ubuntu disco-security/restricted amd64 c-n-f Metadata [116 B]
Get:64 http://archive.ubuntu.com/ubuntu disco-security/universe i386 Packages [6,656 B]
Get:65 http://archive.ubuntu.com/ubuntu disco-security/universe amd64 Packages [6,656 B]
Get:66 http://archive.ubuntu.com/ubuntu disco-security/universe Translation-en [3,132 B]
Get:67 http://archive.ubuntu.com/ubuntu disco-security/universe amd64 c-n-f Metadata [272 B]
Get:68 http://archive.ubuntu.com/ubuntu disco-security/multiverse amd64 c-n-f Metadata [116 B]
Fetched 53.7 MB in 9s (6,313 kB/s)                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2192 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

on sudo apt full-upgrade
is doing a lot. I will post the code when it is complete

---

### Post by #&amp;thj^% on 2019-04-24
May the Force be with you. Fingers Crossed.

---

### Post by carlo-sanguineti on 2019-04-24
After a crash, a repetition of the command, and a two steps upgrade (? - the system told it was not complete), and two errors after the restart...

[ATTACH=CONFIG]283102[/ATTACH]

:-)

Thank you a lot!

There is something more I must do now?

---

### Post by carlo-sanguineti on 2019-04-24
I tried to post both the codes of the two attempts of ```
sudo apt full-upgrade
```, but it looks I'm not able to do it, it maybe are too long.

Since here in Italy is 02:15 AM, I should go to sleep and I will duly perform any suggest you will propose me tomorrow...
I'm 63 and I need some sleep...

Thank you again

See you tomorrow,

Carlo

---

### Post by #&amp;thj^% on 2019-04-24
Yes get rid of those un-needed PPA's. :)
And now check for clutter with:
```
sudo apt autoremove
```
Piacere di conoscerla & Prendersi cura ;)

---

### Post by carlo-sanguineti on 2019-04-24
Still awaken, done!

```

:~$ sudo apt autoremove
[sudo] password for carlos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gcc-8-base:i386 gir1.2-gtksource-3.0 gir1.2-harfbuzz-0.0 gir1.2-mutter-3
  libavcodec-ffmpeg56 libavformat-ffmpeg56 libavutil-ffmpeg54 libbind9-160
  libcfitsio5 libdns-export1102 libdns1102 libedataserver-1.2-23
  libgdbm-compat4:i386 libgdbm5 libgdbm5:i386 libgdbm6:i386 libgmime-3.0-0
  libgraphite2-dev libharfbuzz-dev libharfbuzz-gobject0 libhunspell-1.6-0
  libicu-le-hb-dev libicu-le-hb0 libicu60:i386 libiculx60 libieee1284-3:i386
  libipt2 libirs160 libisc-export169 libisc169 libisccc160 libisccfg160
  libkf5auth5 libllvm7 libllvm7:i386 liblouis16 liblwres160 libminizip1
  libmutter-3-0 libmysqlclient20:i386 libnfs11 libntfs-3g88 libopencv-core3.2
  libopencv-imgproc3.2 liborcus-0.13-0 libpci3:i386 libperl5.26
  libperl5.26:i386 libperl5.28:i386 libplacebo5 libpodofo0.9.5 libpoppler79
  libprotobuf-lite10 libprotobuf10 libprotoc10 libpython3.6
  libpython3.6-minimal libpython3.6-stdlib libqt5webengine-data
  libqt5webenginecore5 libqt5webenginewidgets5 libraw16 libre2-4 libre2-5
  libreadline6 libreadline7 libsane:i386 libsane1 libsane1:i386 libsnmp30:i386
  libswresample-ffmpeg1 libtbb2 libtiff5-dev libvpx3 libwayland-server0:i386
  libwebp5 libx264-148 libx264-152 libx265-160 libx265-79 libzip4
  linux-headers-4.18.0-16 linux-headers-4.18.0-16-generic
  linux-image-4.18.0-16-generic linux-modules-4.18.0-16-generic
  linux-modules-extra-4.18.0-16-generic perl-modules-5.26 python-compizconfig
  python-talloc python-tdb python3.6 python3.6-minimal
0 upgraded, 0 newly installed, 92 to remove and 0 not upgraded.
After this operation, 832 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 339542 files and directories currently installed.)
Removing gcc-8-base:i386 (8.3.0-6ubuntu1) ...
Removing gir1.2-gtksource-3.0:amd64 (3.24.10-1) ...
Removing libicu-le-hb-dev:amd64 (1.0.3+git180724-3) ...
Removing libharfbuzz-dev:amd64 (2.3.1-1) ...
Removing gir1.2-harfbuzz-0.0:amd64 (2.3.1-1) ...
Removing gir1.2-mutter-3:amd64 (3.30.2-1~ubuntu18.10.4) ...
Removing libavformat-ffmpeg56:amd64 (7:2.8.15-0ubuntu0.16.04.1) ...
Removing libavcodec-ffmpeg56:amd64 (7:2.8.15-0ubuntu0.16.04.1) ...
Removing libswresample-ffmpeg1:amd64 (7:2.8.15-0ubuntu0.16.04.1) ...
Removing libavutil-ffmpeg54:amd64 (7:2.8.15-0ubuntu0.16.04.1) ...
Removing libbind9-160:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libcfitsio5:amd64 (3.430-3) ...
Removing libdns-export1102 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libirs160:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libisccfg160:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libdns1102:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libedataserver-1.2-23:amd64 (3.30.1-1build1) ...
Removing libsane1:i386 (1.0.27-3.2ubuntu1) ...
Removing libsane:i386 (1.0.27-3.2ubuntu1) ...
Removing libsnmp30:i386 (5.7.3+dfsg-5ubuntu1) ...
Removing libperl5.28:i386 (5.28.1-6) ...
Removing libperl5.26:i386 (5.26.2-7ubuntu0.1) ...
Removing libgdbm-compat4:i386 (1.18.1-4) ...
Removing libperl5.26:amd64 (5.26.2-7ubuntu0.1) ...
Removing libgdbm5:amd64 (1.14.1-6) ...
Removing libgdbm5:i386 (1.14.1-6) ...
Removing libgdbm6:i386 (1.18.1-4) ...
Removing libgmime-3.0-0:amd64 (3.2.1-1) ...
Removing libgraphite2-dev:amd64 (1.3.13-7) ...
Removing libharfbuzz-gobject0:amd64 (2.3.1-1) ...
Removing libhunspell-1.6-0:amd64 (1.6.2-1build1) ...
Removing libiculx60:amd64 (60.2-6ubuntu1) ...
Removing libicu-le-hb0:amd64 (1.0.3+git180724-3) ...
Removing libicu60:i386 (60.2-6ubuntu1) ...
Removing libieee1284-3:i386 (0.2.11-13) ...
Removing libipt2 (2.0-2) ...
Removing libisc-export169:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libisccc160:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libisc169:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libkf5auth5:amd64 (5.56.0-0ubuntu4) ...
Removing libllvm7:i386 (1:7.0.1-8) ...
Removing libllvm7:amd64 (1:7.0.1-8) ...
Removing liblouis16:amd64 (3.6.0-3ubuntu1) ...
Removing liblwres160:amd64 (1:9.11.4+dfsg-3ubuntu5.1) ...
Removing libqt5webenginewidgets5:amd64 (5.12.2+dfsg-2ubuntu1) ...
Removing libqt5webenginecore5:amd64 (5.12.2+dfsg-2ubuntu1) ...
Removing libminizip1:amd64 (1.1-8build1) ...
Removing libmutter-3-0:amd64 (3.30.2-1~ubuntu18.10.4) ...
Removing libmysqlclient20:i386 (5.7.25-1) ...
Removing libnfs11:amd64 (2.0.0-1~exp1) ...
Removing libntfs-3g88 (1:2017.3.23-2ubuntu0.18.10.2) ...
Removing libopencv-imgproc3.2:amd64 (3.2.0+dfsg-6) ...
Removing libopencv-core3.2:amd64 (3.2.0+dfsg-6) ...
Removing liborcus-0.13-0:amd64 (0.13.4-6) ...
Removing libpci3:i386 (1:3.5.2-1ubuntu2) ...
Removing libplacebo5:amd64 (0.5.0-2) ...
Removing libpodofo0.9.5 (0.9.5-11) ...
Removing libpoppler79:amd64 (0.68.0-0ubuntu1.6) ...
Removing libprotobuf-lite10:amd64 (3.0.0-9.1ubuntu3) ...
Removing libprotoc10:amd64 (3.0.0-9.1ubuntu3) ...
Removing libprotobuf10:amd64 (3.0.0-9.1ubuntu3) ...
Removing libpython3.6:amd64 (3.6.7-1~18.10) ...
Removing python3.6 (3.6.7-1~18.10) ...
Removing libpython3.6-stdlib:amd64 (3.6.7-1~18.10) ...
Removing python3.6-minimal (3.6.7-1~18.10) ...
Unlinking and removing bytecode for runtime python3.6
Removing libpython3.6-minimal:amd64 (3.6.7-1~18.10) ...
Removing libqt5webengine-data (5.12.2+dfsg-2ubuntu1) ...
Removing libraw16:amd64 (0.18.13-1) ...
Removing libre2-4:amd64 (20180701+dfsg-1) ...
Removing libre2-5:amd64 (20190101+dfsg-2) ...
Removing libreadline6:amd64 (6.3-8ubuntu2) ...
Removing libreadline7:amd64 (7.0-5) ...
Removing libsane1:amd64 (1.0.27-3.2ubuntu1) ...
Removing libtbb2:amd64 (2018~U6-4) ...
Removing libtiff5-dev (4.0.10-4) ...
Removing libvpx3:amd64 (1.5.0-2ubuntu1) ...
Removing libwayland-server0:i386 (1.16.0-1ubuntu2) ...
Removing libwebp5:amd64 (0.4.4-1) ...
Removing libx264-148:amd64 (2:0.148.2643+git5c65704-1) ...
Removing libx264-152:amd64 (2:0.152.2854+gite9a5903-2build1) ...
Removing libx265-160:amd64 (2.8-4) ...
Removing libx265-79:amd64 (1.9-3) ...
Removing libzip4:amd64 (1.1.2-1.1) ...
Removing linux-headers-4.18.0-16-generic (4.18.0-16.17) ...
Removing linux-headers-4.18.0-16 (4.18.0-16.17) ...
Removing linux-modules-extra-4.18.0-16-generic (4.18.0-16.17) ...
Removing linux-image-4.18.0-16-generic (4.18.0-16.17) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.18.0-16-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-13-generic
Found initrd image: /boot/initrd.img-5.0.0-13-generic
Found linux image: /boot/vmlinuz-4.18.0-17-generic
Found initrd image: /boot/initrd.img-4.18.0-17-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-modules-4.18.0-16-generic (4.18.0-16.17) ...
Removing perl-modules-5.26 (5.26.2-7ubuntu0.1) ...
Removing python-compizconfig:amd64 (1:0.9.13.1+18.10.20180930-0ubuntu1) ...
Removing python-talloc:amd64 (2.1.14-1ubuntu1) ...
Removing python-tdb (1.3.18-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libc-bin (2.29-0ubuntu2) ...
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directory
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...

```

Now I go really to sleep...
Thank you again, 
Carlo

---

### Post by carlo-sanguineti on 2019-04-25
Hello!
Well, this morning the situation is good.

I have just some questions about variations between my previous (Hybrid?) release and the brand new I got now:
1. Notifications:[INDENT]1.1. The System Load Indicator (version 0.4) notification is visible only when I pass the mouse over it. It's not a big problem.[/INDENT]
[INDENT]1.2. The hp icon does not appear on the notification bar anymore. Normally it would appear after I run ```
cd Desktop chmod +x hplip-3.18.10.run
```. I have the hplip-3.18.10.run on desktop. Well, when I run that chmod nothing happen. The printer/scanner looks still working properly.[/INDENT]
2. Icons:
[INDENT]2.1. Normally I had on the Desktop all the additional internal disk icons (when mounted) and all the QNAP NAS shared directories/folders (when mounted); Nothing appear anymore. It is not a big problem.
2.2. I used to have some icons customized on the Desktop. Now, despite clicking on "properties" of those icons I see the customized one, the icon that appear on the Desktop is the standard one.[/INDENT]

I don't want to bore you with these small problems that are just old man craziness. I only ask you if by chance these small problems are symptomatic of some still undetected (by me) major problem. Nothing else.

I want to thank you once more for your mind help. and when you write to me in Italian you can write the "tu" form and not the "lei". I am old but I don't deserve so much respect :-)...

Thank you again.

Have a nice day (here in Italy is national holiday: the Liberation Day, from the Nazi-Fascist regime)

Carlo

---

### Post by #&amp;thj^% on 2019-04-25
> **carlo-sanguineti said:**
> and when you write to me in Italian you can write the "tu" form and not the "lei". I am old but I don't deserve so much respect :-)...

Thank you again.

Carlo

Although System Load Indicator (indicator-multiload) works well with desktop environments like **Unity, MATE etc**., it's not very compatible with "GNOME 3" (default in Ubuntu 17.10 and later).

If you want to try an alternative solution which is compatible with GNOME, you may use a GNOME shell extension called "system-monitor". 
To install it:
```
sudo apt install gnome-shell-extension-system-monitor
```
For your HP icon problem, coming from 16.04 leaves some Unity-related stuff on your machine that is not only obsolete but prevents the AppIndicator extension from properly working.

What I would do:
```

sudo apt remove indicator-application
```
Now if you don't want to do that>>I've settled with:
```
killall indicator-application-service
```
BTW: Sono cresciuto con rispetto per tutti gli altri e te lo meriti

---

### Post by carlo-sanguineti on 2019-04-25
Well, I tried
```

sudo apt remove indicator-application

```
and then
```

chmod +x hplip-3.18.10.run

```
No output. hp icon still no in the notification bar.
I'll try again tomorrow again after a good old restart.

BTW
Thank you for your Italian sentence.
I do appreciate a lot people that respect other people, the environment, etc.
I do the same
My "I don't deserve it" was an understatement, just joking. In Italian the usual phrase would be "Puoi darmi del tu anche se sono piu' vecchio di te" (you can say to me "you" even if I'm older than you) In English it doesn't make any sense...

Thank you again.

Tomorrow I will tell you how was the final result.

Carlo

---

### Post by braznyc on 2019-04-25
> **1fallen said:**
> Well I at this point agree with Impavidus something very wonky here >> If you don't show the correct version Impavidus is showing like:
```
apt policy base-files
base-files:
  Installed: 10.1ubuntu9
  Candidate: 10.1ubuntu9
  Version table:
 *** 10.1ubuntu9 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status

```
I have used **"sed"** for a number of years now changing my source lists, with very few problems. **I don't use "do-release-upgrade -d"** any more.
```
 sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
```
Update and Upgrade again:
```
sudo apt update 
sudo apt full-upgrade
```
Before enabling all your PPA's first check they are supported for (19.04)


Thanks, that helped me.

---

### Post by carlo-sanguineti on 2019-04-26
Hi 1fallen,

Definitely
```

chmod +x hplip-3.18.10.run

```
Does not make any effect. My knowledge on Linux commands is too poor to try another command.
All I know about command lines refers to Digital VAX-VMS, RT11-M, and MS-DOS... :-)
I need to find something to make me sure my HP ENVY Photo 6220 is properly installed and working.
Well, it was so on my hybrid version, I hope it's the same now.

While
```

sudo apt install gnome-shell-extension-system-monitor

```
Does all I need

Thank you

---

### Post by #&amp;thj^% on 2019-04-26
> **braznyc said:**
> Thanks, that helped me.
Very happy to hear this. :)
> **carlo-sanguineti said:**
> Hi 1fallen,

While
```

sudo apt install gnome-shell-extension-system-monitor

```
Does all I need

Thank you
At this point I'm amazed that this worked at all, but I'm glad to hear things have worked out this well.
For your printer shouldn't you be using HPLIP 3.19.3+dfsg0-1 now?
For the notification did you try:
```
killall indicator-application-service
```
To remove the old and unnecessary clutter of HPLIP:
```
sh hplip-3.18.10.run --noexec
    cd hplip-3.18.10
    sudo ./uninstall.py
    sudo rm -rf /usr/share/hplip/
```

    Afterwards we install official Ubuntu packages instead (optionally):
```
 sudo apt install hplip-gui
```

and run "hp-setup"
> "Puoi darmi del tu anche se sono piu' vecchio di te" But your not, I got you beat by a few years. ;)
Sorry my Italian is at best rusty, so I tried to be just polite and with respect.
But going forward now, we will speak as friends. :)
Best Regards

---

### Post by carlo-sanguineti on 2019-04-28
Hi 1fallen,
I'm sorry I diddn't answer before, but yesterday I had my daughter with me, and I was only for were.

I got those outputs on your last suggestion:

```

killall indicator-application-service

```
gave
```

indicator-application-service: no process found

```

---

```

sh hplip-3.18.10.run --noexec

```
gave
```

Creating directory hplip-3.18.10
Verifying archive integrity... All good.
Uncompressing HPLIP 3.18.10 Self Extracting Archive.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................chown: changing ownership of './.libs/libsane-hpaio.so.1.0.0T': Operation not permitted
chown: changing ownership of './.libs/libhpmud.so.0.0.6T': Operation not permitted
chown: changing ownership of './.libs/cupsext.soT': Operation not permitted
chown: changing ownership of './.libs/libhpipp.so.0.0.1T': Operation not permitted
chown: changing ownership of './.libs/hpmudext.soT': Operation not permitted
chgrp: changing group of './.libs/libsane-hpaio.so.1.0.0T': Operation not permitted
chgrp: changing group of './.libs/libhpmud.so.0.0.6T': Operation not permitted
chgrp: changing group of './.libs/cupsext.soT': Operation not permitted
chgrp: changing group of './.libs/libhpipp.so.0.0.1T': Operation not permitted
chgrp: changing group of './.libs/hpmudext.soT': Operation not permitted

```

so I tried
```

sudo sh hplip-3.18.10.run --noexec

```
that gave just an array of dots...

then I tried hardly

```

cd hplip-3.18.10

```
but
```

bash: cd: hplip-3.18.10: Permission denied

```
So
```

sudo cd hplip-3.18.10

```
but
```

sudo: cd: command not found

```
I tried to double-click on the folder: no permissions.

So I went again on the hp site to download hplip, they sent me on [https://sourceforge.net/projects/hplip/](https://sourceforge.net/projects/hplip/) were I got a brand new hplip-3.19.3.run!

I tried then to do again all the procedure, 

```

sh hplip-3.19.3.run --noexec

```
gave me
```

Creating directory hplip-3.19.3
Verifying archive integrity... All good.
Uncompressing HPLIP 3.19.3 Self Extracting Archive...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

```
then
```

cd hplip-3.19.3
sudo ./uninstall.py

```
gave me
```

HP Linux Imaging and Printing System (ver. 3.19.1)
HPLIP Uninstaller ver. 1.0


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Uninstaller log saved in: /home/carlos/.hplip/hplip-uninstall.log


 
Are you sure to uninstall HPLIP-3.19.1 (y=yes, n=no*)?:y
Starting uninstallation...
HPLIP uninstallation is completed

```
Then
```

sudo rm -rf /usr/share/hplip/

```
No output. Then
```

sudo apt install hplip-gui

```
gave me
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python3-dbus.mainloop.pyqt5 python3-notify2 python3-pyqt5 python3-sip
Suggested packages:
  python3-pyqt5-dbg
The following NEW packages will be installed:
  hplip-gui python3-dbus.mainloop.pyqt5 python3-notify2 python3-pyqt5
  python3-sip
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,452 kB of archives.
After this operation, 16.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu disco/universe amd64 python3-dbus.mainloop.pyqt5 amd64 5.12.1+dfsg-1 [17.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu disco/universe amd64 python3-sip amd64 4.19.15+dfsg-1ubuntu1 [86.5 kB]
Get:3 http://archive.ubuntu.com/ubuntu disco/universe amd64 python3-pyqt5 amd64 5.12.1+dfsg-1 [2,319 kB]
Get:4 http://archive.ubuntu.com/ubuntu disco/universe amd64 hplip-gui all 3.19.1+dfsg0-1 [19.1 kB]
Get:5 http://archive.ubuntu.com/ubuntu disco/universe amd64 python3-notify2 all 0.3-3 [10.6 kB]
Fetched 2,452 kB in 1s (1,925 kB/s)        
Selecting previously unselected package python3-dbus.mainloop.pyqt5.
(Reading database ... 300594 files and directories currently installed.)
Preparing to unpack .../python3-dbus.mainloop.pyqt5_5.12.1+dfsg-1_amd64.deb ...
Unpacking python3-dbus.mainloop.pyqt5 (5.12.1+dfsg-1) ...
Selecting previously unselected package python3-sip.
Preparing to unpack .../python3-sip_4.19.15+dfsg-1ubuntu1_amd64.deb ...
Unpacking python3-sip (4.19.15+dfsg-1ubuntu1) ...
Selecting previously unselected package python3-pyqt5.
Preparing to unpack .../python3-pyqt5_5.12.1+dfsg-1_amd64.deb ...
Unpacking python3-pyqt5 (5.12.1+dfsg-1) ...
Selecting previously unselected package hplip-gui.
Preparing to unpack .../hplip-gui_3.19.1+dfsg0-1_all.deb ...
Unpacking hplip-gui (3.19.1+dfsg0-1) ...
Selecting previously unselected package python3-notify2.
Preparing to unpack .../python3-notify2_0.3-3_all.deb ...
Unpacking python3-notify2 (0.3-3) ...
Setting up python3-dbus.mainloop.pyqt5 (5.12.1+dfsg-1) ...
Setting up python3-notify2 (0.3-3) ...
Setting up python3-sip (4.19.15+dfsg-1ubuntu1) ...
Setting up python3-pyqt5 (5.12.1+dfsg-1) ...
Setting up hplip-gui (3.19.1+dfsg0-1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...

```
and then
```

hp-setup

```
gave me
```

Command 'hp-setup' not found, but can be installed with:


sudo apt install hplip

```


So
```

sudo apt install hplip

```
that gave me
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version (3.19.1+dfsg0-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and here I stopped, since I really don't know what to do...

I am very sorry to bother you so much, my friend... If you get annoyed or (surely) you have something more important to do, I will understand...

Thank you anyway,
Carlo

---

### Post by rbmorse on 2019-04-28
Carlo, this last part isn't just you.  I have the very same issue with HPLIP on my machine (ASUS Intel gen 7 desktop).  

My printer installed without problems using the Gnome devices utility.  No desktop indicator applet, but I do get status messages via the "notifications" utility.

---

### Post by carlo-sanguineti on 2019-04-28
Hi rbmorse,

I found quite a lot of notification utilities on Ubuntu Software. Could you specificate which one you are using?

Thank you,

regards,
Carlo

---

### Post by #&amp;thj^% on 2019-04-28
For S&G's I followed your instructions via:
Downloaded the .run from:
[list]Grabed the address:
[*]HPLIP Website:[http://hplip.sourceforge.net](http://hplip.sourceforge.net)
[*]HPLIP Development Team[/list]
grabbed the hplip-3.19.3.run, downloaded it and ran:
```
sh hplip-3.19.3.run
```
I hate posting this much text in the forums but it might jog a memory as to what was different with my install and yours.
```
HP Linux Imaging and Printing System (ver. 3.19.3)
HPLIP Installer ver. 5.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sun-28-Apr-2019_15:13:27.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
/Gtk-Message: 15:13:30.299: Failed to load module "canberra-gtk-module"
-Gtk-Message: 15:13:30.362: Failed to load module "canberra-gtk-module"
error: ubuntu-19.04 version is not supported, so all dependencies may not be installed. However trying to install using ubuntu-18.10 version packages.

Press 'y' to continue auto installation. Press 'n' to quit auto instalation(y=yes, n=no*): y


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 3.19.3 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 19.04.

Is "Ubuntu 19.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y

Initializing. Please wait...


ENTER USER PASSWORD
-------------------
Please enter the sudoer (me)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


SECURITY PACKAGES
-----------------
AppArmor is installed. 
AppArmor protects the application from external intrusion attempts making the application secure

Would you like to have this installer install the hplip specific policy/profile (y=yes*, n=no, q=quit) ? y


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
|Gtk-Message: 15:14:30.779: Failed to load module "canberra-gtk-module"
HPLIP-3.19.1 exists, this may conflict with the new one being installed.
Do you want to ('i'= Remove and Install*, 'q'= Quit)?    :i
Starting uninstallation...
HPLIP uninstallation is completed


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
\Gtk-Message: 15:18:14.918: Failed to load module "canberra-gtk-module"
OK


RUNNING SCANJET DEPENDENCY COMMANDS
-----------------------------------
sudo apt-get install --assume-yes python-pip (Scanjet-depend step 1)
sudo pip2 install --upgrade pip (Scanjet-depend step 2)
sudo apt-get install --assume-yes libleptonica-dev (Scanjet-depend step 3)
sudo apt-get install --assume-yes tesseract-ocr (Scanjet-depend step 4)
sudo apt-get install --assume-yes libtesseract-dev (Scanjet-depend step 5)
sudo -H pip2 install tesserocr (Scanjet-depend step 6)
sudo apt-get install --assume-yes tesseract-ocr-all (Scanjet-depend step 7)
sudo apt-get install --assume-yes libzbar-dev (Scanjet-depend step 8)
sudo apt-get install --assume-yes python-zbar (Scanjet-depend step 9)
sudo -H pip2 install opencv-python (Scanjet-depend step 10)
sudo -H pip2 install PyPDF2 (Scanjet-depend step 11)
sudo -H pip2 install imutils (Scanjet-depend step 12)
sudo -H pip2 install pypdfocr (Scanjet-depend step 13)
sudo -H pip2 install scikit-image (Scanjet-depend step 14)
sudo -H pip2 install scipy (Scanjet-depend step 15)
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib --prefix=/usr --enable-qt4 --disable-qt5 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-libusb01_build --disable-foomatic-ppd-install --disable-hpijs-install --disable-class-driver --disable-udev_sysfs_rules --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build --enable-apparmor_build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...
Command completed successfully.


Build complete.



POST-BUILD COMMANDS
-------------------
 

CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...
OK


HPLIP UPDATE NOTIFICATION
-------------------------
Do you want to check for HPLIP updates?. (y=yes*, n=no) : y


RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in   
when you started this installer, you will need to either restart your PC or     
unplug and re-plug in your printer (USB cable only). If you choose to restart,  
run this command after restarting: hp-setup (Note: If you are using a parallel  
connection, you will have to restart your PC. If you are using network/wireless,
you can ignore and continue).                                                   

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) : i


PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
Do you want to setup printer in GUI mode? (u=GUI mode*, i=Interactive mode) : u

HP Linux Imaging and Printing System (ver. 3.19.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Gtk-Message: 15:30:37.295: Failed to load module "canberra-gtk-module"
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

Done.


RE-STARTING HP_SYSTRAY
----------------------

HP Linux Imaging and Printing System (ver. 3.19.3)
System Tray Status Service ver. 2.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

```

Now I'm wondering if you caught this:
```
CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...
OK


HPLIP UPDATE NOTIFICATION
-------------------------
Do you want to check for HPLIP updates?. (y=yes*, n=no) : 

```
And:
```
PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
Do you want to setup printer in GUI mode? (u=GUI mode*, i=Interactive mode) : 

```
Finished my install and 'bob's yer uncle'I have a Icon in my (NOTE)>>Unity Panel and Top Panel.(See Screenshots)
```
Desktop: Unity Distro: Ubuntu 19.04 (Disco Dingo) 
```
And it works in Ubuntu-Gnome
My friend I would try your install again, it will offer to uninstall the current installed driver.:confused:

---

### Post by rbmorse on 2019-04-28
> **carlo-sanguineti said:**
> Hi rbmorse,

I found quite a lot of notification utilities on Ubuntu Software. Could you specificate which one you are using?

Thank you,

regards,
Carlo

I'm using the notifier that was installed with the default Gnome desktop.  I'm not sure what it has for a formal name.

---

### Post by carlo-sanguineti on 2019-04-29
Hi, my friend,

Unfortunately today I had to go to work, so I saw your message just after dinner. Well it's not that I hate to work, but I hate the kind of work I am doing in the last years. They will finish in June, but, sincerely, I'm looking forward  to have my life for myself.
I am doing (not so much->) technical documentation, as an obsolete technician as I am. But I think that when you write a configuration manual or an user manual for a big plant that it is still in the hands of the designers, and most of the plant is still to define, you write just a science fiction book, and not a real manual.
And when you ask some infos to these young technician and they would look at you in a better way if you were asking to go to bed with their wife... Yes, I am polemic. I was always was. But I was less bitter than now.

But this is Ubuntu Forum, and not alt.message.technician.frustrate.obsolete :-)

So,

I run
```

sh hplip-3.19.3.run

```
and, after following strictly your instruction, I had a
```

POST-BUILD COMMANDS
-------------------
OK




HPLIP UPDATE NOTIFICATION
-------------------------
Do you want to check for HPLIP updates?. (y=yes*, n=no) : y

```
I had NOT a
```

CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...
OK

```
BTW I had also (in GREEN)
```

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.

```
then in RED
```

error: ubuntu-19.04 version is not supported, so all dependencies may not be installed. However trying to install using ubuntu-18.10 version packages.

```
then in WHITE
```

Press 'y' to continue auto installation. Press 'n' to quit auto instalation(y=yes, n=no*): y

```
"y" was my answer.

After this everything went fine. At the end of everything I had a
```

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)

```

but, after all, I installed my printer, I am plenty of hp icons, and as Deng Xiaoping said once,
"It doesn't matter whether the cat is black or white, as long as it catches mice"
I didn't like Deng Xiaoping so much, but I like this phrase a lot.

Thank you again so much, my friend,

Carlo

---

### Post by carlo-sanguineti on 2019-04-29
Hi, rbmorse,
I understood what were you meaning just few minutes after shutting down my machine.
I'm sorry for the stupid question...
regards,
Carlo

---

### Post by #&amp;thj^% on 2019-04-30
> **carlo-sanguineti said:**
> 
After this everything went fine. At the end of everything I had a
```

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)

```

Thank you again so much, my friend,

Carlo

It now seems like hp-systray is attempting to start before the system tray is loaded .. changing this command (in startup applications) will introduce a 15 second delay in starting hp-systray, giving the system tray time to come up first.
```
sh -c "sleep 15; exec hp-systray"
```
Best Regards

---

### Post by carlo-sanguineti on 2019-04-30
Hi 1fallen.

the command
```

sh -c "sleep 15; exec hp-systray"

```
gave this output:
```

HP Linux Imaging and Printing System (ver. 3.19.3)
System Tray Status Service ver. 2.0


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


error: Unable to lock /home/carlos/.hplip/hp-systray.lock. Is hp-systray already running?



```
The error line was in red.

I anyway added a command with this line on my [COLOR=#000000]startup applications. I will see what it will happen... For some hours I can't restart my computer.
How can the [/COLOR][COLOR=#000000]startup applications decide to run first this my new command and after this the
[/COLOR]```

hp-systray -x[COLOR=#000000]
[/COLOR]
```[COLOR=#000000]
of the HP System Tray service?

Many thanks again, my friend.

Regards,

Carlo[/COLOR]

---

### Post by #&amp;thj^% on 2019-04-30
> **carlo-sanguineti said:**
> Hi 1fallen.

the command
```

sh -c "sleep 15; exec hp-systray"

```
gave this output:
```

HP Linux Imaging and Printing System (ver. 3.19.3)
System Tray Status Service ver. 2.0


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


**[COLOR="#FF0000"]_error: Unable to lock /home/carlos/.hplip/hp-systray.lock. Is hp-systray already running?_[/COLOR]**



```

That was just telling you the hp-systray was already running.
As far as how the programs are started rely's on the code firstly.
The error you showed me a couple of days ago:
```
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
```
Seemed to imply that it started early so I thought I would slow it down a bit with: "sh -c "sleep 15; exec hp-systray">>>That will wait 15 seconds to start the tray, in hopes of not seeing that warning.

---

### Post by carlo-sanguineti on 2019-05-01
Hi 1fallen,

today when I restarted my PC, everything went properly.

So, what to say, my friend,

I thank you very much for everything you did to help me. I'm sorry for my lack of skill, that made you repeat sometimes, and describe very clearly each step, so even me was able to understand.

Thank you again,
Have a nice life, 

Carlo

---

### Post by #&amp;thj^% on 2019-05-01
Thank You very much for the kind words, it's not taken lightly here.
I found you very wise, I think somethings were just lost in translation is all. ;)
If I do get the chance, I will for sure contact you.
Grazie per la vostra ospitalità :)

---

### Post by carlo-sanguineti on 2019-05-02
If chances will be good, it maybe we will meet someday.
I am always grateful with people that help me, as in the same way I can be, I mean, not revengeful, but I will never forget even the dresses wore in the moment somebody did something bad to me.
I I'm going to be old, I'm already am. But my memory it still working properly. And I will never forget the good and the bad.

Have a nice life, my friend!

BTW
I was rebuked by the forum because i wrote down my email address. But It was the only way I knew to tell it to you... :-)

---

### Post by #&amp;thj^% on 2019-05-02
Well I kind of asked if they would remove it for your privacy, but I did get it.:)
And for the record you may always just send me a PM. (Private Message)

---

### Post by carlo-sanguineti on 2019-05-13
Got it.
Thank you again.
Everything is working properly since your help.

Ciao
Carlo

---

