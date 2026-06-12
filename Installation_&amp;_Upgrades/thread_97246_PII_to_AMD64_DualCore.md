---
title: "PII to AMD64 DualCore"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by mariuss on 2005-11-30
I upgraded my hardware from an old Pentium II based system to a new dual core AMD64. Basically I just moved the hard drive from one computer to another.

The first small issue was the fact that the hard drive showed up as a different device in the new system, I had to use a live cd to edit fstab and grub's menu.lst.

The second minor issue, solved by the live cd again, was the fact the new system has an nvidia video card while the old had an ati card. Editing xorg.conf, based on values from the live cd, fixed this.

The system is up and running now, but there still are problems.

The biggest one is that I have 386 binaries and I would need the amd64 ones (for the kernel I would need the smp version). How do I do the switch?

Also, while I can use the new DVD unit it does not seem to work properly. How do install the proper driver? The more general question would be, how do I enforce a new hardware detection?

Am I better off reinstalling from scratch? If I do that, is there a way to preserve my existing home folder?

---

