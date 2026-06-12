---
title: "Black Screen on Wake up and from Idle"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by mnouh on 2011-05-09
OS: Natty 11.04
This was never a problem in 10.10

Laptop: Lenovo T410 running 4gb ram. The Discrete graphic card is a Nvidea Optimus 300M but I have the discrete settings turned off, and I'm using the intel integrated chip.

Screen will go black and just have the cursor active. (I can move the mouse around on a black screen). This happens after I suspend the system and wake up, and it also happens after the CPU comes back from IDLE(When I move the mouse to wake up the laptop). The only way is to manually press the power button and reboot.

CPU Specs

Processor I'm Running:

cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
stepping    : 5
cpu MHz        : 1199.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2


%lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)

---

### Post by ivanovnegro on 2011-05-09
Hm, I had something similar under Kubuntu 11.04, but I dont use the suspend mode.
But maybe disable the suspend mode on your machine.

---

### Post by mnouh on 2011-05-09
hmm, yeah suspend mode is at the moment needed for me. I travel alot and I need the quick resume. Travel "moving alot every couple 30 minutes" To shut it down every time I switch from building to building, is definitely not ideal :)

---

### Post by ivanovnegro on 2011-05-09
I can understand you but some machines just dont work good enough on Linux with the suspend mode, its only a workaround to disable the feature.

---

### Post by spacon08 on 2011-05-17
I've experienced the same problem when idle. Has a solution/ reason been found for this?

---

### Post by Dreadnaxt on 2011-06-19
Same for me. Never happened from 8.04 to 10.10. Now on wake up after suspend the screen is black and only a mouse cursor visible. If trying to enter password it seems to log in to system, but the screen is still black. Sometimes another bug with spontaneous logout helps to get back to select user screen. In this case graphics becomes visible. I'm slightly beginning to hate 11.04!

---

### Post by Marysart on 2011-06-22
Having the same problem in Kubuntu Natty. Is this a known bug?

Ok, did google search. It appears to be a known bug and has to do with intel motherboard p67/H67

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842)

[https://bbs.archlinux.org/viewtopic.php?pid=924218](https://bbs.archlinux.org/viewtopic.php?pid=924218)

Don't have a solution though. I'm in waaay over my head. Bought a new computer with what appears to be the "wrong" motherboard/cpu for linux.

---

### Post by unclepedro on 2011-07-02
Looks like these kind of issues are related to the new SandyBridge GPU. People are working hard on it and fixes should be coming down the pike reasonably soon. I'll post back here once I figure things out.

---

### Post by anacaona on 2011-07-27
Hey friends,

I'm having the same problem, apparently the workaround is to disable suspend as per this [bug report]("https://answers.launchpad.net/ubuntu/+question/163670"), which is really bad in my case because I live in a place where power is a major issue and every little bit counts.

If I hear of better solutions I'll be sure to share them here.

---

### Post by wissamshaar on 2011-08-31
> **mnouh said:**
> OS: Natty 11.04
This was never a problem in 10.10

Laptop: Lenovo T410 running 4gb ram. The Discrete graphic card is a Nvidea Optimus 300M but I have the discrete settings turned off, and I'm using the intel integrated chip.

Screen will go black and just have the cursor active. (I can move the mouse around on a black screen). This happens after I suspend the system and wake up, and it also happens after the CPU comes back from IDLE(When I move the mouse to wake up the laptop). The only way is to manually press the power button and reboot.

CPU Specs

Processor I'm Running:

cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
stepping    : 5
cpu MHz        : 1199.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2


%lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)


Updating the Kernel solved the problem on my Toshiba Satellite U405

---

