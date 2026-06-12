---
title: "UNABLE TO UPGRADE: Network problem during upgrade to 19.10 (why?)"
date: 2019-10-25
forum: Installation &amp; Upgrades
---

### Post by carlo-sanguineti on 2019-10-25
Hello everybody,
Hello to 1fallen, if he's still working here.

As usually, unfortunately, I have problems in upgrading from an Ubuntu release to the next one. This time it's quite strange.

1. My computer is a laptop connected to internet by a Vodafone router, all by cable.
2. I usually do any update on the current release of Ubuntu without any problem. No network problems.
3. Three days ago, after an update, Ubuntu popped up that there was an upgrade, from 19.04 to 19.10, as expected.
4. I started the upgrade, and, arrive to disabling the third party sources without any problem.
5. While "Setting new software channels" the upgrade stops with this pop-up:
    [HTML]Error during update
    A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.[/HTML] 
6. The program then restores the original system state.
That's all.

Every time it the same thing.

A couple of things more:
a. I don't succeed in any moment of the upgrade activity to open the terminal view inside of the upgrade window.
b. Since long time, if I run the software updater by myself, I receive an error pop-up:
    [HTML]Failed to download repository information
    Check your internet connection.[/HTML]

I don't know if these additional information are useful or not.

I also performed the internet speed test on my computer, and the report is good:
- Ping 9 ms
- Download 81.15 Mbps
- Upload 19.32 Mbps

I thank in advance anybody that will help me to find the solution and to upgrade mu Ubuntu from 19.04 to 19.10.

Regards,

Carlo

---

### Post by dino99 on 2019-10-26
you said "as usually", so it is not something new :confused:

is your router using a proxy/vpn ? is your system using 'sudo' is it encrypted ? is journalctl logging something usefull about that issue ?

---

### Post by carlo-sanguineti on 2019-10-26
Hi dino99,

I say "usually' since last three upgrades I had some problem, but different to this:
[https://ubuntuforums.org/showthread.php?t=2417517]("https://ubuntuforums.org/showthread.php?t=2417517")
[https://ubuntuforums.org/showthread.php?t=2376291]("https://ubuntuforums.org/showthread.php?t=2376291")

These are the answers to your questions:
1. is your router using a proxy/vpn ?
    NO
2. is your system using 'sudo' is it encrypted ?
    NO
3. is journalctl logging something usefull about that issue ?
    Frankly I have no idea about how to access to journalactl logging.

I have not a deep knowledge of Linux, despite I use it since about 8 years.
But I can tell you how DEC VAX VMS works :)
Yes, I'm quite old...

Thank you for your help,
Regards,
Carlo

---

### Post by carlo-sanguineti on 2019-11-01
Hello,

The situation is the same as from the beginning.
I just want to add a slight deterioration:
When I click now on "Activities" the view of all the active applications appears a little bigger, so the last row is not completely visualized...

Looking forward for any help,
Thanking in anticipation,
Kind regards,

Carlo

---

### Post by Bashing-om on 2019-11-01
carlo-sanguineti; Ok - I pop in here

So You want to upgrade to 19.10 -
Lets start with the basics here:

1) internet connectivity:
```

ping-c3 8.8.8.8
ping -c3 google.com

```

2) State of the package management system:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
uname -r
cat /proc/version
sudo apt update
sudo apt full-upgrade

