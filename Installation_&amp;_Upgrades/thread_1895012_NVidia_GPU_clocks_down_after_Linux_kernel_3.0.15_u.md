---
title: "NVidia GPU clocks down after Linux kernel 3.0.15 update?"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by uga_boy on 2011-12-13
Hey guys, I noticed this directly after grabbing the latest 'proposed' updates (i know, i know) which include a new complete kernel version. After rebooting and going through the recovery boot because I have a fake raid and also to install the NVidia driver script (290.# i believe) I was able to get the release kernel to boot but it is VERY choppy. Can't play videos, . anything flash or openGL related is just unbearable. Looking at system monitor, everything looks normal, nothing out of the ordinary but if I go to the NVidia x-server settings app it shows my GPU sitting at half max-frequency on the processor, clock and memory. Usually I can toggle a setting to go from 'Adaptive performance', to 'Max performance' but it doesn't change. Stays at level 2 out of 3. I've tried booting with the previous kernel... no luck. Same issue.

Now the really weird thing, I have a dual boot environment with Windows 7. After the Linux updates and the poor performance being experienced, I booted into Windows. I have a i7 and Windows shows all the cores. but 4 of the 8 are 'parked' according to the resource monitor. They barely, if ever, kick in. So basically running on the primary core, no hyper threading is occurring. 

whew... after all that, my question is. Can a kernel (there were more updates than just the kernel mind you) update set something at a hardware level that could make me experience problems in both environments? Things were great across the board and the only significant event that occurred before these symptoms was the update manager updates. It's as if a power profile or something has been set to force the system into half power mode. I've checked all of the power management settings and all are set to max performance. Any help would be greatly appreciated. Thanks!

---

### Post by Viman on 2011-12-14
Hey, I'm sorry for the off-topic, but I've got a question:
How did you manage to upgrade the kernel to 3.0.15?
Everytime I run `apt-get update && apt-get upgrade` only the program binaries get upgraded, never the kernel.
Is there a special command to upgrade the kernel specifically?

---

