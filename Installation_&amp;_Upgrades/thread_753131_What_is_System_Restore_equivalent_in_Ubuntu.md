---
title: "What is System Restore equivalent in Ubuntu?"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by LaRoza on 2008-04-12
> **damd70 said:**
> When I try to download?install any pakages, programs ao applications I get an error saying that "installation failed, error(1)"  All of a sudden I would like to know how to do the Ubuntu equivalent of system restore, so I can take the PC back to before this started happening. I beleive it happened after I unstalled an app called AUTOMATIX2.  I need to learn how to get back to befor I installed that program.  Thank you for you help in advance.

There is no registry in Ubuntu, like there is in Windows.

The equivalent is backing up the files that are edited.

You can uninstall any packages that are causing problems using the package manager.

Creating a similiar application as the Windows System Restore is difficult, as the Windows registry is the focus of it, and it is meant to overcome the fragility of Windows. I know, I am trying to make one: [http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665)

I did finish it, but I am redoing it. Hopefully, it may be useful.

---

### Post by yaztromo on 2008-04-12
Aptitude has a similar facility where if you install a package it will remember all the dependencies it installed for it and remove those too should you choose to uninstall.

---

### Post by schiznik on 2008-04-12
I'd recommend a reinstall unfortunately :(

Automatix does some nasty stuff (forcing installs, overwriting configs) that can easily break your system.

---

