---
title: "ubuntu 3.2.0-15-generic upgrade caused desktop desapeared"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2012-02-17
Upgrade from ubuntu 11.10 ubuntu to 3.2.0-15-generic upgrade caused desktop desapeared
when I launch ubuntu it only show ubuntu
start up with ununtu the word ubuntu and the 5 dots under.
insteas of launching the desktop, a terminal windows is automatically opened,
this terminale works fine.
Is there a way to repair this.

---

### Post by IPEX-731BA5DD06 on 2012-02-17
3.2.0-15 is for Precise 12.04 and not generally for 11.10

I'd suggest you load the kernel 3.0.0.15-17 for 11.10 and use Synaptic to remove the 3.2.0-15 kernel.

Some people are using 3.3.? Kernels on 12.04, but they are razor edge bleeding...errr beta testers.

Didn't work for you, its not ready for 11.10.

---

### Post by uRock on 2012-02-17
If you only installed the kernel, then remove it and use the older kernel, which you should be able to select an older kernel from the grub menu. If you found yourself upgrading to 12.04, then I recommend a clean install of 11.10 as 12.04 is not yet released for production installs.

---

