---
title: "Error when installing with Windows 7 (32-bit)"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by basitr846 on 2011-11-06
[FONT="Arial"][SIZE="3"][/SIZE][/FONT]
Hello, I want to try out the new Ubuntu 11.10 OS and I have tried to install it inside Windows 7 (32-bit) using the "Wubi" utility included on the ISO file, the first phase of the installation was successfully completed and required a reboot, which i have did. But now when my PC starts it gives the following message:
"Try (hd0,0): NTFS5: No wubildr"
The system just stays there and nothing happened even i waited for about 1.5 hours. Please help me with this issue ASAP.

---

### Post by AppleWiz on 2011-11-06
Ouch!

I had much the same problem, the installer for k/ubuntu expects your disk to be partitioned exactly as it wants, otherwise it will trash the Windows7 boot sequence. The Ubuntu installer seems to have some serious bugs.

Hopefully you have a backup of your most important data from Windows? Even if not you may be able to recover/repair Windows using an install disc. Then if you feel brave, proceed to install Ubuntu again, after reading everything about partitioning.

~Rob

---

### Post by basitr846 on 2011-11-06
[SIZE=4][FONT=Arial]I can still boot into windows and there is nothing wrong with the windows partition. But i think the error is saying that it cannot find 'wubildr'. What is 'wubildr'?[/FONT][/SIZE]

---

