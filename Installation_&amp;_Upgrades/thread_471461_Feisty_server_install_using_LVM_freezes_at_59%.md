---
title: "Feisty server install using LVM freezes at 59%"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by ealex292 on 2007-06-12
A few months ago I successfully (mostly) set up a server using Edgy, LVM, and Xen, and more recently I accidentally hosed it trying to resize a partition.

I've been trying to reinstall using an LVM root partition (which worked before), but haven't had any success.

The Feisty install process froze at 55% of the way through "Installing the base system", while "Unpacking module-init-tools".

I tried activating a new console, and got a whole bunch of messages spewed at me, ending with

```

BUG: unable to handle NULL pointer dereference at virtual address 00000010
[...]
Recursive die() failure, output suppressed
<1>Fixing recursive fault but reboot is needed!
```

An attempt to reinstall Edgy failed with a similar message at 59% of the way through (I don't remember what the current package was).

Any suggestions on how to get the install to work?

---

