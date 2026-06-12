---
title: "Can't install any version of ubuntu on my laptop msi l735"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by solfalk on 2010-11-13
Hey,

I have a serious problem installing any version of ubuntu on my laptop. I have tried ubuntu 9.10, 10.04 and 10.10 and fedora 14. It always stops at the purple screen with the 4 dots in ubuntu 10.04 and 10.10. In Fedora it stops at the logo of Fedora. In ubuntu 9.10 it also stops at the logo.
I search for a long time on a lot of forums and tried even the options nomodeset, noapic, acpi=off

I also tried in the commandline:
[LIST]
[*]i915.modeset=1
[*]xforcevesa noapic noapci nosplash irqpoll
[/LIST]

And always i get another warning/error:
[LIST]
[*]Glib-Warning **: getpwuid_r(): failed due to unknown user id (0)
[*]Check battery state                            [ok] -> it stops after this line
[*]mmc0 unknown controller - you may experience problems
[/LIST]

I don't know what the problem is because a while ago it worked fine to install ubuntu on my laptop. But since i put in a new graphics card it won't work anymore.(old: nvidia Geforce Go 7600 (but broken), new: nvidia Geforce Go 7600)

My system:
AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 1,70 GHz
2,00 GB RAM
32-bit system
Nvidia Geforce Go 7600 256 MB


So please if someone can help me, help me because you would be a life-saver.

---

