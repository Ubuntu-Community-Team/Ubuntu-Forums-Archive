---
title: "Why would the Ubuntu installer sometimes detect windows and sometimes not?"
date: 2023-09-19
forum: Installation &amp; Upgrades
---

### Post by nick2023 on 2023-09-19
Hi, I'm trying to set up my machine as a dual boot machine and have done so on many occasions.  I'm running Windows 10 and I'm trying to install Ubuntu 20.04.  It appears that sometimes the installer detects Windows and sometimes it doesn't.  Usually when I try a second time it finds it however, on this occasion I've now tried multiple times and it still hasn't found it.  I don't suppose anybody might know what the problem is?

Regards

Nick

---

### Post by oldfred on 2023-09-19
If Windows fast startup or bitlocker is on, then the Ubuntu installer cannot find it.
And Windows may update settings and turn fast startup back on when updating.

Windows also may update UEFI firmware which reverts many UEFI settings to defaults. You have to review any settings you have to change. One of my systems has 7 settings, so I have to keep a list. Another just works with no changes.

---

### Post by guiverc on 2023-09-19
Also please be specific with details.

Ubuntu 20.04 LTS is available with many installers, and I don't see you actually stating which you're asking about.

- Ubuntu 20.04 LTS Server uses the `subiquity` installer.
- Ubuntu 20.04 LTS Desktop uses the `ubiquity` installer
- (*initially an alternate 20.04 LTS Desktop ISO existed using the canary installer, but I doubt you mean that, nor that it still exists*; *it wasn't available via 'click to download' options, needing to be downloaded by file*)
- Ubuntu 20.04 LTS *flavors* will have `ubiquity` or `calamares` installers; though you don't mention *flavor* so I suspect not `calamares` either.

If the windows system is *hibernated *(*which includes fastboot enabled*) it can also be ignored by some installers, except for the option of *Erase Disk and install*. If using *live* media (*and most media is **live*), and you mount a disk/partition, the installer if started when the partition is still mounted can ignore that partition too. As for behavior, the exact installer you're using matters as they can behave slightly differently for the same situation.

---

### Post by nick2023 on 2023-09-20
It seems that disabling legacy did the trick.  Not entirely sure when or where that got switched on but thanks for the link which told me about it

---

