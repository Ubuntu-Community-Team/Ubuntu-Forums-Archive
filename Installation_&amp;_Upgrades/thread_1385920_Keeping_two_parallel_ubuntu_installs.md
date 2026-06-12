---
title: "Keeping two parallel ubuntu installs"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by AndersAA on 2010-01-20
I have the need currently to keep both 32bit and 64bit ubuntu versions installed (can't use chroot, it's testing display adapter drivers and that means booting with a 32bit kernel).

Is there any easy way to deal with this?  The boot images are generally named the same so a 64bit kernel upgrade could overwrite a 32bit one, and os-detect goes a bit crazy as well.

---

### Post by darkod on 2010-01-20
I don't think the kernel upgrade can mess anything up since you are doing an update when you are boted into the particular version and it will apply the update only to it.

But not sur how the automatic discovery of both OSs will go, haven't tried that so far. And you might need something to tell them apart in grub boot menu.

---

### Post by Kevbert on 2010-01-20
The biggest complaint is generally knowing which installation on boot is the 64 bit version and which is the 32 bit one as grub/grub2 just shows the kernel revision (which will be the same). The two installations are totally independent of each other. When upgrading kernels the first one listed is always the one that was last upgraded. 
Upgrades may need to be done separately as some versions on certain packages will only be for 32 bit and others 64 bit so you can't easily download one set of upgrades while running 32 bit and then transfer them to the 64 bit version.

---

### Post by AndersAA on 2010-01-20
> **darkod said:**
> I don't think the kernel upgrade can mess anything up since you are doing an update when you are boted into the particular version and it will apply the update only to it.

Forgot to mention I had a shared /boot, I've split those up now though.

---

### Post by AndersAA on 2010-01-20
Seeing as there was no quick fix for this I looked into it, and modifying /etc/lsb-release seems fairly safe, atleast as long as you edit the description.  I doubt anything relies on parsing that.

Modified mine to this now:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10 32-bit"

os-prober picks up the change

---

