---
title: "Poor performance after automatic update"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by morganpatrick on 2015-02-28
Hi, I'm running 14.04 on 64 bit machine with an SSD. My machine has always run great until very recently, maybe the last few weeks. Now, wi-fi drops out constantly and windows frequently become unresponsive, where I can't click on anything in a window.

At first I thought this may be a hardware issue, but I noticed there was no problem when I booted from a live USB. So I reinstalled my OS, and everything worked great-- no dropping out.

But of course, when you install a fresh copy of Ubuntu, you're then prompted to run a lot of updates. And once I did this and restarted, my performance is poor again, with frequent dropouts.

So clearly there is some new package that doesn't agree with my system. However, I do'nt know how to go about pinpointing this. Before reinstalling I tried booting into old kernels, going back 1, 2 or 3 versions, but this didn't improve performance.

Any advice would be much appreciated. Thank you.

---

### Post by v3.xx on 2015-02-28
Is this the 3.13 kernel or the 3.16 ?

---

### Post by morganpatrick on 2015-02-28
Thanks so much for the reply. I ran dpkg --list | grep linux-image and got:

ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.76                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.76                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.46.53                                        amd64        Generic

So, the 3.13 kernel.

---

### Post by ian-weisser on 2015-02-28
> **morganpatrick said:**
> wi-fi drops out constantly and windows frequently become unresponsive

Those two might be symptoms of the same problem...or they might be two totally unrelated problems that have coincidentally popped up at the same time.

Has your internet connect been noticeably slower? Are any other systems on the same network also slower? Have you reset your router recently?
Has your system been physically moved to a different location in the room or building recently?
Is your fan running much more than normal? Does your system feel hotter than usual? Are the vents/fans unobstructed?
Does the system take much longer to boot? Or does the desktop take much longer to appear after login?
Does the hard drive run more than usual?
Open a terminal and run the 'top' command. Leave it open and running. When your desktop gets sluggish, what does 'top' report as the biggest resource consumers?

---

### Post by morganpatrick on 2015-02-28
To answer your questions: My internet connection has not been slower on any other devices; I have reset the router; My system has not been moved; I don't know if the fan has been running more (maybe?) but there don't appear to be any obstructions in around the vents; Neither booting nor the appearance of the desktop are slower than usual; Hard to say about the drive running more than usual, because it's an SSD; I have run htop and iotop simultaneously and haven't seen anything out of the ordinary when the internet gets slow, and haven't had the unresponsive window issues when they were running.

However, I think this is the most important piece of information: **When I reinstall the OS, everything runs fine; as soon as I run the software updater and reboot, everything is runnng poorly again.**

---

### Post by ian-weisser on 2015-03-01
It's important. But it's not enough.

Keep using 'top' until you get a snapshot of the system beginning to fail.

Does wireless behave properly under the older kernel?
If so, I would look through the Launchpad bug reports and see if anyone has filed a regression bug for your kernel and wireless hardware.
If the bug report exists, click 'affects me too' and subscribe to it. 
If unreported, start a fresh bug report for the issue.

---

