---
title: "kernel panic after upgrade to 7.10"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Duffy on 2007-10-23
I just did the upgrade to 7.10 from 7.04 on three systems. One failed completely and had to be reinstalled from CD, one went perfect, and the other well, sort of. 

When it tries to boot using the latest kernel 2.6.22-14, it hangs up about have way through the boot cycle. Using the recovery method of booting, it gives the error of "41.775761 Kernel panic - not syncing fatal exception in interrupt".

It will boot using the older kernel of 2.6.20-16 just fine. 

I tried uninstalling the 2.6.22-14 kernel, rebooting and reinstalliing and rebooting, but same problem.

Tried update-initramfs, but same issue.

Any suggestions?

---

### Post by ptipton on 2007-10-23
I have exactly the same issue. Upgraded one machine perfectly and second gives identical error as above. Main difference on second machine is wireless network card so tried removing the windows driver but this made no difference.

---

### Post by Duffy on 2007-10-23
Hmmm, the machine with the problem also has a wireless card. Interesting thing is that I can no longer get the wireless card working. 7.04 was a dream compared to this nightmare.

---

### Post by hal8000 on 2007-10-23
I had a slightly different issue with Gutsy, no wireless card in my case but with the 2.6.22 kernel, booting would halt at "waiting for root filesystem".
My solution is using my own custom 2.6.21 kernel, no initramfs for me as the drivers needed to start ubuntu are compiled into the kernel. I will also watch this thread for a solution, I may recompile the gutsy kernel to find out whats wrong with my system.

---

### Post by ptipton on 2007-10-23
The wireless card is definitly the problem in my case. Its based on realtek chip and if I remove it the system boots fine. There are lots of posts on getting wireless to work in gutsy so will try following them.

---

### Post by Duffy on 2007-10-25
Yup, on further examination of the lines that precede the kernel panic, it is the wireless card that is causing the issue.  Damn, when you buy a wireless card to work specifically with Linux, you expect it to continue working in new versions.  This is just not right.

---

