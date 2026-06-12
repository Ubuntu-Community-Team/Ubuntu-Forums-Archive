---
title: "Livepatch"
date: 2024-05-15
forum: Installation &amp; Upgrades
---

### Post by BigYellowDog on 2024-05-15
I keep getting the message when I log into my server
> *** Livepatch has fixed kernel vulnerabilities. System restart recommended on the closest maintenance window ***
I've done an [COLOR=#0000cd]apt update[/COLOR] & [COLOR=#0000cd]apt upgrade[/COLOR] & a [COLOR=#0000cd]reboot [/COLOR]and I still keep getting the same message.

I'm running 22.04 with 5.15.0-105-generic kernel installed.

---

### Post by #&amp;thj^% on 2024-05-15
You may want to add yourself to a current bug: [https://bugs.launchpad.net/canonical-livepatch-client/+bug/2028377](https://bugs.launchpad.net/canonical-livepatch-client/+bug/2028377)

---

### Post by deadflowr on 2024-05-15
You're not rebooting into the latest kernel.
Current latest is the 5.15.0-107-generic kernel.

---

### Post by BigYellowDog on 2024-05-15
Fixed. I had the reboot message for a few days, but haven't hand time to post.  Must have been another kernel patch in the last few days.

---

