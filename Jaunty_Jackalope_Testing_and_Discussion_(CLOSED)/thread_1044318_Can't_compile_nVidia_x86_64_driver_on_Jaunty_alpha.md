---
title: "Can't compile nVidia x86_64 driver on Jaunty alpha"
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PTrenholme on 2009-01-19
I loaded the Jaunty 9.04 Alpha x86_64 a couple of days ago, and need to run the **NVIDIA-Linux-x86_64-173.14.12-pkg2.run** script to compile the **nvidia** video driver since my (built-in) **GeForce 7150M** is not supported by the **nv** driver in the repositories. (Note: The compilation works fine on released Ubuntu versions.)

However, when I try to run the script I get a message that it can't be compiled and that I should verify that I've got the correct libraries.

I *suspect* that this message is bogus since I also had to compile an Atheros driver module (the MadWifi 0.10.6 [_snapshot_]("http://snapshots.madwifi-project.org/") if you're interested) in order to get my wireless working, which compiled and loaded successfully.

Has anyone had or solved this problem?

---

### Post by patchin_house on 2009-01-19
You may want to take this news sitting down: Jaunty will reportedly be using X.org's new 1.6 server. Sadly, it means no support for proprietary nVidia drivers, and we'll have to use the open source variety instead.

Read on:
[http://www.theregister.co.uk/2009/01/19/jaunty_jackalope_alpha_3/](http://www.theregister.co.uk/2009/01/19/jaunty_jackalope_alpha_3/)

My Hewlett-Packard desktop uses a nVidia card, so upgrading to Jackalope could take a while (not to mention some cash for hardware upgrades, oy).

Philip David
(well past April for me, actually)
2009.01.19

---

### Post by PTrenholme on 2009-01-30
Well, I "solved" the problem by installing the build_essentials and upgrading to the newest kernel (**2.6.28-6-generic**). Then I removed the **nvidia-source** and built the **nvidia** driver from the **NVIDIA-Linux-x86_64-180.25-pkg2.run** package for version 180.25 (the latest release).

it may be worth noting that the **dkpg** build(s) all fail because, I believe, the **nVidia** kernel module is installed earlier in the boot, and the **nVidia** script finds a mismatch between the kernel version and the newly compiled version.

In any case, the **180.25** version seems to work with the pre-release 1.6 X server now in Jaunty. I'm posting this message from Jaunty using the **nvidia 180.25** driver and **X -version** shows this:```
X.Org X Server 1.5.99.901 (1.6.0 RC 1)
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux DV9700us 2.6.28-6-generic #16-Ubuntu SMP Mon Jan 26 20:15:49 UTC 2009 x86_64
Build Date: 23 January 2009  12:26:20PM
```

---

