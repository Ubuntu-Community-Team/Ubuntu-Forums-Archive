---
title: "Why do I need to add keys to update?"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by alexander.s.farley on 2014-10-13
After starting with a clean Ubuntu 14 install on a VPS, I try:
```
apt-get update
```
which fails on:
```
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

```

The following command fixed the error message:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4097EAF437D05B5

```

Why is it that a fresh installation of Ubuntu requires this? Is this normal? Is there any way to update and refresh all keys without such arcane commands?

---

### Post by kc1di on 2014-10-13
Hello alexander.s.farley  and welcome to Ubuntu,

you should only have to enter a key once,  It usually happens because you've changed the default apt-sources list to include new software that was not in the original list. Such as ppa's or enabling a backport or some other repository that was not in the original install.

---

