---
title: "Why offered upgrade to grub-common"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2010-07-22
I'm running v 10.04, which was an upgrade from v 9.10.

When I issue the command grub-install -v, I get the result: grub-install (GNU GRUB 0.97).

The update manager just offered me an update to the package grub-common, which I know from bitter experience is part of grub2, not grub.

Using the package manager, I confirmed that I have a version of grub-common installed. I also confirmed that I did not have the package grub-pc installed.

Since I'm using grub, why do I have grub-common installed at all?

Can I safely delete it?

Leslie

---

### Post by oldfred on 2010-07-23
Grub common is called common for a reason. It is used with both grub legacy and grub2. Do not delete it and you should let it update.

---

### Post by lesliek on 2010-07-24
Thanks for your help, oldfred.

I did as you suggested.

Leslie

---

