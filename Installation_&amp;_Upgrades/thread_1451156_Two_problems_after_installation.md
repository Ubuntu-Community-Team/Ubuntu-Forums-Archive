---
title: "Two problems after installation"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by ReeRD on 2010-04-10
Hello,

I'm trying to migrate to Ubuntu 9.10 x86, however, I have a couple of problems.

My hardware: ASUS F5RL laptop with an ATI 1100 Xpress GPU.

1. After several clean installs I've noticed that Ubuntu usually hangs during the FIRST boot after the installation. I see the message "GRUB loading", then I see the white Ubuntu logo, then the screen flickers and stays black. After a hard reboot, I'm presented with the GRUB menu and after selecting the default kernel Ubuntu is loaded without any problems. Subsequent reboots work fine, too. So the problem is the initial boot. What is the cause of it? I suspect it to be related to video initialization (I may be wrong). There was a case when Ubuntu did NOT hang upon the first boot (but that happened only once out of maybe 5 times).

2. Once I noticed some error displayed during the boot process which disappeared quickly and didn't seem to have any negative effect (the OS loaded fine). It was displayed below the white Ubuntu logo and had references to fstab and something being "not ready" (I think). Is this something I should be worried about?

---

### Post by oldfred on 2010-04-10
To narrow down the issue, look in the log file viewer. It has too much info but look for errors or warning messages.

System, Administration, log file viewer.
I think primarily dmesg, & kern.log but look at them all as you can see the history of lots of things going on in your system.

---

### Post by ReeRD on 2010-04-12
Actually, the logs don't tell anything useful. However, I reinstalled once more and got a kernel oops on first boot (sound related). Reinstalled again and now it's all fine.

Ubuntu may be fine as an OS, but it surely still needs polishing so it doesn't break during the most basic operations. IMO, installation system is completely broken in a very random kind of way.

---

