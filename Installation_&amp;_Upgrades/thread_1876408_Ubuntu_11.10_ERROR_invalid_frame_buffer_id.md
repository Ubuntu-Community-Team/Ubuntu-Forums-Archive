---
title: "Ubuntu 11.10 *ERROR* invalid frame buffer id"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by Kuraboy on 2011-11-06
Hi everyone,

I would like to share my problem and how I fixed it. But I also have a question. This is all too complicated for me.

Before installing 11.10 desktop amd-64 version I tried the live CD and Ubuntu seems to work nicely. 

After installation, when I boot I only get a dark screen and nothing else happens. I reboot in recovery mode and booted in single mode and looked at /var/log/syslog, there I found some error messages talking about invalid frame buffer.


I ran apt-get update then apt-get upgrade, it downloaded some stuff but problem still persisted.

 Then I found this link: [https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

I followed it and installed daily kernel version linux-image-3.1.0-999-generic_3.1.0-999.201111030405

And it seems to have fixed my problem and I can boot into desktop.


MY QUESTION: if I keep running this kernel version how will future updates from Ubuntu effect me? will I still get kernel updates? can it install backward kernel version? Will I get update for the rest of the programs and security issues?

thank you for any clarifications! 

br

---

