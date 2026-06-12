---
title: "understanding memtest86 results"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by helix_r on 2007-12-12
I recently decided to test my memory with memtest86. Much to my surprise, I got errors immediately starting at test #2 or 3. I have a AMD64 x2 4200 running on a ASUS A8N SLI premium mobo with matched 2x1 GB of DDR (PC3200, low latency modules from mushkin). 

Although I do see firefox crash regularly (a few times a day), I have attributed it to the nagging problems of the 64 bit version of the ubuntu distro. Occasionally, about once a week or so, I will leave the computer on for an extended time only to come back to a black screen. Other than that, the computer is stable and functional.

When I test the modules individually, only one of them gives errors.


My questions are the following:

1) How can my machine even boot if memtest86 shows that the RAM is faulty?? The errors start appearing very quickly, its not like the errors start appearing on the very last test. I  had thought that problems with memory bring the machine down very quickly, yet I have a pretty usable system even with faulty RAM. Is this possible? 

2) Should my RAM pass ALL the tests? 

3) I haven't messed with frequencies, voltages and CAS settings because the advice on the internet seems very unreliable in these matters. I am more interested in stability than balls-out performance. Do I need to start messing with bios settings? Where is a good resource for how to do this right?

Thanks!

---

### Post by tgalati4 on 2007-12-12
I'm dealing with similar issues.  Go into your BIOS and start increasing latency of  your memory.  Go from say 5-5-5-15 to 6-6-6-15 and see if your errors go away.  The other thing to try is leave memory speed alone and declock the processor under "Frequency Control".

You want 30 complete passes with no errors to get decent reliability.  Memory errors are simply unacceptable.  One of my machines has a uptime of over 200 days.  You shouldn't need to reboot or accept freezes, that's not part of linux.

If none of this works, then it's time for new RAM.

---

