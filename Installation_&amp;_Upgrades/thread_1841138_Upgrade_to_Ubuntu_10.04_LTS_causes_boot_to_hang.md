---
title: "Upgrade to Ubuntu 10.04 LTS causes boot to hang"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by mmino on 2011-09-08
After upgrading from Ubuntu 9.10 to Ubuntu 10.04 LTS Ubuntu won't run. The boot process starts and hangs right after the splash page. When the screen is frozen the monitor screen displays the Ubuntu name with the 5 dots below it.

I can boot successfully using a CD so I don't think it is a compatibility issue with my hardware.

Any ideas on what to do next will be greatly appreciated.

Best regards
Michel

---

### Post by BlacqWolf on 2011-09-09
Start your computer. When your computer leaves the BIOS, hold 'shift' to enter the grub menu. Then select Ubuntu Recovery Mode, and select "Run in a failsafe graphics mode." Then, on the menu that appears, afterwards, select "Run in failsafe graphics just for one session." I honestly don't know what it is that this does to the files saved on the hard disk, or under what circumstances it helps, but in many cases it resolves booting issues (for me, at least).

If this doesn't work, you may want to connect your computer to the Internet through an ethernet cable, then enter recovery mode, this time selecting "repair broken packages."

---

### Post by mmino on 2011-09-12
Thank you so much :)

Problem solved.....yessss

---