```

From these we see where we jump to next :)

[INDENT]all in the process
[/INDENT]

---

### Post by carlo-sanguineti on 2019-11-05
Hi Bashing-om,
I' sorry for the delay in the answer, but I was quite busy in these days.
Anyway, the output I had was:

```
ping -c3 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=14.10 ms64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=12.6 ms64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=45.4 ms
```

```
ping -c3 google.comPING google.com (216.58.206.78) 56(84) bytes of data.64 bytes from lhr35s11-in-f14.1e100.net (216.58.206.78): icmp_seq=1 ttl=56 time=43.5 ms64 bytes from lhr35s11-in-f14.1e100.net (216.58.206.78): icmp_seq=2 ttl=56 time=51.4 ms64 bytes from lhr35s11-in-f14.1e100.net (216.58.206.78): icmp_seq=3 ttl=56 time=44.8 ms
--- google.com ping statistics ---3 packets transmitted, 3 received, 0% packet loss, time 5msrtt min/avg/max/mdev = 43.460/46.563/51.404/3.468 ms
```

```
cat -n /etc/apt/sources.list     1	deb http://archive.ubuntu.com/ubuntu disco main restricted universe multiverse     2	deb-src http://archive.ubuntu.com/ubuntu disco main restricted universe multiverse     3	deb http://archive.ubuntu.com/ubuntu disco-updates main restricted universe multiverse     4	deb-src http://archive.ubuntu.com/ubuntu disco-updates main restricted universe multiverse     5	deb http://archive.ubuntu.com/ubuntu disco-backports main restricted universe multiverse     6	deb-src http://archive.ubuntu.com/ubuntu disco-backports main restricted universe multiverse     7	deb http://archive.ubuntu.com/ubuntu disco-security main restricted universe multiverse     8	deb-src http://archive.ubuntu.com/ubuntu disco-security main restricted universe multiverse     9	# deb http://archive.ubuntu.com/ubuntu disco-proposed restricted main universe multiverse    10	# deb-src http://archive.ubuntu.com/ubuntu disco-proposed restricted main universe multiverse    11	deb http://archive.canonical.com/ubuntu disco partner    12	deb-src http://archive.canonical.com/ubuntu disco partner
```

```
tail -v -n +1 /etc/apt/sources.list.d/*==> /etc/apt/sources.list.d/behda-ppa-trusty.list <==
==> /etc/apt/sources.list.d/behda-ppa-trusty.list.save <==
==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list <==# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu saucy main
==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list.distUpgrade <==# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu saucy main
==> /etc/apt/sources.list.d/caffeine-developers-ppa-saucy.list.save <==# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu vivid main # disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu saucy main
==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <==# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.distUpgrade <==# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <==# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/canonical_partner.list <==deb http://archive.canonical.com/ubuntu/ cosmic partner
==> /etc/apt/sources.list.d/canonical_partner.list.distUpgrade <==deb http://archive.canonical.com/ubuntu/ cosmic partner
==> /etc/apt/sources.list.d/canonical_partner.list.save <==deb http://archive.canonical.com/ubuntu/ cosmic partner
==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==# deb http://ppa.launchpad.net/diesch/testing/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
==> /etc/apt/sources.list.d/diesch-testing-trusty.list.distUpgrade <==# deb http://ppa.launchpad.net/diesch/testing/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==# deb http://ppa.launchpad.net/diesch/testing/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list <==# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main
==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list.distUpgrade <==# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main
==> /etc/apt/sources.list.d/djcj-ubuntu-vlc-stable-utopic.list.save <==# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu utopic main
==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list <==# deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu utopic main
==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list.distUpgrade <==# deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu utopic main
==> /etc/apt/sources.list.d/flacon-ubuntu-ppa-utopic.list.save <==# deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu utopic main
==> /etc/apt/sources.list.d/google-chrome.list <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
==> /etc/apt/sources.list.d/google-chrome.list.save <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 
==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list <==# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main
==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list.distUpgrade <==# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main
==> /etc/apt/sources.list.d/jd-team-jdownloader-saucy.list.save <==# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main
==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list <==# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu utopic main
==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list.distUpgrade <==# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu utopic main
==> /etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list.save <==# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu utopic main
==> /etc/apt/sources.list.d/opera.list <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
# The line above will make sure you get all final public releases.# Uncomment the following line if you want to get alpha and beta# releases, too.
# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
==> /etc/apt/sources.list.d/opera.list.distUpgrade <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
# The line above will make sure you get all final public releases.# Uncomment the following line if you want to get alpha and beta# releases, too.
# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
==> /etc/apt/sources.list.d/opera.list.save <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
# The line above will make sure you get all final public releases.# Uncomment the following line if you want to get alpha and beta# releases, too.
# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
==> /etc/apt/sources.list.d/opera-stable.list <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
# deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to xenial
==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
# deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to xenial
==> /etc/apt/sources.list.d/opera-stable.list.save <==# This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades
# deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to xenial
==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list <==# deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu xenial main
==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list.distUpgrade <==# deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu xenial main
==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-xenial.list.save <==# deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu xenial main
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list.distUpgrade <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_drawers_ubuntu.list.save <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list.distUpgrade <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_u-splitter_ubuntu.list.save <==# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/u-splitter/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty disabled on upgrade to vivid
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list.distUpgrade <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-artful.list.save <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu bionic main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list.distUpgrade <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu bionic main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-bionic.list.save <==# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu bionic main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-disco.list <==deb http://ppa.launchpad.net/rvm/smplayer/ubuntu disco main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu disco main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-disco.list.distUpgrade <==deb http://ppa.launchpad.net/rvm/smplayer/ubuntu disco main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu disco main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list <==# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu cosmic main # disabled on upgrade to artful disabled on upgrade to bionic disabled on upgrade to cosmic# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list.distUpgrade <==# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu cosmic main # disabled on upgrade to artful disabled on upgrade to bionic disabled on upgrade to cosmic# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main
==> /etc/apt/sources.list.d/rvm-ubuntu-smplayer-zesty.list.save <==# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu cosmic main # disabled on upgrade to artful disabled on upgrade to bionic disabled on upgrade to cosmic# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu zesty main
==> /etc/apt/sources.list.d/skype-stable.list <==# deb [arch=amd64] https://repo.skype.com/deb stable main # disabled on upgrade to bionic
==> /etc/apt/sources.list.d/skype-stable.list.distUpgrade <==# deb [arch=amd64] https://repo.skype.com/deb stable main # disabled on upgrade to bionic
==> /etc/apt/sources.list.d/skype-stable.list.save <==# deb [arch=amd64] https://repo.skype.com/deb stable main # disabled on upgrade to bionic
==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list <==# deb http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu utopic main
==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list.distUpgrade <==# deb http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu utopic main
==> /etc/apt/sources.list.d/starws-box-ubuntu-deadbeef-player-utopic.list.save <==# deb http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu utopic main
==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list <==# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.distUpgrade <==# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.save <==# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu utopic main # disabled on upgrade to utopic# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list <==# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.distUpgrade <==# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.save <==# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu yakkety main # disabled on upgrade to yakkety# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main # disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.distUpgrade <==# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main # disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main # disabled on upgrade to utopic disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list <==# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu saucy main
==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list.distUpgrade <==# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu saucy main
==> /etc/apt/sources.list.d/videolan-master-daily-saucy.list.save <==# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main # disabled on upgrade to trusty disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu saucy main
==> /etc/apt/sources.list.d/vivaldi-beta.list <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/beta/deb/ stable main # disabled on upgrade to xenial
==> /etc/apt/sources.list.d/vivaldi-beta.list.distUpgrade <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/beta/deb/ stable main # disabled on upgrade to xenial
==> /etc/apt/sources.list.d/vivaldi-beta.list.save <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/beta/deb/ stable main # disabled on upgrade to xenial
==> /etc/apt/sources.list.d/vivaldi.list <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/stable/deb/ stable main
==> /etc/apt/sources.list.d/vivaldi.list.distUpgrade <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/stable/deb/ stable main
==> /etc/apt/sources.list.d/vivaldi.list.save <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/stable/deb/ stable main
==> /etc/apt/sources.list.d/vivaldi-snapshot.list <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/snapshot/deb/ stable main
==> /etc/apt/sources.list.d/vivaldi-snapshot.list.distUpgrade <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/snapshot/deb/ stable main
==> /etc/apt/sources.list.d/vivaldi-snapshot.list.save <==### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.# deb http://repo.vivaldi.com/snapshot/deb/ stable main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.distUpgrade <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list.save <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main # disabled on upgrade to vivid# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main # disabled on upgrade to xenial# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.distUpgrade <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main # disabled on upgrade to xenial# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-wily.list.save <==# deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main # disabled on upgrade to xenial# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu wily main
```

```
uname -r5.0.0-32-generic
```

```
cat /proc/versionLinux version 5.0.0-32-generic (buildd@lgw01-amd64-034) (gcc version 8.3.0 (Ubuntu 8.3.0-6ubuntu1)) #34-Ubuntu SMP Wed Oct 2 02:06:48 UTC 2019
```

```
sudo apt update[sudo] password for carlos: Hit:1 http://archive.ubuntu.com/ubuntu disco InReleaseHit:2 http://ppa.launchpad.net/rvm/smplayer/ubuntu disco InRelease             Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     Get:5 http://archive.ubuntu.com/ubuntu disco-updates InRelease [97.5 kB]       Get:6 http://deb.opera.com/opera stable InRelease [2,591 B]                    Hit:7 http://archive.canonical.com/ubuntu disco InRelease                      Get:8 http://archive.ubuntu.com/ubuntu disco-backports InRelease [88.8 kB]Hit:9 http://archive.canonical.com/ubuntu cosmic InReleaseGet:11 http://archive.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]Err:6 http://deb.opera.com/opera stable InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B8EC3BAABDC4346Get:12 http://archive.ubuntu.com/ubuntu disco-updates/universe Sources [57.5 kB]Get:13 http://archive.ubuntu.com/ubuntu disco-updates/main Sources [105 kB]   Get:14 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages [308 kB]Get:15 http://archive.ubuntu.com/ubuntu disco-updates/main i386 Packages [253 kB]Get:16 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 DEP-11 Metadata [134 kB]Get:17 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 48x48 Icons [19.4 kB]Get:18 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 64x64 Icons [44.2 kB]Get:19 http://archive.ubuntu.com/ubuntu disco-updates/universe i386 Packages [316 kB]Get:20 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 Packages [323 kB]Get:21 http://archive.ubuntu.com/ubuntu disco-updates/universe Translation-en [114 kB]Get:22 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 DEP-11 Metadata [64.8 kB]Get:23 http://archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 48x48 Icons [32.6 kB]Get:24 http://archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 64x64 Icons [106 kB]Get:25 http://archive.ubuntu.com/ubuntu disco-backports/universe amd64 DEP-11 Metadata [7,980 B]Get:26 http://archive.ubuntu.com/ubuntu disco-security/main Sources [65.5 kB]  Get:27 http://archive.ubuntu.com/ubuntu disco-security/universe Sources [36.4 kB]Get:28 http://archive.ubuntu.com/ubuntu disco-security/main amd64 Packages [235 kB]Get:29 http://archive.ubuntu.com/ubuntu disco-security/main i386 Packages [183 kB]Get:30 http://archive.ubuntu.com/ubuntu disco-security/main Translation-en [83.7 kB]Get:31 http://archive.ubuntu.com/ubuntu disco-security/main amd64 DEP-11 Metadata [37.6 kB]Get:32 http://archive.ubuntu.com/ubuntu disco-security/main DEP-11 48x48 Icons [12.9 kB]Get:33 http://archive.ubuntu.com/ubuntu disco-security/main DEP-11 64x64 Icons [27.4 kB]Get:34 http://archive.ubuntu.com/ubuntu disco-security/universe i386 Packages [259 kB]Get:35 http://archive.ubuntu.com/ubuntu disco-security/universe amd64 Packages [266 kB]Get:36 http://archive.ubuntu.com/ubuntu disco-security/universe Translation-en [80.2 kB]Get:37 http://archive.ubuntu.com/ubuntu disco-security/universe amd64 DEP-11 Metadata [20.0 kB]Get:38 http://archive.ubuntu.com/ubuntu disco-security/universe DEP-11 48x48 Icons [14.3 kB]Get:39 http://archive.ubuntu.com/ubuntu disco-security/universe DEP-11 64x64 Icons [52.9 kB]Fetched 3,542 kB in 6s (593 kB/s)                   Reading package lists... DoneBuilding dependency tree       Reading state information... DoneAll packages are up to date.W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com/opera stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B8EC3BAABDC4346W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B8EC3BAABDC4346W: Some index files failed to download. They have been ignored, or old ones used instead.
```

```
sudo apt full-upgradeReading package lists... DoneBuilding dependency tree       Reading state information... DoneCalculating upgrade... Done0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

As you see, no upgrade was done...
Looking forward for any further help from you, thank you a lot anyway,
regards,
Carlo

---

### Post by SeijiSensei on 2019-11-05
First, I'd get rid of all those entries in your sources.list that refer to distributions other than the one you are using.  I'd also remove any PPAs and start with just the basic repositories that refer to your current distribution.  Then you need to run "sudo apt dist-upgrade" on your current release version before trying to run do-release-upgrade. After you have a functioning system, you can start to add back the PPAs.

Or, perhaps a better solution is just to install 19.10 from scratch.  Do you have a separate /home partition?  Along with a separate /home, I have another partition where I can install new distro versions so I don't run into conflicts, and a separate /boot.  If the new version works properly, I can edit the bootloader to use the new version by default.

---

### Post by carlo-sanguineti on 2019-11-05
Hello SeijiSensei
Than you for your answer.
To to what you suggest me I had to be a better user of Linux / Ubuntu. If you like do help me, tell me in detail how to remove all the unnecessary entries and PPAs.

Secondly, I have a disk devoted only to the programs. where the directories are:
bin
boot
cdrom
core
dev
etc
home
initrd.img.old
lib
lib32
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
snap
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old

Nevertheless, I am absolutely not able to install Ubuntu from scratch. I never did with a Linux operating system in my life. I'm afraid to do something really bad...

Thank you again,
Regards,
Carlo

---

### Post by #&amp;thj^% on 2019-11-13
Once again my old friend the PPA's are not a good way to go on a Version Up-grade.
First remove/purge all of the below PPA's from your source list.
```
deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu vivid main #  main
deb http://ppa.launchpad.net/diesch/testing/ubuntu utopic main
deb http://ppa.launchpad.net/djcj/vlc-stable
deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main
deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu vivid main
deb http://deb.opera.com/opera/ stable non-free #Opera Browser
deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main 
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/drawers/ubuntu trusty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu artful main
deb [arch=amd64] https://repo.skype.com/deb stable main
deb http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu vivid main
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu yakkety main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
deb http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main

```
As you can see there are many many chance's for your up-grade to fail. ;) Future reference before any OS version up-grade you'll need to get rid of the "Foreign" sources, to become pure ubuntu only sources.
After those have been purged/removed, then re-fresh your list:
```
sudo apt update
sudo apt dist-upgrade
```
If any errors appear, stop there and post back what was shown in the terminal. 
Roll up your shirt sleeve's we could be here a while. :)

---

### Post by carlo-sanguineti on 2019-11-14
Hi, my old friend! Wasn't necessary to answer so promptly...
Thank you, really.  know it was an effort from you. I'm touched and grateful.

I removed manually all the PPA you told me, and even someone was noted as "disabled on *xyx* upgrade" or something like this.
All garbage that I installed on the first years on Ubuntu. I didn't installed anything outside the Ubuntu Software application since your last successful intervention, but evidently it was not enough.

And... no errors! If you have time to waste here is the output to read... Now the machine asks me to restart. I will write again after it.

Thank you really a lot,
Carlo

[HTML]
sudo apt dist-upgradeReading package lists... DoneBuilding dependency tree       Reading state information... DoneCalculating upgrade... DoneThe following packages were automatically installed and are no longer required:  linux-headers-5.0.0-32 linux-headers-5.0.0-32-generic  linux-image-5.0.0-32-generic linux-modules-5.0.0-32-generic  linux-modules-extra-5.0.0-32-genericUse 'sudo apt autoremove' to remove them.The following packages will be upgraded:  ghostscript ghostscript-x imagemagick imagemagick-6-common imagemagick-6.q16  libgs9 libgs9-common libmagick++-6-headers libmagick++-6.q16-8  libmagick++-6.q16-dev libmagick++-dev libmagickcore-6-arch-config  libmagickcore-6-headers libmagickcore-6.q16-6 libmagickcore-6.q16-6-extra  libmagickcore-6.q16-dev libmagickwand-6-headers libmagickwand-6.q16-6  libmagickwand-6.q16-dev linux-firmware20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.Need to get 90.5 MB of archives.After this operation, 1,537 kB of additional disk space will be used.Do you want to continue? [Y/n] YGet:1 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagick++-6.q16-dev amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [125 kB]Get:2 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagick++-dev all 8:6.9.10.14+dfsg-7ubuntu2.3 [1,416 B]Get:3 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagick++-6-headers all 8:6.9.10.14+dfsg-7ubuntu2.3 [47.5 kB]Get:4 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickwand-6.q16-dev amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [303 kB]Get:5 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickwand-6-headers all 8:6.9.10.14+dfsg-7ubuntu2.3 [10.5 kB]Get:6 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 imagemagick-6.q16 amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [427 kB]Get:7 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickcore-6.q16-dev amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [973 kB]Get:8 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickcore-6-arch-config amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [24.5 kB]Get:9 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickcore-6-headers all 8:6.9.10.14+dfsg-7ubuntu2.3 [49.1 kB]Get:10 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 imagemagick-6-common all 8:6.9.10.14+dfsg-7ubuntu2.3 [61.1 kB]Get:11 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickwand-6.q16-6 amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [303 kB]Get:12 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickcore-6.q16-6-extra amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [64.3 kB]Get:13 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagickcore-6.q16-6 amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [1,641 kB]Get:14 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libmagick++-6.q16-8 amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [129 kB]Get:15 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 ghostscript-x amd64 9.26~dfsg+0-0ubuntu7.4 [43.0 kB]Get:16 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 ghostscript amd64 9.26~dfsg+0-0ubuntu7.4 [50.9 kB]Get:17 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libgs9 amd64 9.26~dfsg+0-0ubuntu7.4 [2,389 kB]Get:18 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 libgs9-common all 9.26~dfsg+0-0ubuntu7.4 [5,092 kB]Get:19 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 imagemagick amd64 8:6.9.10.14+dfsg-7ubuntu2.3 [14.3 kB]Get:20 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 linux-firmware all 1.178.6 [78.8 MB]Fetched 90.5 MB in 13s (7,152 kB/s)                                            (Reading database ... 334983 files and directories currently installed.)Preparing to unpack .../00-libmagick++-6.q16-dev_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagick++-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../01-libmagick++-dev_8%3a6.9.10.14+dfsg-7ubuntu2.3_all.deb ...Unpacking libmagick++-dev (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../02-libmagick++-6-headers_8%3a6.9.10.14+dfsg-7ubuntu2.3_all.deb ...Unpacking libmagick++-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../03-libmagickwand-6.q16-dev_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickwand-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../04-libmagickwand-6-headers_8%3a6.9.10.14+dfsg-7ubuntu2.3_all.deb ...Unpacking libmagickwand-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../05-imagemagick-6.q16_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking imagemagick-6.q16 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../06-libmagickcore-6.q16-dev_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickcore-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../07-libmagickcore-6-arch-config_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickcore-6-arch-config:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../08-libmagickcore-6-headers_8%3a6.9.10.14+dfsg-7ubuntu2.3_all.deb ...Unpacking libmagickcore-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../09-imagemagick-6-common_8%3a6.9.10.14+dfsg-7ubuntu2.3_all.deb ...Unpacking imagemagick-6-common (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../10-libmagickwand-6.q16-6_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickwand-6.q16-6:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../11-libmagickcore-6.q16-6-extra_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickcore-6.q16-6-extra:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../12-libmagickcore-6.q16-6_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagickcore-6.q16-6:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../13-libmagick++-6.q16-8_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking libmagick++-6.q16-8:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../14-ghostscript-x_9.26~dfsg+0-0ubuntu7.4_amd64.deb ...Unpacking ghostscript-x (9.26~dfsg+0-0ubuntu7.4) over (9.26~dfsg+0-0ubuntu7.3) ...Preparing to unpack .../15-ghostscript_9.26~dfsg+0-0ubuntu7.4_amd64.deb ...Unpacking ghostscript (9.26~dfsg+0-0ubuntu7.4) over (9.26~dfsg+0-0ubuntu7.3) ...Preparing to unpack .../16-libgs9_9.26~dfsg+0-0ubuntu7.4_amd64.deb ...Unpacking libgs9:amd64 (9.26~dfsg+0-0ubuntu7.4) over (9.26~dfsg+0-0ubuntu7.3) ...Preparing to unpack .../17-libgs9-common_9.26~dfsg+0-0ubuntu7.4_all.deb ...Unpacking libgs9-common (9.26~dfsg+0-0ubuntu7.4) over (9.26~dfsg+0-0ubuntu7.3) ...Preparing to unpack .../18-imagemagick_8%3a6.9.10.14+dfsg-7ubuntu2.3_amd64.deb ...Unpacking imagemagick (8:6.9.10.14+dfsg-7ubuntu2.3) over (8:6.9.10.14+dfsg-7ubuntu2.2) ...Preparing to unpack .../19-linux-firmware_1.178.6_all.deb ...Unpacking linux-firmware (1.178.6) over (1.178.3) ...Setting up libgs9-common (9.26~dfsg+0-0ubuntu7.4) ...Setting up imagemagick-6-common (8:6.9.10.14+dfsg-7ubuntu2.3) ...Installing new version of config file /etc/ImageMagick-6/policy.xml ...Setting up libgs9:amd64 (9.26~dfsg+0-0ubuntu7.4) ...Setting up linux-firmware (1.178.6) ...update-initramfs: Generating /boot/initrd.img-5.0.0-36-genericcryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-5.0.0-35-genericcryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-5.0.0-32-genericcryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-3.19.0-31-genericcryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-3.16.0-34-genericcryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-3.13.0-39-genericE: amd64-microcode: unsupported kernel version!cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryupdate-initramfs: Generating /boot/initrd.img-3.11.0-19-genericE: amd64-microcode: unsupported kernel version!cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries     nor crypto modules. If that's on purpose, you may want to uninstall the     'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs     integration and avoid this warning./sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directorySetting up ghostscript (9.26~dfsg+0-0ubuntu7.4) ...Setting up libmagickcore-6.q16-6:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickwand-6.q16-6:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickcore-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagick++-6.q16-8:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickcore-6-arch-config:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickcore-6.q16-6-extra:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickwand-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up ghostscript-x (9.26~dfsg+0-0ubuntu7.4) ...Setting up libmagickcore-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up imagemagick-6.q16 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagickwand-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagick++-6-headers (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagick++-6.q16-dev:amd64 (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up imagemagick (8:6.9.10.14+dfsg-7ubuntu2.3) ...Setting up libmagick++-dev (8:6.9.10.14+dfsg-7ubuntu2.3) ...Processing triggers for mime-support (3.60ubuntu1) ...Processing triggers for hicolor-icon-theme (0.17-2) ...Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...Processing triggers for libc-bin (2.29-0ubuntu2) .../sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/nvidia_settings.conf: No such file or directoryProcessing triggers for man-db (2.8.5-2) ...Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...Rebuilding /usr/share/applications/bamf-2.index...Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...[/HTML]

---

### Post by carlo-sanguineti on 2019-11-14
Hi, my friend,
After the restart everything was OK with 19.04 still on. So I did the upgrade by Software Update and now I have the 19.10 happily working on my machine.
Thank you a lot, again.

You can say, as an ancient Roman did long time ago, "Veni, vidi, vici". Take care about Brutus :D!!!

It's nearly one o'clock in the morning, here in Genova. I will go happily to bed.

Thank you again,

Carlo

---

### Post by #&amp;thj^% on 2019-11-14
Great News! Now that's what we call team work. ;) (You conquered)
Take Good care, Best Regards

---

