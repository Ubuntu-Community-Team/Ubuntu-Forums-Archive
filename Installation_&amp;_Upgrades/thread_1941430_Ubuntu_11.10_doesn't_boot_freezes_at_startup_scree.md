---
title: "Ubuntu 11.10 doesn't boot: freezes at startup screen"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by neshua on 2012-03-15
Hi guys. 
I am aware that this problem is very common, but after hours of research I was not able to solve it, so I open a new thread.

I installed Ubuntu 11.10 on my new HP 8560w (graphics: Radeon FirePro M5950) using a ubuntu image on USB stick (not wubi). However, when I try to boot ubuntu, it freezes at the purple screen.

I read about this problem in the internet and I tried several of the proposed solutions. The common solution seems to be replacing "quiet splash vt.handsoff=7" in the GRUB menu before booting. I tried many replacements, among them:

- delete "quiet splash": still same problem (freezes at purple screen).

- replace "quiet splash" by "nomodeset": It starts some processes, most of them with status [OK]. The only process with status [fail] is "Starting load fallback graphics devices". After that, some more are started, ending with "Stopping Userspace bootsplash" with status [OK]. Then nothing happens.

- replace "quiet splash vt.handoff=7" by "nomodeset": It doesn't boot to full ubuntu, but just to a terminal where I can enter "login" and "password" and it says "Welcome to Ubuntu", giving me a terminal to use. 

- replace "quiet splash vt.handoff=7" by "acpi=off radeon.modeset=0": same thing. 

I tried similar commands when booting ubuntu from USB stick (without installing the OS). The errors are the same essentially. 

What else can I try? The last two options above seem promising. At least I get a working terminal... Do I have to install proprietary graphics drivers from there? If yes, how?

Thanks a lot!

---

