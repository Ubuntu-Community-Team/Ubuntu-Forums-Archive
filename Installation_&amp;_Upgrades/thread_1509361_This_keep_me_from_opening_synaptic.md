---
title: "This keep me from opening synaptic"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by tanapon on 2010-06-14
I downloaded a package for my printer to my desktop and installed it using Package Installer by double-clicking the file.

The package was not installed properly and there were error messages.

Then I tried to use Synaptic Package Manager to correct but this message will pop up first and close Synaptic.

***************************************************************
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
***************************************************************

How do I correct this problem or remove this package to allow Synaptic to run properly.

I can't use any apt-get in terminal as well. Same thing will happen in terminal.

---

### Post by oldos2er on 2010-06-14
What were the error messages?

---

### Post by 67GTA on 2010-06-14
Running ```
sudo dpkg --remove --force-remove-reinstreq mfc4800lpr
``` should get rid of it. Be sure to run ```
sudo apt-get update 
```afterwards to update the package cache.

---

