---
title: "Dell Inspiron Mini 10v - Lucid 10.04 beta - netbook ed"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by barrydrake on 2010-04-13
I'm delighted with Lynx on my new Inspiron Mini V10.  It installed out of the box, and is just great!  I've had the occasioan nuisance problem.  It seemed to be doing a forced disk check on bootup far too often.  Often it would reach around 70% and freeze.  I got into it using a rescue boot card, and altered /boot/grub/grub.cfg (yes, I know you don't edit that, and why).  I removed the 'quiet splash' so I could see what was happening.  

It reported that /dev/sda1 had been uncleanly mounted, The boot process then invoked fsck which was reporting an error.  The boot then continued for a couple of lines of output and froze.

I ran fsck /dev/sda1 from the rescuer card and this seemed able to fix the problem for now.

I had put GRUB_CMDLINE_LINUX="noapic" into /etc/default/grub as this was a suggestion on another forum for correcting the problem.  I'd also considered nolapic and noacpi or even GRUB_CMDLINE_LINUX="noapic, nolapic, noacpi" but I'd really like to understand what these commands do before trying it.  (Oh, before anyopne asks, I did run sudo update-grub after the edit).

Any thoughts?

---

