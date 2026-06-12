---
title: "problem with seymour display driver (radeon)"
date: 2017-01-03
forum: Installation &amp; Upgrades
---

### Post by jgw on 2017-01-03
I just upgraded my laptop from 14.04 TO 16.04 and now my display is all screwed up (colors, can't really read, etc)  I don't know how to fix this.  the colors are all wrong, very hard to read, etc.  I apologize for this one as I really can't read what I am writing.   The laptop display is a AMD Radeon HD 6470M with 1GB dedicated DDR3 video and the display size is 1600x900 (hd+).  After my upgrade the display was just fine and remained so after the reboot.  Then, for no reason I know it magically went bad.  The driver looks like it should be the right one but it produces a genuine mess.

Here is what I have:
greg@greg-HP-EliteBook-8560p:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:36 memory:c0000000-cfffffff memory:d4400000-d441ffff ioport:4000(size=256) memory:d4440000-d445ffff

If this driver is wrong I need to know howto install the right one.  If not then how to I control this one?

Thank you......................


I will mark this as done.  I left this machine on all night and when I took a look this morning everything was just fine and dandy.  I have no idea why as, when I left it last night, the screen was VERY colorful and absolutely unreadable.  I did find that this machine was compatible with the radeon driver.  Oh, I left it on as I have found that, in isolated cases, healing can occur (praise the lord, pass the ammunition and we will all be free)

---

