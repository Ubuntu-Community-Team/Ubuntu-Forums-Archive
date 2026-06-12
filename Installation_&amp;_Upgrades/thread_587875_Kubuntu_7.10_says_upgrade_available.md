---
title: "Kubuntu 7.10 says upgrade available?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2007-10-23
Fresh install of Kubuntu 7.10 Gutsy on reformatted partition.  The system occasionally says an upgrade is available, and goes through a few MB downloads to report it has now upgraded to 7.10.
With the most recent "upgrade", it seemed to download a bit more, and now appears to have frozen with a box titled "Distribution Upgrade" and the pointer pointing at Installing the upgrades, with progress bar stuck on 0%.

How do I get out of this?  If I try to close the box, there is a warning strongly recommending it is not stopped.

TIA

Peter

---

### Post by KhaaL on 2007-10-23
I also have the exact same problem on the same distro. I downloaded a RC image, but I don't think that's what causing it... I think it's because I removed two installed packages (due to regression bugs) that kubuntu-desktop depends on...

Would be nice to know how to get out of this situation

---

### Post by sneakypeteb on 2007-10-23
There's a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/154771]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/154771")

---

### Post by jynyl on 2007-10-28
This bug appears to be fixed now.  An update to adept via the normal update method seems to fix it.  The fixed version is adept 2.1.3ubuntu17.1 (and some associated adept modules).

---

