---
title: "Install synaptic package manager"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by phaedrus2 on 2014-02-22
How would I search to find which repository contains synaptic?

Thanks in advance.


Kubuntu 12.04

---

### Post by Bashing-om on 2014-02-22
phaedrus2l Hi !
To find relevant info for a package do:
```

apt-cache search synaptic

```
Which returns several possibilities.
Now get specific:
```

apt-cache show synaptic

```
that output shows that "synaptic" is in the universe repository -> insure that the universe repository is enabled in the software Center, and
To install:
```

sudo apt-get install synaptic

```
all there is to it. Wonderful little Package Management System that it is !

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by phaedrus2 on 2014-02-22
> **Bashing-om said:**
> phaedrus2l Hi !
To find relevant info for a package do:
```

apt-cache search synaptic

```
Which returns several possibilities.
Now get specific:
```

apt-cache show synaptic

```
that output shows that "synaptic" is in the universe repository -> insure that the universe repository is enabled in the software Center, and
To install:
```

sudo apt-get install synaptic

```
all there is to it. Wonderful little Package Management System that it is ![INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


Thanks for the speedy reply.

The first command produced...

[HTML]:~$ apt-cache search synaptic
muon - package manager for KDE
sessioninstaller - APT based installer using PackageKit's session DBus API
xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-dev - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-dev-lts-quantal - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-dev-lts-raring - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-dev-lts-saucy - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-lts-quantal - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-quantal-dbg - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-raring - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-raring-dbg - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-saucy - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-saucy-dbg - Synaptics TouchPad driver for X.Org server
[/HTML]

...none of which seemed significant to my search. Next...

[HTML]:~$ apt-cache show synaptic
N: Can't select versions from package 'synaptic' as it is purely virtual
N: No packages found
[/HTML]

...so of course the install would fail.

---

### Post by Bashing-om on 2014-02-22
phaedrus2; One of us has a typo (??)
OR is the universe repository not enabled on your system ?

Because -> this is the return !
> 
sysop@1310mini:~$ apt-cache show synaptic
Package: synaptic
Priority: optional
[color=red]==>>Section: universe/admin[/color]
Installed-Size: 7672
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Michael Vogt <mvo@debian.org>
Architecture: amd64
Version: 0.80.2
Depends: libapt-inst1.5 (>= 0.8.16~exp12), libapt-pkg4.12 (>= 0.8.16~exp12), libc6 (>= 2.14), libept1.4.12 (>= 1.0.9), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.14.0), libgtk-3-0 (>= 3.0.0), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.6), libvte-2.90-9 (>= 1:0.27.2), libx11-6, libxapian22, hicolor-icon-theme
Recommends: gksu | kdebase-bin | policykit-1, libgtk2-perl (>= 1:1.130), rarian-compat
Suggests: dwww, menu, deborphan, apt-xapian-index, tasksel, software-properties-gtk
Conflicts: menu (<< 2.1.11)
Filename: pool/universe/s/synaptic/synaptic_0.80.2_amd64.deb
Size: 2447910
MD5sum: 0eef458952f1d5e89274c202819477bd
SHA1: 7d7650ded39bbe71be538c4d0df8d21f4016bed0
SHA256: 3f0e3dde5d2f563a1e66b49ec76e22119dade04807c4a5cf1cb357ffcf0c538c
Description-en: Graphical package manager
 Synaptic is a graphical package management tool based on GTK+ and APT.
 Synaptic enables you to install, upgrade and remove software packages in
 a user friendly way.
 .
 Besides these basic functions the following features are provided:
  * Search and filter the list of available packages
  * Perform smart system upgrades
  * Fix broken package dependencies
  * Edit the list of used repositories (sources.list)
  * Download the latest changelog of a package
  * Configure packages through the debconf system
  * Browse all available documentation related to a package (dwww is required)
Description-md5: d4fb8e90c9684f1113e56123c017d85f
Homepage: [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
Description-md5: d4fb8e90c9684f1113e56123c017d85f
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: lubuntu-desktop, ubuntustudio-desktop

sysop@1310mini:~$ 


I would not lie to ya nor deceive ya.
In this case it is as I say.

[INDENT]the truth
[INDENT][INDENT]the whole truth
[INDENT][INDENT][INDENT]and nothing less then the truth
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by phaedrus2 on 2014-02-23
> **Bashing-om said:**
> OR is the universe repository not enabled on your system ?


That was the problem. It's a chrubuntu KDE 12.04 installation with the "universe" repository disabled as default. I'm new to Ubuntu/Debian based systems so I missed the obvious.

Thanks for the help.

---

### Post by Bashing-om on 2014-02-26
phaedrus2; Hey,

Pleased ya got it solved, and was but a small matter.
Please mark this post solved; aids others seeking a solution and helps keep the forum tidy.
- 1st post -> thread tools -

'buntu has a learning curve, as all operating systems do, and you are well on your way.

just
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

