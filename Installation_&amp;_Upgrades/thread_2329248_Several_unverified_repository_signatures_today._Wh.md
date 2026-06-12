---
title: "Several unverified repository signatures today. Why and how to fix?"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2016-06-29
Yesterday, my normal updates worked correctly.

Today, I'm getting the following message, "The following signatures couldn't be verified because the public key is not available." It is happening for the following repositories:
[LIST]
[*]VirtualBox [http://download.virtualbox.org](http://download.virtualbox.org)
[*]PlayOnLinux [http://deb.playonlinux.com](http://deb.playonlinux.com)
[*]Canonical [http://archive.canonical.com](http://archive.canonical.com)
[*]Ubuntu [http://extras.ubuntu.com](http://extras.ubuntu.com)
[*]Ubuntu [http://archive.ubuntu.com](http://archive.ubuntu.com)
[*]Chromium [http://dl.google.com](http://dl.google.com)
[*]Launchpad [http://ppa.launchpad.net](http://ppa.launchpad.net)
[*]Dropbox [http://linux.dropbox.com](http://linux.dropbox.com)
[*]Intel [https://download.01.org](https://download.01.org)
[/LIST]
The errors from [FONT=lucida console]sudo apt update[/FONT] are as follows.
```
W: GPG error: http://download.virtualbox.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: http://deb.playonlinux.com trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991 NO_PUBKEY 1397BC53640DB551
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52A794126E3AB2D3
W: GPG error: http://linux.dropbox.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
```What's going on? I know that I can manually add the public keys with [FONT=lucida console]sudo apt-key[/FONT], but is that safe to do?

---

### Post by Frogs Hair on 2016-06-29
I have some of the same sources with no errors. It may be a temporary glitch on the download server in use.

---

### Post by Paddy Landau on 2016-06-30
I have discovered the source of this problem, quite by accident.

It is a [bug relating to GPG]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540"). I have used the workaround, which fortunately worked, although it was rather repetitive entering a couple of dozen keys!

---

### Post by Bashing-om on 2016-06-30
@Paddy Landau; Hey, hey ...

Thanks for the heads up and solution.
Noted.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]we are all on this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

