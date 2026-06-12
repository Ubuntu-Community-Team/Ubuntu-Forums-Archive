---
title: "I messed up my video/update"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by boz86 on 2013-11-18
I upgraded to 12.04, thought I had the wrong video driver, so installed another. Now I can't get Ubuntu up in graphic mode.

If I run "startx" at the terminal I get some messages:

Using system config directory "/usr/share/x11/xorg.conf.d"
NVIDIA: API mismatch: the NVIDIA kernel module has version 304.88, but this NVIDIA driver component has version 319.32. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Fatal server error: no screens found

Server terminated with error (1). Closing Log file.
xinit: giving up
xinit: unable to connect to X server: no such file or directory
xinit: server error


I tried burning an ISO DVD with 13.10 and running it, but it wants to install in a new partition rather than update LTS 12.04.

Any help appreciated.

---

### Post by papibe on 2013-11-18
Hi boz86.

If you installed the driver either using apt-get, the software center, or using the 'Additional Drivers', take a look at this post [here]("http://ubuntuforums.org/showthread.php?t=2169638&p=12765972#post12765972").

In case you installed the Nvidia driver from the Nvidia site, you need to use the same script you used to installed it, but with the option --uninstall to actually uninstall it. Check [here]("https://help.ubuntu.com/community/NvidiaManual") for details (check the section Uninstall Driver).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by boz86 on 2013-11-18
Thanks Papibe

Working through the instructions, what does it mean 

[LIST]
[*]Remove all packages separately except for these two: 	Code:
 	nvidia-cg-toolkit
nvidia-common 

[*]
[/LIST]

---

### Post by boz86 on 2013-11-18
> **papibe said:**
> Hi boz86.

If you installed the driver either using apt-get, the software center, or using the 'Additional Drivers', take a look at this post [here]("http://ubuntuforums.org/showthread.php?t=2169638&p=12765972#post12765972").
.
Got as far as the nvidia purge command in your link and that solved it.
thanks.

On to restoring the wireless network....

---

