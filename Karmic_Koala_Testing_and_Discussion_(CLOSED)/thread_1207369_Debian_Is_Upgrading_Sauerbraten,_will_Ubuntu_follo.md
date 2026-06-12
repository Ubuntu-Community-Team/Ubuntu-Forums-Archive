---
title: "Debian Is Upgrading Sauerbraten, will Ubuntu follow?"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2009-07-08
I've done some googling and found that debian will upgrade their version of sauer to the 2009 trooper addition, and thus closed Bug #527032.

I Know this is after the Debian import freeze, but is it possible for Ubuntu to import the newer version for Karmic?

---

### Post by tgpraveen on 2009-07-08
if u file a request for it, it will be done.
it sure will be nice to have it.

---

### Post by Col-1023 on 2009-07-08
There is already a bug report in launchpad to upgrade the game, and I think it's status is 'New".

Does another bug report need to be filed?

---

### Post by zekopeko on 2009-07-08
> **Col-1023 said:**
> There is already a bug report in launchpad to upgrade the game, and I think it's status is 'New".

Does another bug report need to be filed?

no. but you can confirm it. and please post a link to the bug here.

---

### Post by Col-1023 on 2009-07-08
The bugs url is,

[https://bugs.launchpad.net/bugs/379832](https://bugs.launchpad.net/bugs/379832)

It has been changed to Wishlist 39 minutes ago by Murat Güne&#351;.

I hope this mean there will be some movement.

---

### Post by autocrosser on 2009-07-08
I confirmed & commented---hope we get it.....

---

### Post by UbuWu on 2009-07-08
> **Col-1023 said:**
> The bugs url is,

[https://bugs.launchpad.net/bugs/379832](https://bugs.launchpad.net/bugs/379832)

It has been changed to Wishlist 39 minutes ago by Murat Güne&#351;.

I hope this mean there will be some movement.

When you want it synced from debian, you should change the bug to a sync request and subscribe ubuntu-universe-sponsors. See the process described here:

[https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

---

### Post by meeples on 2009-07-08
is this what you were loooking for?

> sauerbraten (0.0.20090504.dfsg-1) unstable; urgency=low
 
  [ Bruno "Fuddl" Kleinert ]
  * New Upstream Version (Closes: #527032)
  * Add a script to build pristine tarballs from upstream SVN repository
  * Update my email address in some files and in the uploaders field
  * Refresh patch to fix the clean target in the top-level makefile
  * Add a patch for top-level makefile to build binaries with debug symbols
  * Updated debian/copyright as we get sources via SVN, now
  * Bump Debian standards version to 3.8.2
    + Updated section for sauerbraten-dbg
    + Use unicode copyright symbol in debian/copyright
  * Bumped debhelper compatibility level to 7
  * Versioned binary dependency on sauerbraten-data is now put into a generated
    substitution variable
  * Update Vcs-* fields in debian/control to reflect new repository location
  * Minor changes in README.Debian about download location and from where the
    sources were obtained.
 
  [ Evgeni Golov ]
  * debian/rules:
    + Don't FTBFS with DEB_BUILD_OPTIONS=noopt.
      ($(info ...) isn't allowed before the first target)
    + Neither is $(error ...), so move it into the build target.
      Closes: #511719
 
Date: Wed,  08 Jul 2009 23:55:42 +0100
Changed-By: Michael Marley <michael@michaelmarley.com>
Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Origin: Debian/unstable
[https://launchpad.net/ubuntu/karmic/+source/sauerbraten/0.0.20090504.dfsg-1](https://launchpad.net/ubuntu/karmic/+source/sauerbraten/0.0.20090504.dfsg-1)

---

