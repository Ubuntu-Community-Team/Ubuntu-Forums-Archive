---
title: "Install 12.04 from PCMCIA CD-Drive does not work"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by lububox on 2012-06-18
Hey everyone,

its my first post ):P ... so please don't be too hard with your answers.
I have a very old Sub-Notebook which I wanted to reactivate with Lubuntu. Its a Sony PCG-C1MHP (384MB RAM...thats already the max. possible). One year ago or so, I easily managed to install Xubuntu and I was not very satisfied with the performance and so it wasn't used by me anymore. Now I found Lubuntu and wanted to give it a try.
Problem is, I just have a PCMCIA CD-ROM Drive to boot from. The old BIOS does not support booting from USB. I could boot from network, but the  network jack is on the port replicator which I don't have anymore. Let me try to describe what happens.
The Lubuntu install disk boots and shows installation menu, where I can decide to live boot, or add kernel parameters etc. (so far so good). When I now select install it starts to load and shows the Lubuntu progress screen. After a long time it stops and shows initramfs prompt. In the boot.log it shows something like "unable to find a medium containing a live file system".
My assumption is, that after loading the kernel, which does not contain the appropriate PCMCIA support, my drive was kind of disconnected again and so setup was not able to read from the install disk anymore. My second assumption is, that time ago when I managed to install Xubuntu, the install disk had the right PCMPCIA kernel modules onboard. Am I right ... somehow? ;)
**What can I do, to manage to install Lubuntu on that machine?** I combed through the whole internet the last two days and didn't found a solution how I could fix this. A install .iso with another kernel would be the best I guess ...

Many thanks for your help

---

### Post by lububox on 2012-06-19
Has no one an idea? :-(
Maybe I will switch and try another distro, maybe I give Xubuntu another try and upgrade and slim it more down ...

---

