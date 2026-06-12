---
title: "Install-HP DV6119 laptop"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Archius on 2007-01-31
AMD X2 TL-50
GeForce Go 6150 NVIDIA Graphics

Those are the two most important things, and broadcom NIC card. After I install Ubuntu, and I try to load it, all I get is a slightly pixilated black screen that grows to a pixilated white screen, or vice versa, and just goes back and forth. Strange thing is, it does the very same thing with Ubuntu, Kubuntu, Xubuntu, Knopptix, and Puppy. Any ideas how to fix this problem? I know the RAM is good, already tested with memtest 86+. I'm pulling my hair out here.

---

### Post by marknu1 on 2007-11-18
Bummer to see that nobody responded to this.  I just tried to install Ubuntu on my dv6119 and I am having the same problem.  I've only tried the 64-bit ubuntu and the 32-bit versions of Ubuntu and Kubuntu, but it's the same story.  All versions were 7.10.  I can't believe this is still an issue, seeing as the original post is from January of this year...

---

### Post by gsplitt on 2008-03-10
Sorry to post a response so late after your message, but hey, I could only get linux on my box so fast...

So it seems the issue is easily resolved with the following steps:

[LIST]
[*]when the cd menu first loads, fit F6. This will allow you to simply type the following into the command line
[*]Type " noapic " at the end of the field, and hit enter
[*]Tada, problem solved!
[/LIST]

Hope this helped! Take care.

---

