---
title: "Parallel boot in Ubuntu?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by crabby on 2008-04-29
Hi guys,

I know that other distro's can use parallel boot to sharply decrease boot time, but I have been unable to find any information regarding this for ubuntu.

Is it possible? And if so, how?

I am running 8.04 x64

Thanks,

crabby

---

### Post by lemming465 on 2008-05-05
Ubuntu has converted to event-based boot using their "upstart" tool.  Ironically, this has had a bigger effect on shutdown times than startup times so far, but their motive isn't really to reduce start up times, it's to get removable media handling right.

I haven't seen a lot of documentation on upstart yet, but I haven't looked recently.  I think Fedora 9 is converting to upstart.

Currently most of the delay in boot isn't due to stuff which could run in parallel but doesn't.  It's due to a mixture of a) slow hardware POST due to legacy BIOS idiocy b) excessive unnecessary disk access by applications which are launching in stupid ways  c) mediocre scheduling of the I/O which does have to occur.

Good luck working on this; it's an interesting and difficult topic.  It also tends to interact with things like laptop disk idling and hibernation.

---

