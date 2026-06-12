---
title: "Which command is used to create encrypted swap during installation?"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by AlbertP on 2014-05-23
Hello,

I have messed with my swap and want to re-create the swap partition as it is made during 14.04 installation with encrypted home directory. Does anybody know what cryptsetup commands would be required to format the partition here?

I do NOT want to add a key to set it up for hibernation (as in most how-to's), I just want to have the original cryptswap partition back, as it was after installation, which does not ask for a key when booting. I have already discovered that the UUID is in /etc/crypttab, so don't need help on that step either, this is just about formatting the partition the same way it used to be formatted.

---

