---
title: "System boots to another virtual terminal instead of 7."
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by far_star on 2009-09-24
Running x86_64 with Nvidia proprietary drivers.

My system boots to a blank screen. Hitting enter brings me to a text based login prompt. I switch to virtual-terminal 7 with Ctrl-Alt + F7 and only then does gdm start and present a login screen. 

Anyone else having this behaviour before I post a bug ? Thanks.

---

### Post by eluminx on 2009-09-25
Yes im on the same boat as you are.

---

### Post by alexmurray on 2009-09-25
Yep I can confirm this one too - NVIDIA 9600M GT with Ubuntu packaged NVIDIA drivers installed.

---

### Post by moviemaniac on 2009-09-25
It's been that way for two days now ;)

---

### Post by Sophont on 2009-09-25
After yesterdays updates I had temporary problems booting (but worked fine later) and noticed that it's on F8 instead of F7 now.

---

### Post by martinpm24 on 2009-09-25
i have the same issue

---

### Post by Sophont on 2009-09-25
Not sure it's an "issue".

Don't really care if it's on F7 or F8. :-)

---

### Post by Technoviking on 2009-09-25
Filed bug.

[https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/436680](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/436680)

---

### Post by Technoviking on 2009-09-25
Reinstalling the kernel packages fixes this problem.

T-V

---

### Post by alvevind on 2009-09-25
Same problem here.

Tried reinstalling kernel, still same problem.

Tried disabling proprietary nVidia driver, still same problem.

---

### Post by nhasian on 2009-09-25
yes i'm experiencing the same problem.  I marked "affects me too" on the launchpad bug report.  between the symlink errors and dropping to a terminal prompt on bootup, I've been afraid to reboot.  Its doing wonders for my uptime though :)

---

### Post by Aries K on 2009-09-25
Anyone know which update causes this issue? Has an official release been released into the updates yet?

---

### Post by alexmurray on 2009-09-26
This has been fixed for me with the latest updates.

---

### Post by taavikko on 2009-09-26
> **Technoviking said:**
> Reinstalling the kernel packages fixes this problem.

T-V

Reinstallation didn't fix the problem, but thanks for the report though.
It also affects KDM.

My laptop running radeon isn't affected so it seems it's only affecting Nvidia users.

---

### Post by moviemaniac on 2009-09-26
> **alexmurray said:**
> This has been fixed for me with the latest updates.
The kernel update should have done the trick.

> **taavikko said:**
> My laptop running radeon isn't affected so it seems it's only affecting Nvidia users.
I'm also running a radeon card (fglrx) and I was affected by the bug.

---

### Post by far_star on 2009-09-26
I have updated this morning and the bug has not been fixed.

---

### Post by todak on 2009-09-26
I am also affected by this bug. I am using 32-bit karmic with latest updates. In the meantime, when I am presented with the blank screen **Ctrl+Alt+F7** continues the process into GDM.

---

### Post by jfernyhough on 2009-09-26
You can increase the efficiency of the workaround by 33% by pressing only ALT-F7. Not that this helps an awful lot. :D

---

### Post by alexmurray on 2009-09-26
Damn, I just restarted and this is back - plus initially my machine didn't successfully boot at all (got to where xsplash would start and didn't go any further), then it booted but I had to do CTRL-ALT-F7 just to get x to come up.

Also, sometimes I see usplash and sometimes I don't...

Something is definitely a bit screwy...

---

### Post by ktp on 2009-09-26
> **jfernyhough said:**
> You can increase the efficiency of the workaround by 33% by pressing only ALT-F7. Not that this helps an awful lot. :D

I saw the same issue using todays daily live cd.  Alt+f7 did the trick for me too...but was really funny to see blank screen for while.  I thought it was still booting since there is no progress bar for boot process now.

---

### Post by PsychedelicReaction on 2009-09-27
same problem here (Dell xps1330m with nvidia 8600). Had no luck reinstalling kernel packages.

---

### Post by dino99 on 2009-09-27
i think that i'll remove SUM

---

### Post by moviemaniac on 2009-09-27
Weird. My system got updated to the latest kernel (-11) which still shows this bug. Today I booted into the old 2.6.31-10 kernel to double-check something and not only did the system start faster but it booted right into gdm. :lolflag:

---

### Post by nhasian on 2009-09-27
my laptop with the source set to Main Server, the linux kernel is held back for some reason, but my brother's laptop set to United States Server and he's got the latest kernel (2.26.31-11) update.  I guess I'll keep waiting...

> **moviemaniac said:**
> Weird. My system got updated to the latest kernel (-11) which still shows this bug. Today I booted into the old 2.6.31-10 kernel to double-check something and not only did the system start faster but it booted right into gdm. :lolflag:

---

