---
title: "upgreade trouble, kernel panic on boot"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by fredex on 2006-04-22
Tried today to upgrade to Breezy (from Hoary) using these instructions:

[https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

Instructions seem to imply that the system will automatically reboot during the process, but it didn't. It choked on firefox (note that the instructions I had DO NOT tell you to remove firefox first, too bad I didn't see the correct ones earlier). I tried rerunning "update all packages" and it tried to update fewer packages but still died. not knowing what else to do I rebooted, and it came up with no X, only text logins.

So I browsed the forums, found discussion of deborphan so I did:
sudo aptitude install deborphan
which ran for quite a while before ending. rebooted now I get a kernel panic upon boot that says: 
Audit (1145735133.288:0): initialized
Kernel panic - not syncing: VFS: unable to mount rootfs on unknown-block(0,0)

Am I hosed? I'd just as soon not lose what's on the drive...

Suggestions welcomed, Thanks!

Fred

---

