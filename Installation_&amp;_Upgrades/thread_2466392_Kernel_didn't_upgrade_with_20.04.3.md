---
title: "Kernel didn't upgrade with 20.04.3"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by jlc2010 on 2021-08-26
Hi,

My system just upgraded to 20.04.3, but the kernel didn't.  The same thing happened with the upgrade to 20.04.2.  How to I force a complete refresh of the 20.04.3 release without having to reinstall everything?  I'm afraid I might be missing some other items, too.

Thanks!

    -John

---

### Post by Dennis N on 2021-08-26
You would want the install what's called the Hardware Enablement (HWE) Stack to get newer kernels.
See this to learn how:
[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

---

### Post by mikewhatever on 2021-08-27
There is no need to upgrade the kernel, or "force a complete refresh" of anything. The original 5.4 kernel is supported/updated for 5 years.
Now, there are merrits to switch to newer kernels with relatively new hardware (say, 5 years or newer), but otherwise all you get is regressions and zero benefits.

---

### Post by guiverc on 2021-08-27
There have been two kernel stack choices for LTS releases for the last ~*decade*.

**GA** - the default kernel stack, the most *stable* thus default for Server installs.

**HWE** - *hardware enablment* which changes at .2 & later upgrades; default to Ubuntu Desktop 20.04 LTS installs and later (but **not** earlier installs). All *flavor* desktop installs from 20.04.2 and up default to HWE (like earlier releases 18.04, 16.04, 14.04, 12.04..) but not 20.04 or 20.04.1

- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

**The ISO used to install dictates which kernel stack is default** (eg. Ubuntu Server, Lubuntu 20.04 & 20.04.1 default to GA, .... etc with others default to HWE such as Ubuntu Desktop 20.04 LTS, 20.04.1, Ubuntu Desktop 20.04.2, Ubuntu Desktop 20.04.3, Lubuntu 20.04.2, 20.04.3 etc)[I].

[/I](*I'm using Lubuntu as example - as I know it best*)

You can change the stack in use, even have both installed (*and pick which you use at boot time*, ie. `grub`), but using the more *stable* GA stack is default for many ISOs, and *not* the sign of a problem - just your installation media.

---

### Post by jlc2010 on 2021-08-28
I thought when I read the notes on the release of 20.04.3 that the HWE version was part of the upgrade.  If not, I'll just wait until 22.04 to upgrade again.  

Thanks for everyone's response!

    -John

---

### Post by Impavidus on 2021-08-29
So on what kernel are you? If you're on 5.4, you'll stay on 5.4 and just get the security patches. If you're on 5.8, the HWE kernel, you should be automatically upgraded to 5.11. If that doesn't happen, it means that kernel installation failed or you've a missing metapackage, so that the new kernels don't get pulled in.```
uname -r
```

---

### Post by MAFoElffen on 2021-08-30
> **jlc2010 said:**
> I thought when I read the notes on the release of 20.04.3 that the HWE version was part of the upgrade.  If not, I'll just wait until 22.04 to upgrade again.  
They upgraded some of the Hardware Enablement Stack packages as a small part of that, but that doesn't mean that it would automatically install if you didn't have it already... LOL. It doesn't work that way.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/ChangeSummary/20.04.3#Kernel_and_Hardware_support_updates](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/ChangeSummary/20.04.3#Kernel_and_Hardware_support_updates)
[https://discourse.ubuntu.com/t/focal-fossa-20-04-3-lts-point-release-status-tracking/22948](https://discourse.ubuntu.com/t/focal-fossa-20-04-3-lts-point-release-status-tracking/22948)

---

### Post by jlc2010 on 2021-08-30
Yes, I'm on 5.4.  I thought when it hit 20.04.3, the kernel would be part of the upgrade.

---

