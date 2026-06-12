---
title: "SHA signatures on archive.ubuntu.com are empty"
date: 2024-04-16
forum: Installation &amp; Upgrades
---

### Post by carbonbased80 on 2024-04-16
The content of Packages.gz and Packages.xz is empty in [http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/)

This seems to have happened somewhat recently (these files used to be ~1.3MB+), and prevents me from being able to confirm the signatures of packages after download.

Is this a known issue?  I'm not where to look, or even where to report this (I'm guessing this isn't even the right forum, but I can't find an appropriate one).

Thanks,
Jeff

---

### Post by ajgreeny on 2024-04-16
You link followed by a few more clicks led me to [http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/by-hash/SHA256/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/by-hash/SHA256/) where the signatures are shown.
See my attached image.

---

### Post by carbonbased80 on 2024-04-16
> **ajgreeny said:**
> You link followed by a few more clicks led me to [http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/by-hash/SHA256/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble-updates/main/binary-amd64/by-hash/SHA256/) where the signatures are shown.
See my attached image.

I saw that, but I don't think that's the same as what I"m looking for... I'm actually not sure what that's telling me.

What I need is the SHA signatures of the packages in the repo.

For example, the focal archive is still available:
[http://archive.ubuntu.com/ubuntu/ubuntu/dists/focal/main/binary-amd64/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/focal/main/binary-amd64/)

And contains records for each packages:
eg.
[FONT=courier new]$ xzcat Packages.xz | head -16
Package: accountsservice
Architecture: amd64
Version: 0.6.55-0ubuntu11
Priority: standard
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian freedesktop.org maintainers <pkg-freedesktop-maintainers@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 452
Depends: dbus, libaccountsservice0 (= 0.6.55-0ubuntu11), libc6 (>= 2.4), libglib2.0-0 (>= 2.44), libpolkit-gobject-1-0 (>= 0.99)
Suggests: gnome-control-center
Filename: pool/main/a/accountsservice/accountsservice_0.6.55-0ubuntu11_amd64.deb
Size: 60940
MD5sum: 87a0e27c83950d864d901ceca0f2b49c
SHA1: ce92ea3783ca4ca6cdb5115381379f9c1317566b[/FONT]

---

### Post by deadflowr on 2024-04-16
You're looking in the wrong pocket.
noble-updates isn't used yet.

Development releases don't open up the -updates and -security channels until right before the official release.

What you want is here: [http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble/main/binary-amd64/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/noble/main/binary-amd64/)

---

