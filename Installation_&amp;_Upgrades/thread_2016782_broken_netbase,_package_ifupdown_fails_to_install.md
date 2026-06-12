---
title: "broken netbase, package ifupdown fails to install"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by macguges on 2012-07-04
While attempting to install unetbootin with Ubuntu Software Center and synaptic, my father's pc has entered a broken state.  I have long experience with linux, but not much with ubuntu.

I opened a terminal to run apt-get update and upgrade after failing with my original goal of installing unetbootin -- USC had complained it could not fetch packages from the us package site, though I could visit it with firefox, so I figured I would update the system first -- but apt-get upgrade failed on package ifupdown.   Apparently the package conflicts with netbase, which is either a dependency or an alternate to ifupdown.  I discovered a bug (#525667, [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/525667](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/525667)) that shows the same errors as my situation:

```
budtuba@wickinsmusic:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libgomp1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ifupdown
Suggested packages:
  rdnssd
The following packages will be upgraded:
  ifupdown
1 upgraded, 0 newly installed, 0 to remove and 712 not upgraded.
4 not fully installed or removed.
Need to get 0 B/54.1 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 161781 files and directories currently installed.)
Preparing to replace ifupdown 0.7~rc2+experimentalubuntu2 (using .../ifupdown_0.7.1ubuntu1_amd64.deb) ...
Unpacking replacement ifupdown ...
dpkg: error processing /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/init.d/networking', which is also in package netbase 5.0ubuntu1
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My father's pc will not complete upgrading successfully, and I want to restore the package system to an up to date, non-broken state.  My problem is the same as the bug #525667, except for the version differences, "ifupdown upgrade was offered but it would not install due to apparent conflict with netbase."   Apparently a fix was released two years ago, which is confusing.  Has the bug become "unfixed", or was it never properly fixed at all?  Could someone recommend how I should proceed?

Thanks in advance for any assistance.

---

### Post by atenz on 2012-07-06
I guess you have  **Ubuntu Quantal  Repository **enabled , since this package is present only in in quantal [SIZE=4][here]("https://launchpad.net/ubuntu/+source/ifupdown/0.7.1ubuntu1") .[/SIZE]

Also post the output of 

[HTML]cat /etc/apt/source.list[/HTML].
Because Similar problem had been reported in Ask Ubuntu[SIZE=4] [here .]("http://askubuntu.com/questions/160523/broken-apt-index-cant-fix-dependencies")[/SIZE]

---

### Post by macguges on 2012-07-08
> **atenz said:**
> I guess you have  **Ubuntu Quantal  Repository **enabled , since this package is present only in in quantal [SIZE=4][here]("https://launchpad.net/ubuntu/+source/ifupdown/0.7.1ubuntu1") .[/SIZE]

Also post the output of 

[HTML]cat /etc/apt/source.list[/HTML].
Because Similar problem had been reported in Ask Ubuntu[SIZE=4] [here .]("http://askubuntu.com/questions/160523/broken-apt-index-cant-fix-dependencies")[/SIZE]

You are right indeed.  Huh - I suppose I mistakenly chose the alpha release of Ubuntu to install here, because all of the repositories in sources.list refer to Quantal:

```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/ .Trash-1000/files/dists/quantal/main/binary-i386/

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/ .Trash-1000/files/dists/quantal/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/ dists/quantal/main/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/ dists/quantal/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/ quantal main restricted
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120601)]/.Trash-1000/files/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu quantal main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal universe
deb-src http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe
deb-src http://archive.ubuntu.com/ubuntu quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu quantal multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb http://archive.ubuntu.com/ubuntu quantal-security universe
deb-src http://archive.ubuntu.com/ubuntu quantal-security universe
deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb http://archive.canonical.com/ quantal partner
deb-src http://archive.canonical.com/ quantal partner
deb-src http://extras.ubuntu.com/ubuntu quantal main

```Alpha releases would not be the best choice for my dad, since he's a novice user still.  I wonder what the simplest procedure to downgrade his machine would be?

Ahh, I found this [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto).  I'll use the first method to downgrade this pc to Precise Pangolin.

---

### Post by macguges on 2012-07-08
I've found I cannot downgrade the system as planned because of this same broken dependency.  Any commands I've tried so far bring me around to the original error:

```
budtuba@wickinsmusic:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libgomp1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ifupdown
Suggested packages:
  rdnssd
The following packages will be upgraded:
  ifupdown
1 upgraded, 0 newly installed, 0 to remove and 764 not upgraded.
4 not fully installed or removed.
Need to get 0 B/54.1 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously unselected package ifupdown.
(Reading database ... 161781 files and directories currently installed.)
Preparing to replace ifupdown 0.7~rc2+experimentalubuntu2 (using .../ifupdown_0.7.1ubuntu1_amd64.deb) ...
Unpacking replacement ifupdown ...
[B]dpkg: error processing /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/init.d/networking', which is also in package netbase 5.0ubuntu1[/B]
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I've attempted to remove ifupdown with dpkg, which fails because ubuntu-minimal and upstart both depend on ifupdown.  What should be my next step?

```
budtuba@wickinsmusic:~$ sudo dpkg -r ifupdown
dpkg: dependency problems prevent removal of ifupdown:
 ubuntu-minimal depends on ifupdown.
 upstart depends on ifupdown (>= 0.6.10ubuntu5).
dpkg: error processing ifupdown (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 ifupdown

```

---

### Post by macguges on 2012-07-08
OK, I understand now that my attempted "downgrade" cannot work; using the broken package system to fix the broken package system is a non-starter, even if the system appears functional otherwise.  So I'm installing Precise Pangolin from scratch.

---

