---
title: "Crash during installation and after"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by thinker-tinker on 2011-02-11
Hello, 

I have spend the last couple of nights chasing and isolating a problem but so far couldn't fix it. Hopefully someone can help.  The problem originally occurred when trying to install ubuntu (lucid 10.04.1 amd64) on my desktop pc (msi p35 neo2 with marvell 88SE6111 controller and intel quad-core cpu with a samsung sata drive and 2 samsung ide drives; master cdrw, slave dvd). 


The installation from cd would consistently hang after keyboard selection (as I have learned, this is when hardware is detected). The same also happend with the alternate install cd as well as each and every other ubuntu-derived distro I have tried (from 9.10 up to 10.10), including debian squeeze x64.   However, I could boot and run a live easypeasy from cd (but not install it either for the same reason). First I tried to tinker with every single bios option (from all-disabled to all-enabled) but no luck here.

Next, I tried bios update (from 1.5 with marvell bios L61 to 1.C with marvell bios L69) with the only effect being a slower boot because marvell now takes a good long look around before moving on. After that, I played with the master/slave settings of my ide-drives and plugged sata drives in different places (ich9 ports and the one marvell sata port). Still no luck (and no sleep). Switching sata between ide and ahci made no difference to linux, but on ahci windows xp64 would no longer run. Same for APIC table format (linux doesn't care, windows insists on 1.1).


I had also suspected my built-in multi-usb-reader since some posts said sd cards had caused trouble in the same spot, but deactivating usb only killed my mouse and not the problem ;-)  Finally it turned out that switching off IDE in the bios would get me over the critical point while killing my cd drives, so I did an install from a sd card and thought I was safe now.


However, when turning ide back on in the bios, the freshly installed ubuntu consistently crashes a few seconds after login (gdm doesn't seem to have a problem, it seems the crash happens when gnome tries to access the cd for the "places" menu). Running update manager (with ide disabled) didnt't help. Neither did all kinds of &quot;ide generic&quot; kernel parameters, loading pata_marvell before ahci or passing marvell_enable=1/0 to it.  Now I've run out of ideas (and so has google).


I can work long and happy, if I turn off IDE, but that leaves me without my disc drives. Sure, I could go buy SATA ones, but so far I still hope someone can point me to a software solution (kernel module, kernel parameter or patch). In the meantime, I'll be compiling a new kernel with pata_marvell and generic ide built in.  Since this whole report has been rather prose, I'll be happy to add any details / logs etc. the experts require. Unfortunately, /var/log/messages didn't give any indication of the crash reason (or I didn't see it).

Regards 
-- Andreas

---

### Post by thinker-tinker on 2011-02-11
Find enclosed some information I took off the live-easypeasy and my ubuntu installation (with ide off!) as well as my /etc/modules. Kernel parameters in /etc/default/grub are:

GRUB_CMDLINE_LINUX="generic.all_generic_ide=1 all_generic_ide ide-pci-generic.all-generic-ide"

---

### Post by thinker-tinker on 2011-02-11
# /etc/modules
lp
rtc
# next two lines added to try and fix marvell problem
# See also:
# [http://fixunix.com/debian/542307-bug-493657-workaround-2-6-25-2-6-26-marvell-88se6121-88se6145-pata_marvell-ahci-regression.html](http://fixunix.com/debian/542307-bug-493657-workaround-2-6-25-2-6-26-marvell-88se6121-88se6145-pata_marvell-ahci-regression.html)
# [http://www.gossamer-threads.com/lists/linux/kernel/968813](http://www.gossamer-threads.com/lists/linux/kernel/968813)
# [http://www.linuxquestions.org/questions/linux-general-1/module-load-order.-648599/](http://www.linuxquestions.org/questions/linux-general-1/module-load-order.-648599/)
# [http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#MSI_motherboards_that_use_Marvell_88SE6111_chipset](http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#MSI_motherboards_that_use_Marvell_88SE6111_chipset) (PATA/IDE section)
pata_marvell
ahci
options ahci marvell_enable=1

---

### Post by thinker-tinker on 2011-02-11
Had to .tgz the logs because they were to big for the forum

---

### Post by thinker-tinker on 2011-02-12
Thinking about it, it seems interesting that both easy peasy and ubuntu desktop can boot a live system from the cd but are unable to use it during installation or after. There must be different kernel modules and parameters involved...

---

