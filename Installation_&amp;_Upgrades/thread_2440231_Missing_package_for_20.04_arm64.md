---
title: "Missing package for 20.04 arm64"
date: 2020-04-07
forum: Installation &amp; Upgrades
---

### Post by 0n0w1c on 2020-04-07
An important package for me is missing from the repository for the new 20.04 arm64: freeipa-client
It appears all of the supporting packages exist, just not the install script that pulls them all together.

This package does exist for 19.10 arm64.

---

### Post by deadflowr on 2020-04-07
It was removed at some point because of this:
[https://bugs.launchpad.net/ubuntu/+source/dogtag-pki/+bug/1858967]("https://bugs.launchpad.net/ubuntu/+source/dogtag-pki/+bug/1858967")

But it looks like a new version has beeen recently uploaded ( a few hours ago)
[https://launchpad.net/ubuntu/focal/+source/freeipa]("https://launchpad.net/ubuntu/focal/+source/freeipa")
Current shows in proposed.

---

### Post by 0n0w1c on 2020-04-08
I filed a bug report (#1871474) shortly after posting here and the Ubuntu/Debian package maintainers responded quickly, and indeed, the package is now available.
However, It only configures a client as there seems to be a remaining bug in the server. The client portion is what I needed to proceed.

Thank you!

---

