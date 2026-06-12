---
title: "Software Updater Problem"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by Allister_Graham on 2015-04-23
Today when I tried to launch Software Updater in order to upgrade to the newly-release Ubuntu 15.04. However, it failed to open. I ran apt-get from the terminal, and it spat out the following error message:

```
E: The package avast4workstation:i386 needs to be reinstalled, but I can't find an archive for it.
```

I have failed to reinstall or upgrade this package (it is Avast Antivirus). I no longer want it, anyway.

I'm running Ubuntu 14.10 64-bit on a Toshiba Satellite C50.

Please help. :-(

---

### Post by slickymaster on 2015-04-23
What happens if you try```
sudo dpkg --purge --force-remove-reinstreq avast4workstation:i386
```
If successful, try then to upgrade.

---

