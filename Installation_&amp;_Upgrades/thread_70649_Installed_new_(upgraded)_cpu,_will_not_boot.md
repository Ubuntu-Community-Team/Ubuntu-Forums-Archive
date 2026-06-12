---
title: "Installed new (upgraded) cpu, will not boot"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by CyberBob on 2005-09-30
After troubleshooting and solving an installation issue with Hoarty, I've chosen to upgrade the cpu (from a Cyrix MII 300 to a K6 2 500, same M571 motherboard).  Please see my prior thread for the gory details:

[http://www.ubuntuforums.org/showthread.php?t=68348](http://www.ubuntuforums.org/showthread.php?t=68348)

It was running fine business with the Cyrix cpu - all I did today was change the jumpers on the main board to adjust the core cpu voltage to accomodate the K6, swapped the cpus, and hit the ON switch.

After getting the K6 cpu installed, I fire up the box and the following appears when booting:

Uncompressing Linux ... OK, booting the kernel.
ACPI: Unable to locate RSDP
audit(1128116766.920:0): Initialized
/bin/sh/: error while loading shared libraries ... and so on.
Kernel panic - not syncing: UFS: Unable to mount root fs on unknown-block(0,0)

My question is this: must I re-install Hoarty all over again or is there a way to fix this by running a live-CD of Hoarty?

I have confirmed that I can run the live CD of Hoarty without problems - but I'm not sure if I can then access the filesystem already on hda.  If so, I need help in learning what I need to do (e.g. compile a new kernel or whatever) to make this box behave on startup with the new cpu.

---

### Post by CyberBob on 2005-10-01
Well,

I decided to do a complete re-install.  Took me another hour of watching blue and red, but everything now works fine.

I bet there is an easier way to have fixed this, but it probably would have taken me way more than an hour to figure it out.  Sometimes brute force is the most expedient path to take ...  ;-)

---

