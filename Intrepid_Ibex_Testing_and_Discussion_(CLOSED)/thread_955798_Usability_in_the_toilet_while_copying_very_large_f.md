---
title: "Usability in the toilet while copying very large files"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by heavensblade23 on 2008-10-22
Running Intrepid Ibex 8.10 64-bit, I get extremely poor system performance whenever a large file operations are taking place.  Examples are copying multiple gigs of files, moving multiple gigs of files, or unzipping very large archives.  Firefox becomes unresponsive and/or dims every other minute, the package manager takes 3-4 times as long to install a new package, and so forth.  I'm using Nautilus to copy the files, but I believe I tried a simple 'cp' in the terminal with similar results.

I have a pretty beefy system (C2D, 4 gigs of RAM, hard drive with 32mb cache) and this problem doesn't occur in Vista, so I'm stumped.

System monitor looks pretty normal even while usability is going into the toilet.  Not much RAM or CPU used, no significant paging going on.

Bug filed:
[https://bugs.launchpad.net/ubuntu/+bug/287742](https://bugs.launchpad.net/ubuntu/+bug/287742)

---

### Post by FuturePilot on 2008-10-22
Probably related to this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094")

---

### Post by PinkFloyd102489 on 2008-10-22
I thought you meant you were getting crashes while USING the toilet. :P


Yeah it sounds like the heavy I/O bug. Is this on a laptop?

---

### Post by heavensblade23 on 2008-10-22
> **FuturePilot said:**
> Probably related to this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094")

Indeed.  Switching to a different scheduler (deadline or the old one, anticipatory) helps a lot.  CFQ was enabled by default a bit too early, it seems.

---

### Post by heavensblade23 on 2008-10-22
> **PinkFloyd102489 said:**
> 
Yeah it sounds like the heavy I/O bug. Is this on a laptop?

No, it's on a desktop with a very recent 7200rpm drive.

---

### Post by jfernyhough on 2008-10-22
Wowsers - thanks for this thread.

I looked at the bug report and tried changing the scheduler from CFQ to Deadline - boot time went down, and after logging in the desktop is usable much more quickly. In fact, the entire system feels more responsive.

I added " elevator=deadline " to my boot options.

---

