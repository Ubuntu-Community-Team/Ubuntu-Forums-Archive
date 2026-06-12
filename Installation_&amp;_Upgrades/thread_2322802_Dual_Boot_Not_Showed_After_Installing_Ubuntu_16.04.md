---
title: "Dual Boot Not Showed After Installing Ubuntu 16.04 (Twice)"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by masum3 on 2016-04-30
Hello, there.
I recently installed Ubuntu 16.04 from a live usb stick on a windows 10 (original, upgraded from 8.1). Used USB installer to create ubuntu disk. I have installed linux distributions many times before as well. But this time, after I installed, dual boot menu is not showed and it straight goes to Windows. So, I installed again. But it remains the same. I tried "Boot repair" from live usb and also made bootmenudisplay=yes on windows. Since windows is in UEFI mode, the second time I went to UEFI start on windows and then installed Ubuntu. Still the same.

Here is a summary of what I did so far. First time, I installed Ubuntu with "Something else" in partition. 3000 MB for swap space, 50000 MB for home, 150000 MB for root, 1000 MB for boot (if the order is correct). Then I installed it like I usually do. But no boot menu. So I used boot repair on live disk and bcdedit on windows. No luck. I will post the boot info text file too if necessary.

Looking for a solution. Thanks in advance.

---

### Post by oldfred on 2016-04-30
Probably best to not have a separate /boot partition. With most desktops a bit more maintenance often required. But ok.

But did you install in UEFI boot mode? How you boot install media, UEFI or BIOS/CSM is how it installs.

What brand/model system. Some need work arounds.
What CPU, & video chip?

Post link to Summary Report from Boot-Repair to see if something is mis-configured.
Do not post entire report, just link.

---

