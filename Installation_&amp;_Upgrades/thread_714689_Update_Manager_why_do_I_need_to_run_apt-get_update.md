---
title: "Update Manager: why do I need to run apt-get update to avoid &quot;NOT AUTHENTICATED&quot;?"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by pmorch on 2008-03-04
Hi,

I've been seeing this annoying thing on two of my installations recently. One is running Gutsy and the other is running Feisty, and both exhibit the same behavior:

[LIST]
[*]The Update Manager icon is present in the Notification Area indicating that packages need to be installed. 
[*]I click on the icon and Update Manager appears showing a number of packages. 
[*]I then hit "Install Updates".
[*]This brings up a screen that shows the packages as being "NOT AUTHENTICATED" 
(e.g. today that's udev, nautilus and thunderbird to name a few.)
[*]I then hit Cancel, and hit the "Check" button (which seems to do an apt-get update behind the scenes)
[*]A subsequent "Install Updates" runs without incident - the problem has gone away.
[*]Until in a couple of days, where again, I'll see that there are packages available for update, that again will be "NOT AUTHENTICATED" until i hit "Check" or run "apt-get update" manually
[/LIST]

Does the "list" created by "apt-get update" time out or something?

I've noticed that the command line apt-get exhibist the exact same behaviour: "apt-get dist-upgrade" will complain about unauthenticated packages. Then an "apt-get update" will fix it. If I wait a couple of days and then want to "apt-get install foo" it will again complain about unauthenticated packages. "apt-get update" will fix it again, etc.

I've been a long-time debian and ubuntu user. I don't remember this apt-get behaviour and think it has cropped up "recently". 

Does anybody know why packages loose their "authentication status" after a day or two? And why, if that is the case, Update Manager can see that there are new packages but not "refresh" the authentication status of the package list?

I'm thinking that this must be an annoyance and usability problem for all Update Manager users, but I don't find this being a FAQ. Maybe it is something with my setup. But I get the same behaviour for both Gutsy and Feisty here on both my Ubuntu machines, so I'm quite puzzled. After 3 hours of googling I give up and hope somebody can shed some light on this.

Below you'll see that my package list is quite standard (except for medibuntu, but the mentioned packages surely are not from medibuntu...)
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

### Post by PmDematagoda on 2008-03-04
I think your problem may be with the Medibuntu repositories not being authenticated.

Open your sources.list file for editing and then change the last line to make it look like this:-
```
deb-src http://packages.medibuntu.org/ gutsy free non-free
```
and then update the sources list, see if that solves your problem.

---

### Post by zvacet on 2008-03-04
It look little bit strange that is happened in such short intervals,but you don´t have to worry.You are getting updates from Ubuntu repos only,so nothing bad can happened if you accept that kind of updates.But you allready know that.I didn´t expirienced something like that if that is what you want to know.

---

### Post by pmorch on 2008-03-05
> **PmDematagoda said:**
> I think your problem may be with the Medibuntu repositories not being authenticated.

Open your sources.list file for editing and then change the last line to make it look like this:-
```
deb-src http://packages.medibuntu.org/ gutsy free non-free
```
and then update the sources list, see if that solves your problem.

The weird thing is that packages are authenticated "today", but if I wait a few days, all of a sudden they aren't authenticated any longer. I don't see how that can be explained by entries in sources.list. And certainly not deb-src lines, as far as I understand. Why do you think that enabling a deb-src line would fix it? By "then update the sources list, see if that solves your problem" I take it you mean run "apt-get update". As I said in my original post, running "apt-get update" **always** fixes it without *any* changes to sources.list.

I started thinking about that "apt-get update" must be run peridocially or Update Manager wouldn't discover new packages, and so  I discovered /etc/cron.d/apt that runs "apt-get update" every day, because /etc/apt/apt.conf.d/10periodic contains 
```
APT::Periodic::Update-Package-Lists "1";
```
(A wholly undocumented apt feature as far as I can tell)

And maybe these things run by cron cause it to fail... I don't know. Now I'm curious... /etc/crontab has:
```
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

Meaning that /etc/cron.daily/apt will be run at 6:25 every morning. So maybe there is a behavior difference whether my machine happens to be on or not at 6:25 AM. 

And what happens if I am a good boy and turn off my computer every night and turn it back on every morning at 9 am for 10 years. Will Update Manager then never discover that there are new updates until I manually run "apt-get update"?

Ah, so many questions...

---

### Post by cyau90 on 2008-03-25
Hi-

I've been using Ubuntu for a few months now, and have just experienced the same problem with update manager as the user above. 

Any ideas?

Thank you

[ps. This is my first post in the Forum]

---

