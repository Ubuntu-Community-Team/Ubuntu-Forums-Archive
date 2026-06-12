---
title: "Frustrating installation problems..."
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by Fatal Force Sam on 2013-10-14
Alright - a bit of background info. I installed 12.04 Precise to get RAID installation support on a machine. Got the RAID 1 setup fine, and worked on the machine for a couple weeks. Then for reasons that will be left unsaid, I had to migrate that installation (physically plopped the HDD's into another machine, think server to desktop). 

I couldn't stand the universal menu bar that is an integral part of Unity, so I switched to the classic gnome desktop. Initially when I saw the monitors pop up with the logon screen, and I was able to log in successfully (after transplanting the software RAID to the new machine)I thought that was great. (having horrible experiences migrating HDD's in a Windows environment, I wasn't hopeful that such a drastic shift in underlying hardware would be successful at all) So having my desktop show up, and everything "appearing" to be ok I went on my merry way.

Well things have been getting progressively worse. I get random program crashes, from Xorg to my Nvidia drivers. By far the most frequent crashing is the shockwave player within Chrome (I've tried all applicable fixed and get no positive results). My launcher bar will randomly stop working at time and completely vanish. All these are more or less cosmetic, and I was able to live with it. Recently though I've been getting segmentation faults that I simply have no answers for. 

The first problem is when running Scons.
[COLOR=#0000ff]
tmp$ scons
Segmentation fault (core dumped)[/COLOR]

This lead me down all sorts of paths trying to figure it out, I eventually tried uninstalling scons in the attempt to do a clean install on it. However, I noticed something a bit strange when I did that. 

[COLOR=#0000ff]root@fatal:/tmp# apt-get remove scons[/COLOR]
[COLOR=#0000ff]Reading package lists... Done[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)
[/COLOR]
So again another segmentation fault that just crept up.

Another area these are occurring is when I do the following:

[COLOR=#0000ff]root@fatal:/tmp# apt-get upgrade[/COLOR]
[COLOR=#0000ff]Reading package lists... Done[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]root@fatal:/tmp# apt-get update[/COLOR]
[COLOR=#0000ff]Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://dl.google.com](http://dl.google.com) stable Release[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B][/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release[/COLOR]
[COLOR=#0000ff]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB][/COLOR]
[COLOR=#0000ff]Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release[/COLOR]
[COLOR=#0000ff]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release[/COLOR]
[COLOR=#0000ff]Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex[/COLOR]
[COLOR=#0000ff]Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [420 kB][/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en[/COLOR]
[COLOR=#0000ff]Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B][/COLOR]
[COLOR=#0000ff]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [97.8 kB][/COLOR]
[COLOR=#0000ff]Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B][/COLOR]
[COLOR=#0000ff]Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [695 kB][/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#0000ff]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB][/COLOR]
[COLOR=#0000ff]Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [219 kB][/COLOR]
[COLOR=#0000ff]Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB][/COLOR]
[COLOR=#0000ff]Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [715 kB][/COLOR]
[COLOR=#0000ff]Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB][/COLOR]
[COLOR=#0000ff]Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [223 kB][/COLOR]
[COLOR=#0000ff]Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB][/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en[/COLOR]
[COLOR=#0000ff]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en[/COLOR]
[COLOR=#0000ff]Fetched 2,486 kB in 3s (702 kB/s)[/COLOR]
[COLOR=#0000ff]Reading package lists... Done[/COLOR]
[COLOR=#0000ff]root@fatal:/tmp# apt-get upgrade[/COLOR]
[COLOR=#0000ff]Reading package lists... Done[/COLOR]
[COLOR=#0000ff]Building dependency tree[/COLOR]
[COLOR=#0000ff]Reading state information... Done[/COLOR]
[COLOR=#0000ff]The following packages will be upgraded:[/COLOR]
[COLOR=#0000ff]  apport python-apport python-problem-report ubuntu-tweak[/COLOR]
[COLOR=#0000ff]4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
[COLOR=#0000ff]24 not fully installed or removed.[/COLOR]
[COLOR=#0000ff]Need to get 0 B/1,249 kB of archives.[/COLOR]
[COLOR=#0000ff]After this operation, 105 kB of additional disk space will be used.[/COLOR]
[COLOR=#0000ff]Do you want to continue [Y/n]? Y[/COLOR]
[COLOR=#0000ff](Reading database ... 229343 files and directories currently installed.)[/COLOR]
[COLOR=#0000ff]Preparing to replace python-problem-report 2.0.1-0ubuntu17.4 (using .../python-problem-report_2.0.1-0ubuntu17.5_all.deb) ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: warning: subprocess old pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]dpkg - trying script from the new package instead ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error processing /var/cache/apt/archives/python-problem-report_2.0.1-0ubuntu17.5_all.deb (--unpack):[/COLOR]
[COLOR=#0000ff] subprocess new pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error while cleaning up:[/COLOR]
[COLOR=#0000ff] subprocess installed post-installation script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Preparing to replace python-apport 2.0.1-0ubuntu17.4 (using .../python-apport_2.0.1-0ubuntu17.5_all.deb) ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: warning: subprocess old pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]dpkg - trying script from the new package instead ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error processing /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.5_all.deb (--unpack):[/COLOR]
[COLOR=#0000ff] subprocess new pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error while cleaning up:[/COLOR]
[COLOR=#0000ff] subprocess installed post-installation script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Preparing to replace apport 2.0.1-0ubuntu17.4 (using .../apport_2.0.1-0ubuntu17.5_all.deb) ...[/COLOR]
[COLOR=#0000ff]apport stop/waiting[/COLOR]
[COLOR=#0000ff]Segmentation fault[/COLOR]
[COLOR=#0000ff]dpkg: warning: subprocess old pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]dpkg - trying script from the new package instead ...[/COLOR]
[COLOR=#0000ff]Segmentation fault[/COLOR]
[COLOR=#0000ff]dpkg: error processing /var/cache/apt/archives/apport_2.0.1-0ubuntu17.5_all.deb (--unpack):[/COLOR]
[COLOR=#0000ff] subprocess new pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]apport start/running[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error while cleaning up:[/COLOR]
[COLOR=#0000ff] subprocess installed post-installation script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Preparing to replace ubuntu-tweak 0.8.5-1~precise2 (using .../ubuntu-tweak_0.8.6-1~precise1_all.deb) ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: warning: subprocess old pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]dpkg - trying script from the new package instead ...[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error processing /var/cache/apt/archives/ubuntu-tweak_0.8.6-1~precise1_all.deb (--unpack):[/COLOR]
[COLOR=#0000ff] subprocess new pre-removal script returned error exit status 139[/COLOR]
[COLOR=#0000ff]No apport report written because MaxReports is reached already[/COLOR]
[COLOR=#0000ff]Segmentation fault (core dumped)[/COLOR]
[COLOR=#0000ff]dpkg: error while cleaning up:[/COLOR]
[COLOR=#0000ff] subprocess installed post-installation script returned error exit status 139[/COLOR]
[COLOR=#0000ff]Errors were encountered while processing:[/COLOR]
[COLOR=#0000ff] /var/cache/apt/archives/python-problem-report_2.0.1-0ubuntu17.5_all.deb[/COLOR]
[COLOR=#0000ff] /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.5_all.deb[/COLOR]
[COLOR=#0000ff] /var/cache/apt/archives/apport_2.0.1-0ubuntu17.5_all.deb[/COLOR]
[COLOR=#0000ff] /var/cache/apt/archives/ubuntu-tweak_0.8.6-1~precise1_all.deb[/COLOR]
[COLOR=#0000ff]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
[COLOR=#0000ff]root@fatal:/tmp#

[/COLOR]Needless to say, I am at a loss. I feel like there is a fundamental package that is just broken on my current machine that was installed with the original server in mind. Ideally, I would be able to fix my current installation so that I don't have to go through the process of retweaking a vanilla Ubuntu install as well as setting up required programs.

Thanks for help in advance.

~Sam

---

### Post by Fatal Force Sam on 2013-10-14
Also - weird stuff like above is just happening. Note the command sequence I did,

apt-get upgrade
->immediate seg fault
apt-get update
-> updated succesfully
apt-get upgrade
-> doesn't seg fault immediately, but does segfault on following individual packages

Also, I intend to do several passes of mem-test tomorrow morning to rule that out.

---

### Post by Fatal Force Sam on 2013-10-14
Another update - I was diagnosing a lot remotely yesterday, and was sending remote "sudo reboot" commands to restart my machine in hopes of a fix. Well, when I went to log on this morning locally, the machine just crashed to a terminal prompt. So I hard powered down, gave it a little bit, and started the machine back up. All of a sudden everything that was broken before is now fixed.. I can "sudo apt-get upgrade", I can build Gem5 with Scons, and I haven't even had a Chrome Shockwave Player crash in about an hour!

Basically, I'm leaning more and more towards it being a RAM problem. If this isn't the case, I have absolutely no idea what is wrong with the installation.. I'll run a Memtest and report back :)

---

### Post by heir4c on 2013-10-14
Info about segmentation fault:
[http://www.oit.uci.edu/help/manuals/uci.unix.guide/common_mistakes_and_pitfalls/segmentation.html](http://www.oit.uci.edu/help/manuals/uci.unix.guide/common_mistakes_and_pitfalls/segmentation.html)
[https://en.wikipedia.org/wiki/Segmentation_fault](https://en.wikipedia.org/wiki/Segmentation_fault)
[https://en.wikipedia.org/wiki/Core_dump](https://en.wikipedia.org/wiki/Core_dump)

There is some problem with a program that will use some addresses on the memory that is reserved for the system.
What you first can do is: Open Software&Updates and look on the first TAB to the Backports. Uncheck that, and do again a update and upgrade. (And maybe choose a other server to download the update).
Does that help?

---

### Post by Fatal Force Sam on 2013-10-14
I'm a software developer, I know what a segmentation fault is :D 

The issue, as indicated by the simple fact that a hard reboot allowed me to operate as normal (for a short time), was with a RAM stick. 600+ errors within 1 minute of Memtest. This hopefully will no longer be an issue as I've replaced the bad module.

Thanks for reading.

---

### Post by heir4c on 2013-10-14
Ok,:D:D:D:D:D

---

