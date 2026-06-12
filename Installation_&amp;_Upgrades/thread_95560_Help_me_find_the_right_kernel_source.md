---
title: "Help me find the right kernel source"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by diamond on 2005-11-26
I am trying to build  the latest version of FUSE so I can get ntfsmount working. In order to do so, I need the kernel source, which apparently is not included with a standard Ubuntu install.

I am running Ubuntu 5.10, and when I check my kernel version (uname -r), I get:

2.6.12-9-386

Checking the Synaptic Package Manager for kernel source packages, it appears that the latest version for which source is available is 2.6.11-7. Clearly that won't do.

So I decided to go straight to the source (hah!): kernel.org. Browsing through their archives, I see versions all the way up to 2.6.12.6, and then one that is just labeled 2.6.12.

So what do I need? I'm afraid to install the wrong sources.

---

### Post by Xian on 2005-11-26
[QUOTE=diamond]Checking the Synaptic Package Manager for kernel source packages, it appears that the latest version for which source is available is 2.6.11-7. Clearly that won't do.[/QUOTE]
You are looking under the wrong name.
Do a search for 'linux-source'.

---

### Post by diamond on 2005-11-26
Bingo!

Thank you very much.

---

### Post by Xian on 2005-11-26
Great, don't forget you will still need to untar that package.

---

