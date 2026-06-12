---
title: "No support for CMD649 after install"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Rhialto on 2005-11-03
Hello all,
 
i have recently installed Kubuntu Breezy on about every system i have; On my server, i encounter some problems though. My server has two ide controllers, the SvrWrks OSB4 and the CMD649. Both are supported as modules by Kubuntu and install detects them perfectly. However, when the base system is installed and the system reboots, the reboot crashes when trying to load modules with the message that it cant find /dev/hda and as such, cant find the modules. Seems logical since /dev/hda resides on the CMD649 which is not built in the kernel by default. I solved this for now by using another box for compiling a custom kernel which has support for my chipsets and now the system boots fine.

However, i'm now wondering how i should have solved this if i didnt have a second system nearby... is there a way to preload the modules (like FreeBSD does) or can i build a custom kernel during install? How should i have solved this problem?

Thanks in advance for any suggestions,
Chris

---

