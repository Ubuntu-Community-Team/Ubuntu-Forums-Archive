---
title: "Installing on SLI system"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2007-04-22
Can you install Ubuntu on an SLI based system? I'm getting a black screen during installation of Feisty no matter what I try unless I remove one of the video cards.

---

### Post by kevpatts on 2007-04-22
Just to let you know, I got it to work by removing the second card, installing, opening Synaptic (from the Admin menu) clicking the updates tab and selecting the pre-release one (third down) to get the latest drivers, then installing nvidia-glx-new and doing the obvious change to xorg.conf. I then rebooted X to make sure eveything was okay and then shutdown, reinstalled the second card and SLI bracket and booted into a fully working SLI enabled Ubuntu installation.

Sweet!
Kevpatts

---

### Post by shredsalot on 2007-07-27
so, what are the obvious changes? :(

---

