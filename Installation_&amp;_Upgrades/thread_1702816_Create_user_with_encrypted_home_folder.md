---
title: "Create user with encrypted home folder"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Timmmy on 2011-03-08
Hi,

I want to create a user with a encrypted home folder.
I tried "sudo adduser --encrypt-home username" but I get following error "adduser: Could not find program named `ecryptfs-setup-private' in $PATH".

I installed the cryptsetup package but without result.

Any ideas?

Thx,

Timmmy

---

### Post by uopjohnson on 2011-05-01
You need ecryptfs-utils.

---

