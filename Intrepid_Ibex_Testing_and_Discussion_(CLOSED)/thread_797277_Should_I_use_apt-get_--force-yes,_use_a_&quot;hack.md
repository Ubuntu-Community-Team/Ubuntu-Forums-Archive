---
title: "Should I use apt-get --force-yes, use a &quot;hack&quot; or wait?"
date: 2008-05-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by KIAaze on 2008-05-17
I'm currently facing the following problem:
I cannot install **libnet-dbus-perl** (and therefore all packages depending on it) because it depends on **perlapi-5.8.8**, which is supposed to be provided by **perl-base**.

However the current hardy version, **perl-base (5.10.0-9)**, provides **perlapi-5.10.0** instead of **perlapi-5.8.8**.

Should I install libnet-dbus-perl using --force-yes?
How dangerous is this really?

Or should I rebuild/reinstall the perl-base (5.10.0-9) package so that it provides perlapi-5.8.8 too?

Or should I just wait until it's fixed in the repos?

Currently, what bothers me most is that gnome-applets can't be installed because of this. ^^'

---

### Post by geirha on 2008-05-17
Hardy provides [perl-base](http://packages.ubuntu.com/hardy/perl-base) 5.8.8, so the 5.10 you got, you must've got from some other repository. Uninstalling it and installing Hardy's perl-base should fix your problem.

I'd stay away from using --force-yes at all costs.

EDIT: Heh, I didn't notice this was the intrepid forum.

---

### Post by KIAaze on 2008-05-17
> **geirha said:**
> EDIT: Heh, I didn't notice this was the intrepid forum.

Yes, and I've been to intrepid with some upgrades. ^^

---

### Post by plun on 2008-05-17
Well, just some opinions and the way I handle it

I am always using the terminal, no hidden issues as with a GUI.

Apt-get or Aptitude

These commands

```
sudo apt-get update && sudo apt-get dist-upgrade
```


```
sudo aptitude update && sudo aptitude dist-upgrade
```


Aptitude gives you proposals how to fix a breakage.

You can "toggle" solutions with a No answer

(dist upgrade or just upgrade can be discussed....)


**There is a major risk for the moment with a total  breakage if you chooses wrong Aptitude proposal.**


My situation for the moment:

```
The following packages are BROKEN:
  libffi4 
The following packages will be upgraded:
  gcc-4.2-base 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.4kB of archives. After unpacking 20.5kB will be freed.
The following packages have unmet dependencies:
  libffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.3-4ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
apport-gtk
apturl
awn-extras-applets-trunk
awn-manager-trunk
deskbar-applet
envyng-gtk
gdebi
gedit
gnome-app-install
gnome-games
gnome-volume-manager
jockey-gtk
libdeskbar-tracker
libffi4
python-awn-trunk
python-gnome2-desktop
python-gnome2-extras
python-gnome2-extras-dev
python-gtksourceview2
python-launchpad-integration
python-notify
python-vte
rhythmbox
sonata
system-config-printer-gnome
totem
totem-gstreamer
totem-mozilla
totem-plugins
ubufox
update-manager
update-notifier

Leave the following dependencies unresolved:
gedit-common recommends gedit
gnome-games-data recommends gnome-games
nautilus recommends gnome-app-install
avant-window-navigator-trunk recommends awn-manager-trunk (>= 0.2)
Score is -2142
[B]
Accept this solution? [Y/n/q/?] q[/B]
Abandoning all efforts to resolve these dependencies.
Abort.

```

So for me its just to wait.... therefore I am using apt-get when
Aptitudes proposal is unacceptable for me.

This is the challenge and maybe someone can sort this out....:)

---

### Post by KIAaze on 2008-05-17
I chose the hack solution in the end and it worked. I have my applets back. :)

1)I downloaded the hardy and intrepid versions of the perl-base .deb packages
2)extracted them into the same directory (first intrepid, then hardy).
3)extracted the control file from the intrepid package and modified it as follows:
```
Package: perl-base
Source: perl
Version: **5.10.0-10**
Architecture: i386
Essential: yes
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Brendan O'Dea <bod@debian.org>
Installed-Size: 2296
Pre-Depends: libc6 (>= 2.4)
Suggests: perl
Conflicts: autoconf2.13 (<< 2.13-45), libscalar-list-utils-perl (<< 1:1.18-1), libxsloader-perl (<< 0.08-1)
Replaces: libclass-multimethods-perl (<< 1.70-4), libperl5.8 (<< 5.8.0-20), libscalar-list-utils-perl, libxsloader-perl, perl (<< 5.8.8-5), perl-modules (<< 5.8.8-8)
Provides: libscalar-list-utils-perl, libxsloader-perl, perl5-base, perlapi-5.10.0, **perlapi-5.8.8**
Section: perl
Priority: required
Description: The Pathologically Eclectic Rubbish Lister
 A scripting language with delusions of full language-hood, Perl is used
 in many system scripts and utilities.
 .
 This is a stripped down Perl with only essential libraries.  To make
 full use of Perl, you'll want to install the `perl', `perl-modules' and
 optionally `perl-doc' packages which supplement this one.

```
4)Rebuilt and installed the package.
5)Installed gnome-applets. :D

But now I suddenly have a bunch of new upgrades available and update manager wants to upgrade perl-base from 5.10.0-10 to 5.10.0-10. :confused:
Running all upgrades except perl-base for the moment.

---

