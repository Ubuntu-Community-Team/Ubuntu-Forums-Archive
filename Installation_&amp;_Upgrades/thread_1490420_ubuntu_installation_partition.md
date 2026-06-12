---
title: "ubuntu installation partition"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by michaelisneat on 2010-05-22
I'm trying to install ubuntu 10.04 on an old computer, but the installer doesn't have any listed partitions and I can't go any further. The hard drive I'm trying to install it to was just formated in Windows 7, it's a clean hard drive. Uh, how am I supposed to install it?

---

### Post by darkod on 2010-05-22
If the installer doesn't see it at all, provided the disk is actually recognized by BIOS, it usually means it was used in raid and has raid metadata remains on it.

Boot the ubuntu cd in live mode, open terminal and execute:

sudo dmraid -r -E /dev/sda (if it's the only hdd it will be /dev/sda, if not adjust the command)

If that asks you if you want to remove the raid settings, that was your problem. Just remove them and start the installer again.

Of course, do the above only if you are not actually running raid, it sounds like you are not. Otherwise it will destroy your array.

If that didn't help, we'll need more info.

---

