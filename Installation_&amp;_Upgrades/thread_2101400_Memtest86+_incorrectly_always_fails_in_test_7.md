---
title: "Memtest86+ incorrectly always fails in test 7"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by OneOfMany07 on 2013-01-04
The Memtest86+ version built in to the Lubuntu install media for 12.10 x64 always gives me tons of errors when I run test 7 on any machine.  I downloaded the version from Memtest86+'s website and it works as expected.

I just installed Lubuntu again and the version on the hard drive, in the Grub boot menu, is doing the same thing.  I assume it was copied on during installation from the version built in to the OS.

Both times I saw this issue has been on Intel based machines (one Nehalem, and one Sandybridge).  Originally I thought the problem was the motherboard on the Sandybridge as it happened with multiple DIMMs and CPUs, but replacing the motherboard didn't fix the problem.  Only using a different source for the application did.

Has anyone else seen this?  And where do I file the bug?  All the suggested components looked very desktop'y.

---

### Post by Doug S on 2013-01-04
This is a known problem. Please review, and maybe add notes to [the bug report]("https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209") . there are also links to 3 duplicate bug reports (which I did not look at).

---

### Post by OneOfMany07 on 2013-01-04
Awesome, thanks!  I'm surprised this has lasted for so long.  Hopefully they update the release media (ISOs) soon.

---

