---
title: "[SOLVED] New Install Freezes On Reboot"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by scott_s on 2008-09-14
I just got a new desktop and have been attempting to install Ubuntu 8.04 64-bit.  It's an HP machine, here's a quick rundown on the hardware:

Core 2 Quad Processor
NVIDIA GeForce 9300
Gigabit ethernet on system board (not sure what kind)

The LiveCD works fine, the installation goes smoothly, it boots up for the first time with no problems.  Then I updated all the software that was out of date, and after that, the majority of the time it seems to freeze on the boot (unfortunately, I didn't try rebooting without installing updates first).  I read a few threads, and tried acpi=off, and that seemed to fix the problem.  Recovery mode also worked without doing anything special with the boot options.  Then I switched to the proprietary NVIDIA drivers, and I was totally hosed: normal boot froze, recovery mode froze, and none of these boot options helped:
1) pci=nopci
2) acpi=off
3) acpi=noirq
4) pci=noacpi

When I deleted quiet and splash from the boot options, I usually froze on one of two messages:
sda: <4> Driver 'sd' needs updating - please use bus_type methods (default boot options, or with modifications 3 or 4)
or
etho0: RTL8166c/8111c at [memory address, it looks like], [mac address, it looks like] XID 3.4000c0 IRQ 507 (with modification 1)



The output of dmesg right after a successful LiveCD boot is attached (I had to gzip it to get past size limits), in case that is helpful.

Any ideas?  I'm kind of stuck on this one... Ubuntu's usually worked pretty easily for me, but this is my first foray into 64-bit territory.

---

### Post by Pumalite on 2008-09-14
Boot into Recovery Mode and use 'xfix'

---

### Post by scott_s on 2008-09-14
Thanks for the suggestion.  Based on some similar situations I read about in the forums (and which I now can't find again to cite the link... grr) I tried upgrading my kernel to 2.6.27.  This seems to have done the trick, in the sense that I can now boot/reboot without issues.  I'm still sorting through some graphics issues (the option to upgrade my drivers to the NVIDIA proprietary drivers seems to have gone away, so I'm not really sure what my 3d acceleration situation is at this point), but I'm definitely in a much better place than I was two hours ago.

---

