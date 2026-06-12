---
title: "Ubuntu and windows won't boot!"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by pwert00 on 2013-04-14
Hi all,


I recently ran into problems with my HP Pavilion g6-2235us laptop and it is now unable to boot.  I was wondering if I could receive help from the wonderful people of this forum.  


I originally had windows 8 installed on my computer and I installed Ubuntu 12.10 64bit alongside it.  This configuration worked fine for 6 months until two weeks ago when I started running into problems.  My computer became unable to boot from grub into ubuntu12.10 so I reinstalled ubuntu12.10.  My system kept working after the reinstall for almost two weeks with a few glitches in the system (ubuntu would not wake up from sleep and I would have to hard restart every time, Ubuntu would occasionally be unable to boot) when I tried updating the bios to accompany my new RAM, to use boot-repair, and to repair broken packages in recovery mode. My computer froze in the middle of repairing packages in recovery mode and I had to hard restart, causing my system to again be unable to boot.  So I reinstalled Ubuntu again today (wiping my Ubuntu partition) and I have run into the same recurring problem: my freshly installed Ubuntu partition will not boot.  It would boot when freshly installed (without getting updates) but once I got into the system for the first time and installed  video drivers for my radeon driver and updated my system, Ubuntu again would not boot.  


Even worse though, grub is the first thing that pops up on my screen when I first turn on the PC.  The computer used to boot first into windows and I would have to interrupt it with esc to pull up grub, but not anymore.  I don't know why but after my fresh install grub is the first thing that pops up and it is unable to boot into my windows partition.  So now I am stuck with a brick - Ubuntu won't boot and grub won't boot into windows.  


Any help?


Thanks.


When I say it won't boot, I mean it freezes up during the booting process.  It usually freezes right after the text "starting configure virtual network devices".

EDIT: boot-repair gave out the following link: [http://paste.ubuntu.com/5709021/](http://paste.ubuntu.com/5709021/)

---

### Post by Mark Phelps on 2013-04-15
You don't actually NEED to install Radeon drivers, the installer does that for you automatically.  The default open-source drivers are pretty good so unless you need hardware acceleration for 3D gaming, they will work just fine.

As for booting, sorry, your PC has UEFI -- and I have no experience repairing boot with those devices.

---

### Post by oldfred on 2013-04-15
UEFI/BIOS update resets everything to defaults. After losing a lot of settings with my system (BIOS only) I used camera and made screenshots of every screen so I could easily reset to my preferred settings.

Some systems only boot with secure boot on. Or you may need secure boot off.

If you get grub menu, then you have booted and it is either UEFI parameter conflicting with kernel or kernel needs extra boot parameters.
Did you reinstall with 12.04.2 or 12.10 (same as 12.04.2) as that is a new kernel and grub version over 12.04. And you have to install kernel headers to get proprietary drivers to install correctly.

---

