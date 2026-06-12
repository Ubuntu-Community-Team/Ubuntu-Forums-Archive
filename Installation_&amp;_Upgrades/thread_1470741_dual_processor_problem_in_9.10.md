---
title: "dual processor problem in 9.10"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by hatebreed on 2010-05-03
I need help!! I can't get my second cpu to recognize. Is there a way to make the kernel see the 2nd cpu?

---

### Post by hatebreed on 2010-05-03
well I found out what is going on, this is what I found in my log file

weird, boot CPU (#0) not listed by the BIOS.
SMP motherboard not detected.
SMP disabled
Brought up 1 CPUs
Total of 1 processors activated (801.77 BogoMIPS).
CPU0 attaching NULL sched-domain.

so there lies my problem. so the question is how do I get the kernel to see the 2nd cpu?

---

### Post by hatebreed on 2010-05-03
booted up knoppix and it found both cpus. Its' using kernel 2.4 smp. So what I would like to do is get a 2.6 smp kernel put out by ubuntu that would work, any thoughts?

---

### Post by hatebreed on 2010-05-04
Finally got it!!!! go into /etc/default/grub (as root of course)
look for grub_cmdline_linux_default="" add apic=off apci=off in the quotes then save. now go to a shell as root type update-grub, then reboot. such a simple fix for a big problem. turns out that tyan boards and linux don't see eye to eye with these settings. it's actually a kernel issue because the older kernels work, such as 2.4, and xp works. I don't know what was changed and why it was but it should be addressed so people don't go through the same things I just did. anyways that's the fix.

---

### Post by Thomas9777 on 2010-06-04
Thanks a bunch for posting the solution your self. Even though you had to figure it out on your own. I have the same problem, and this info is great!!!!!

---

