---
title: "To set up Dual boot from Linux, how do you keep the linux option on start-up pls?"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by zipher on 2008-10-25
Hi folks,

Here's where I'm at:

Have been using Hardy Heron very happily but this week decided to start a database project, so in order to do something 'more familiar' I got out the old Windows XP and Office CD'd so as to load MSAccess.

Well, what happened is, that using the Hearty Heron live CD I resized my partitions to make space for windows again. Next I loaded up windows on the 30Gigs alootted to it then loaded Office as well.

My prob that I'm having is, that when I boot up the system it goes straight into windows and doesn't let me choose between Windows and Linux.

If, however I boot up with the live CD once again, then I can access both partitions as separate file systems, in a fashion.

Question: How can I return to the dual-boot-on-startup status, which I enjoyed when installing Linux on top of Windows please?

Cheers,
Zipher

---

### Post by NoWayBill on 2008-10-25
Check this thread...
[http://ubuntuforums.org/showthread.php?t=224351&highlight=repair+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=repair+grub)

All that happened is that the Windo$e bootloader overwrote Grub in the MBR.
A simple fix.

---

