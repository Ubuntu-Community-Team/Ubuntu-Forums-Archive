---
title: "Unable to boot Ubuntu after two reboots"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by gjwolfswinkel on 2008-04-14
I have installed Ubuntu 7.10 and 8.04 on my Acer 7720 laptop. In both cases, I installed the OS successfully, and was able to reboot after install. Then, after installing the latest updates, you have to reboot again; this is where it goes wrong. The OS won't boot anymore; it begins, but hangs somewhere, and the screen goes black. Starting in recovery mode will complete successfully to the menu that allows for x window recovery, drop to console or resume normal boot. 

If you go to resume normal boot, the system will start displaying errors like these:

ata4.00: status: { DRDY }
ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x2 frozen
..followed two lines below that with a Emask 0x4 (timeout) timeout. 

This sequence gets repeated a lot, then the screen goes black here too. 

I have identified ata4.00 as my Optiarc dvd drive. 

I have installed 7.10 and upgraded online to 8.04. I tried with acpi=off and generic_ide_all in the menu.lst, both to no avail. 

This is getting frustrating, to be honest - I've been getting this to work for four days :-/ Any help would be appreciated.

---

### Post by jbulcher on 2008-04-14
Have you tried booting without your optical drive?

---

### Post by gjwolfswinkel on 2008-04-18
I finally got this sorted out by setting generic_all_ide in the boot options, and restoring a previous version of xorg.conf.

I sure hope the definitive 8.04 version will solve this bug.

---

### Post by gjwolfswinkel on 2008-04-23
In the end, my xorg-config and ATI driver stuff was becoming such a mess that I had to reset it completely. I wiped my xorg-conf, leaving only an empty file in it's place; then I rebooted. That reset everything to 'generic' and 'vega'. After that I downloaded the most recent driver from AMD, and installed that one. Finally, a working 1400x900 screen :-)

---

### Post by makhand on 2008-04-27
I sure hope they fixed this problem in the official release or that they fix it "quietly" in their iso downloads or something. It has cost me lots of time. I"ll try your suggestions/feedback.

nope, cant even reinstall. this is lame.

---

