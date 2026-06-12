---
title: "Got a command line when rebooting after upgrade"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by Ann J on 2010-03-15
Hi All,

I just installed some software upgrades via the Upgrade Manager, and got a dialog window telling me to reboot. I did so, but a command line appeared:

[CENTER]GNU GRUB version 1.97~beta 4[INDENT][LEFT][ Minimal BASH-like line editing is supported. For the first words TAB lists possible completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>
[/LEFT]
[/INDENT][LEFT]I'm not sure what to do with this at all, and don't know how to enter ubuntu. I'm using Ubuntu 9.10 installed with Wubi on an HP notebook. Any help is appreciated!
[/LEFT]
[/CENTER]

---

### Post by Arand on 2010-03-15
You might be seeing this issue: [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
seems to be the primary workaround.
Probably a good idea to backup copy the current C:\wubildr before overwriting it.
- Arand

---

### Post by Ann J on 2010-03-17
> **Arand said:**
> You might be seeing this issue: [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
seems to be the primary workaround.
Probably a good idea to backup copy the current C:\wubildr before overwriting it.
- Arand

Thanks, I did that and it did the trick!

---

