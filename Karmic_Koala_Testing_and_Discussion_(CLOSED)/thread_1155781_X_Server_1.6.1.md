---
title: "X Server 1.6.1"
date: 2009-05-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-11
Anyone know why we dont have the /1 point revision for the x server yet in karmic?

---

### Post by Triptol on 2009-05-11
Packager had not time to package it?

---

### Post by taavikko on 2009-05-11
> **Triptol said:**
> Packager had not time to package it?

Or no one has yet had the time to upload it
[https://edge.launchpad.net/ubuntu/+source/xorg-server](https://edge.launchpad.net/ubuntu/+source/xorg-server)

---

### Post by Nullack on 2009-05-11
Bryce is usually onto it quick - was wondering if there was some issue with the .1 point release

---

### Post by Nullack on 2009-05-20
Still isnt there - anyone know whats happening?

---

### Post by vishalrao on 2009-05-21
Maybe Bryce et al are in UDS mode for the moment :)

---

### Post by rudenko_ruslan on 2009-05-24
> X.Org X Server 1.6.1.901 (1.6.2 RC 1)
Release Date: 2009-5-8
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ruslan-desktop 2.6.30-5-generic #6-Ubuntu SMP Mon May 11 19:56:30 UTC 2009 i686
Build Date: 23 May 2009  09:44:43PM
xorg-server 2:1.6.1.901-2ubuntu1 (buildd@rothera.buildd) 
That's from mine "Xorg.0.log" file ;)

---

### Post by fifth on 2009-05-24
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.6.1.901 (1.6.2 RC 1)
Release Date: 2009-5-8
X Protocol Version 11, Revision 0
```

Update came through today.

---

### Post by vishalrao on 2009-05-24
Well yes: [https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html)

---

### Post by Nullack on 2009-05-24
They skipped .1 and went straight to the RC of .2

---

### Post by Kareeser on 2009-05-24
> - obsolete:
100_xserver_exa_force_greedy.patch

Heh, so I'm guessing I shouldn't try upgrading for fear of breaking X again :)

---

