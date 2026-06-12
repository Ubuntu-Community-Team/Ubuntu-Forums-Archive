---
title: "Missing desktop"
date: 2019-01-30
forum: Installation &amp; Upgrades
---

### Post by dfpd62 on 2019-01-30
Just upgraded from 16.04 to 18.04 and have a major screen issue.

The machine boots OK to a blank purple screen, but if I press enter and type my password Gnome boots my normal desktop wallpaper and screen resolution.

The problem is that nothing else works, there are no screen icons, no sidebar, no info bar at the top of the screen.

the only thing that works is right clicking on the desktop and choosing "Open Terminal" I can troubleshoot from there but the only program i've been able to run from there is Firefox (tried chromium, terminal says its running but nothing appears on screen but a Youtube video can be heard playing through the headphones).

At Reboot if I choose "Rescue" and start with "failsafe graphics" all works as it should, the screen icons, sidebar and activities bar work properly but with VGA resolution 1024x768.

This is what I've found out so far.

Code:

dd@dd-desktop:~$ sudo lshw -C video
 
  *-display                 
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:37 memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:c0000-dffff


Code:

dd@dd-desktop:~$ lsmod |grep radeon
radeon               1470464  20
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
drm_kms_helper        172032  1 radeon
drm                   401408  16 drm_kms_helper,radeon,ttm
dd@dd-desktop:~$ grep -r radeon /etc/modprobe.d
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb

I think this shows that the correct driver is loaded and running
Therefore I think the issue must be with Gnome.
Anyone else had anything like this?

Cheers D.

---

