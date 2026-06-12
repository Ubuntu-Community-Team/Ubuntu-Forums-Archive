---
title: "There are known issues with ZFS in Ubuntu 21.10 causing filesystem corruption"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by Flimm on 2021-10-16
I use ZFS on Ubuntu, and I upgrade to Ubuntu 21.10, and I started experiencing filesystem corruption. I decided to install a fresh install of Ubuntu 21.10 with ZFS, only to experience filesystem corruption again.

Turns out, this is a known issue! In [the release notes]("https://discourse.ubuntu.com/t/impish-indri-release-notes/21951"), it says:

> The version of the ZFS driver included in the 5.13.0-19 kernel contains [a bug]("https://bugs.launchpad.net/bugs/1906476") that can result in filesystem corruption. Users of ZFS are advised to wait until the first Stable Release Update of the kernel in 21.10 before upgrading.

So if you're installing Ubuntu 21.10, don't select the ZFS option! And don't upgrade to Ubuntu 21.10 if you use ZFS.

---

