---
title: "Not really help, more a query."
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2005-05-25
I previously had 4.10 on my primary slave, along with a FAT32 shared partition with nothing important on it.

I got 5.04 so I started over. Previously, when I installed 4.10 I removed my primary master (Win XP) as I can select at boot time which disk to go with. This time I left it in, but I messed up with the boot loader and had to start over, which I did with the primary master removed.

The first time (XP disk in) I was asked if the hardware clock was set to UTC (mine isn't). With 4.10 I wasn't asked this, and I assumed it was one of the differences. However, when I did it again with the XP disk out, I wasn't asked and it assumed my HWC was UTC.

Is it meant to happen this way?

Kind of makes sense, if there's another disk in there, chances are it's a Windows disk so the HWC will be local time. But why not ask the question even if there isn't?

---

