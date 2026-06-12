---
title: "gksudo &quot;update-manager&quot;"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Rory on 2006-06-01
**A thread devoted exclusively to people's helpful advice and experiences in upgrading via this command:**

```
gksudo "update-manager"
```

Instructions here:
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Few points of clarification:
gksudo "update-manager" -d command is no longer necessary.  The "-d" is only for beta releases.

This command automatically updates your repository file.

It disables all third party repos.

Does it still change the "breezy" references to "dapper" references for the third-party repos as it disables them?

I have a lot of third-party repos.  I'd be interested to hear other people's experiences upgrading systems with lots of third-party repos via this command.

**Post questions, comments, advice & experiences related to upgrading via the *gksudo "update-manager*" command in this thread.**

---

### Post by Rory on 2006-06-01
Following my post, above, I have a more specific question:

I'm holding off experimenting with this command for a bit because I'm a bit worried about my k7 kernel (linux-k7 and ati card packages (xorg-driver-fglrx, fglrx-kernel-k7, fglrx-control).  

The kernel version and these ati packages must match or you can no longer boot in.    I've been using the ubuntu-fglrx-k7 package from the Seveas repo ([http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/)) that forces both to match so you don't run in to this problem when Ubuntu releases a new kernel version.  

With the gksudo "update-manager" command disabling third-party packages, I don't know what my fate will be if I try upgrading in this manner.  

Thoughts?

---

