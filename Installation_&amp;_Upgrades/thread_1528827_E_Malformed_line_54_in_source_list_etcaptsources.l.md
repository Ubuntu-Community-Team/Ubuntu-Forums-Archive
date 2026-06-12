---
title: "E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by Masmidow on 2010-07-11
Hey Guys,

  I have been having some trouble installing the latest version of Firefox (3.6.6). My first command was:
[I]**sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa**

[I]And that went smooth. Then I typed in:
[/I][/I][B][I]sudo apt-get update

[/I][/B][I]This is when I received this error output:
[B]
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)

[/B]So, I went to the /etc/apt/sources.list file and appended these two line to the end:
[B][COLOR=Black]
[/COLOR][/B][/I][B][COLOR=Black]deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main 

[/COLOR][/B][COLOR=Black]When I retried the command (sudo apt-get/update), I received the same error message 
[/COLOR]
[I]Any advice? Thanks in advance! BTW here is the /etc/apt/sources.list file:

[B][COLOR=Teal]# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
[COLOR=Red]deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main[/COLOR] [/COLOR][/B]
[/I][I][I]
[COLOR=Black]The red lines are the ones I have appended.[/COLOR]

[/I]

[/I]

---

### Post by snowpine on 2010-07-11
To edit the file:

```
gksu gedit /etc/apt/sources.list
```

Type a # symbol at the beginning of the two malformed lines at the end and save the file. This will "comment out" these lines so Ubuntu skips those repositories and uses the default sources only (which happen to include FF 3.6.6). You should now be able to update your system.

---

### Post by drs305 on 2010-07-11
If you want to keep those lines, make sure the full address is in the line, with no "...".

> 
deb [http://ppa.launchpad.net/ubuntu-](http://ppa.launchpad.net/ubuntu-)**mozilla-daily**/ppa/ubuntu  lucid main
deb-src [http://ppa.launchpad.net/ubuntu-](http://ppa.launchpad.net/ubuntu-)**mozilla-daily**/ppa/ubuntu lucid main 


But this is the line with the problem I believe:
> 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


Change it to:
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by Masmidow on 2010-07-12
Worked like a charm! Should of occurred to me to check line 54! Doy! 

Thank you.

---

