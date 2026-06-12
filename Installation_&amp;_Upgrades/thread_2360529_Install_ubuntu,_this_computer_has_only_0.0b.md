---
title: "Install ubuntu, this computer has only 0.0b"
date: 2017-05-05
forum: Installation &amp; Upgrades
---

### Post by redanaconda on 2017-05-05
Hi, 
I'm having the same issue while trying to install ubuntu on a physical machine along with Win 10. (Dell Precision Tower 3620). I have two drives and have set aside 30 GB space for ubuntu on the second one (i.e. the one which has not the windows on it). Secure boot is off in the bios. In general i'm trying to follow [this guide]("https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN"):

---

### Post by QIII on 2017-05-05
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2356163](https://ubuntuforums.org/showthread.php?t=2356163)

Please do not hijack threads.  

Your problem is entirely different from the problem described in the other thread.  You will get better help in your own thread rather that confounding the thread of another user.

---

### Post by oldfred on 2017-05-05
Does UEFI have drives set for RAID or Intel SRT?
You need AHCI if so.

Post this:
sudo parted -l

---

### Post by yancek on 2017-05-05
When you say you have two "drives", are you using windowspeak which means you actually have two partitions on one drive or do you actually have two separate physical hard drives?
Usually best to shrink windows to create unallocated space on which to install Ubuntu, run chkdsk from windows and reboot to test windows before beginning the install.

---

