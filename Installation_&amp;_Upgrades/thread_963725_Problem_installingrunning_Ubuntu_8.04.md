---
title: "Problem installing/running Ubuntu 8.04"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Microaide on 2008-10-30
I am having problems installing and running Ubuntu 8.04 on an industrial touchscreen computer. I have tried booting directly from the CD in live CD mode. I get as far as the screen with an orange progress bar, which reaches about 80%. Then the computer just locks up (I have waited over 10 minutes, and there is no CD read activity).

I tried installing inside Windows (Wubi install) and kept getting a fatal error (application terminated, do I want to send a report to Microsoft) just after all files were copied from the CD to the hard drive.

Then I decided to try the Wubi install after booting Windows XP into safe mode. The install completed successfully. But when I try to boot into Ubuntu, I get stuck at the same screen as the live CD mode, with progress bar at about 80%.

I have used the same CD to run Ubuntu on my Windows XP laptop with no problems (both live CD and Wubi install), so I know the CD is good. Both the laptop (IBM Thinkpad T20) and the touchscreen computer are running Windows XP SP2. The touchscreen computer has a Pentium 4 2.8GHz CPU, 1G RAM, 80G drive, Intel 82845G/GL/GE/PE/GV Graphics controller, and an Elo Serial Touchscreen Interface.

Could it be the Elo touchscreen interface that is causing problems? If so, how can I get Ubuntu running without the touchscreen driver (I can use an external mouse)?

I am currently downloading Ubuntu 8.10, and will try it in a few hours.

---

### Post by Microaide on 2008-10-30
Tried Ubuntu 8.10, still no-go. Gets past the progress bar screen, eventually tells me "Ubuntu is running in low-graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

I select "run in low-graphics mode for just this session", it tells me to stand by for one minute, I click OK, and eventually hang at a text screen where the last line is as follows:

* Checking battery state...   [ OK ]

I tried everything I could think of, including setting low graphics mode as an option on the boot menu. When I do that it eventually hangs at a black screen. Any suggestions would be greatly appreciated.

---

