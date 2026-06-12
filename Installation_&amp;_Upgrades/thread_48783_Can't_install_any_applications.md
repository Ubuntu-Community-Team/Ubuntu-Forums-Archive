---
title: "Can't install any applications"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by mirshafie on 2005-07-13
(I'm not sure if this is the right forum section. If not, please move this thread.)

I can't install any applications with apt-get or Synaptic anymore. In apt-get, I get this error:
> Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

This is after some nice people at #Ubuntu helped me link /usr from one partition to another.
I've tried renaming /var/lib/dpkg/available-old to /var/lib/dpkg/available, but it didn't help.

So, any ideas what I can do to correct this?
Thanks.

(Might aswell mention that I'm not at all familiar with Linux platforms.)

---

### Post by Xian on 2005-07-13
If renaming the file with the backup (which is the normal fix) didn't work then we'll have to edit that file by hand. My guess is that you have some text that begins with 'Priority' on the second line that just needs a colon immediately following the 'y', so that it would be 'Priority:'. 

If this isn't the case then post that file (the first 10 lines) and we'll have a look-see. :)

---

### Post by mirshafie on 2005-07-13
The first few lines seem completely taken out of context.

These are the 25 first lines:

> 

free and its discussion and development are open to everybody. The
 current source code is written to support several operating systems,
 including GNU/Linux, OS/2, Win32 and various Unices and is available
 under the GNU General Public License (commercial applications and
 backends are welcome, too, however).
 .
 This package includes the command line frontend scanimage, the saned
 server and the sane-find-scanner utility, along with their documentation.

Package: katomic
Priority: optional
Section: games
Installed-Size: 684
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdegames
Version: 4:3.4.0-0ubuntu2
Depends: kdelibs4 (>= 4:3.4.0), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libkdegames1 (>= 4:3.4.0), libqt3c102-mt (>= 3:3.3.3), libstdc++5 (>= 1:3.3.4-1)
Size: 106716
Description: Atomic Entertainment game for KDE
 This is a puzzle game, in which the object is to assemble a molecule
 from its atoms on a Sokoban-like board.  On each move, an atom goes
 as far as it can in a specified direction before being stopped by a
 wall or another atom.

---

### Post by Xian on 2005-07-14
I honestly don't see an error in that output.
Try updating dselect:
```
$ sudo dselect update
```

---

### Post by mirshafie on 2005-07-14
It works fine now! Thanks for the help! :)

---

