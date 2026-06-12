---
title: "hang on 8.10 with iwlagn driver"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by mferrier on 2008-11-03
Hi, I upgraded from hardy to intrepid over the weekend, and today my laptop (dell xps 1330) has frozen 6 or 7 times, requiring a hard power-off to restart. I've narrowed it down (I think) to my wireless card; turning on the killswitch and disabling it in the NetworkManager and switching to wired seems to have fixed it.

When a freeze happens, on my laptop I notice the WLAN, capslock and numlock icons are blinking rhythmically.

I've pored over my syslog/kern.log/etc but haven't been able to find anything indicating what the problem is.

Does anyone have any advice or suggestions to help me diagnose and fix this problem?

Thanks!

---

### Post by Pettman on 2008-11-03
I also got trouble with the iwlagn driver. It got better when I installed the backport-modules package but there are still problems. The system have gone pretty inresponsive on me a couple of times, I can still move the mouse and magic sysrq works some of the time but clicking doesn't do anything.

---

### Post by mferrier on 2008-11-06
Found the related bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/276990)

---

