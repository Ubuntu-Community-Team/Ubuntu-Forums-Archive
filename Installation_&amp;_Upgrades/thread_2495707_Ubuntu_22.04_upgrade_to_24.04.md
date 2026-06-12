---
title: "Ubuntu 22.04 upgrade to 24.04"
date: 2024-02-27
forum: Installation &amp; Upgrades
---

### Post by micckey on 2024-02-27
Hello guys. So I was following steps on this site [https://linuxconfig.org/ubuntu-upgrade-to-24-04-noble-numbat-a-step-by-step-howto-guide](https://linuxconfig.org/ubuntu-upgrade-to-24-04-noble-numbat-a-step-by-step-howto-guide) to upgrade my ubuntu version. However the upgrade stopped abruptly and when I tried rebooting I got this error: systemd-oomd.socket loaded failed failed Userspace Out-Of-Memory (OOM) Killer Socket. When I try booting in recovery mode and repair the broken packages, I get the screen attached

---

### Post by TheFu on 2024-02-28
With some upgrades, things fail.  It is usually related to having added PPAs or other manually installed software that isn't park of the core Ubuntu Repos.

So, you made some backups. If they are well made, then you have lots of options. You can restore them and try again, being certain to have a clean, fully upgraded system BEFORE making the attempt again.  If your backups require reinstalling a new OS, which is how mine work, then I'd just do a fresh install of 22.04, then selectively restore my backups as needed.  

There's something good about a fresh install without any old cruft from prior OS versions. They just work better and are less confusing because subsystems that have been replaced between the releases are fully removed. That's a good thing.

---

### Post by Frogs Hair on 2024-02-28
24.04 is still in development so I'm not sure why this tutorial was published without addressing the possible problems . When that tutorial was published 24.04 was still an alpha release and unfit to be a daily driver and that still may be the case. There is no reason to upgrade early other than for testing purposes.

---

### Post by TheFu on 2024-02-28
> **Frogs Hair said:**
> 24.04 is still in development so I'm not sure why this tutorial was published without addressing the possible problems . When that tutorial was published 24.04 was still an alpha release and unfit to be a daily driver and that still may be the case. There is no reason to upgrade early other than for testing purposes.

I completely missed that.  **24.04 isn't released and has about 8 weeks longer before it will be.  **

Even then, I wouldn't rush to install it unless I can have downtime. The earliest I would install it is mid-June after any big initial release issues are found and fixed.  If stability is really paramount for your needs, wait until 24.04.1 is released - probably in August.

For someone who isn't part of the testing team, now is NOT the time to install 24.04.

_New the the enemy of stable._

---

### Post by grahammechanical on 2024-02-29
From my experience, what breaks the system is the removal of obsolete packages. In the development version the obsolete packages would normally be removed as their replacements are installed.

There is a risk of breakages when upgrading from one LTS version to another LTS version. This is likely to happen if the desktop has been modified. Some applications may not have been developed to run on the new LTS version. They may not be modified to run on the new desktop toolkits that hare being used. So, the application may have what the upgrade process considers as obsolete packages.

Read carefully the list of obsolete packages. It might be possible to stop the removal of certain packages while allowing the removal of others.

Another thing to watch out for is the automatic change of Firefox and Thunderbird from deb package to snap package. I do not mind snap packages. Others do not want them. Personal choice.

Regards

---

