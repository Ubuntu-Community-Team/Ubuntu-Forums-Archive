---
title: "Graphics problems after upgrading HWE Stack"
date: 2016-09-01
forum: Installation &amp; Upgrades
---

### Post by bjorn-lisper on 2016-09-01
I run Xubuntu 14.04 LTS on a HP EliteBook 840 G1. The update manager  recently began prompting me for upgrading the HWE Stack, and so I did.  Now I run the Ubuntu 16.04 Xenial HWE Stack and the kernel has been  upgraded to 4.4.0-36-generic.

 After the upgrade I experience some annoying problems:

 1. Sometimes the screen goes blank, like if the screen-saver kicks in  but randomly, it may take 30 seconds or an hour between these  events and regardless of if I do any activity or not. I will get the  screen back, but  sometimes with some delay (from immediate to a few seconds).

 2. If I close the lid so the computer hibernates, and when waking it  up again, then, after login, the cursor will disappear from the screen.  It is somehow still logically there, because I can see items being  highlighted as as move the mouse, but the arrow is invisible. A reboot  will fix it.

Is there anoyone out there experiencing the same problem? I presume this should be an issue for 16.04 systems as well. Any fix?

Björn

PS. the "lshw -C display" yields the following:

  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)

---

### Post by ubfan1 on 2016-09-01
There are several X related packages in the hardware stack update besides the kernel.  Did you upgrade these too?  I successfully run a 4.6 kernel on 14.04, not from the official packages, and all it needed in addition was the firmware package, so the X is not always necessary it seems.

---

### Post by bjorn-lisper on 2016-09-01
To be honest I don't know. I first did the HWE Stack upgrade using the update manager, then the manager immediately prompted me for another upgrade including the new kernel + (I think) some other system-related stuff which was not so well specified - the manager don't give details unless you specifically ask for them. So I simply made the upgrades suggested by the manager without altering anything.

---

### Post by bjorn-lisper on 2016-09-01
I should add some more observations regarding the problem with the screen going blank. Today it happened two or three times, so it's not terribly frequent. Every time it seemed to be triggered by some event, like a mouse click or move. The screen would go blank for a couple of seconds, then back to normal. So far the system has never frozen, or crashed.

---

### Post by bjorn-lisper on 2016-09-15
Another note. The problem with the cursor disappearing after waking up from suspend turned out to be a known one, and there are workarounds (simplest seems to be to hit crtl-alt-F1 then ctrl-alt-F7, works for me). But nobody else seems to have reported problems with the screen going blank so possibly those issues are unrelated.

---

