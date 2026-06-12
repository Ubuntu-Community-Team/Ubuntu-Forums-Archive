---
title: "Dual-boot Win7 system -- epic 10.04 upgrade fail"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by ceenvee703 on 2010-06-02
I had a machine that dual-booted Windows 7 and Ubuntu 9.10.

This past weekend I thought I'd upgrade to 10.04. 

I obviously selected the utterly wrong set of selections when prompted during installation to pick partitions for GRUB2 to manage. I am sorry I can't say what I picked, but I can tell you the results:

* Ubuntu 10.04 boots fine

* Windows 7 just blinks with a flashing cursor in the upper left

* I do have my Win 7 install disc and used the "repair" option and the command line commands, but the repair disc does NOT see any valid Windows partitions... no C:, nothing. I can't run the various repair options I've seen online because there's nothing to run it on.

* I can see the Windows partition when booted under Ubuntu... all the data is still apparently there.

* I've seen various threads about restarting with the LiveCD and re-running GRUB2 but am not sure I've seen a definitive page on how to re-run GRUB2 and what to select once I've done so.

I would be happy to get both Win 7 and Ubuntu bootable, but barring that, I would like to get Win 7 back with everything intact. If the easiest path forward is to reformat and reinstall Win 7, that's less fine but doable -- I've backed up what I can via Ubuntu to an external drive.

Thanks.

---

### Post by darkod on 2010-06-02
Do this procedure on the partition where your win7 boot files are:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Note that if you have the small 100MB win7 boot partition, that's where your boot files are, not on the bigger system partition. In 99% of cases it works out fine, but there have been cases where it can't work. Lets hope you're not one of them. :)

---

### Post by ceenvee703 on 2010-06-02
Thanks for the reply. I installed testdisc and followed the directions. It did _something_ to my Win 7 partition... now instead of a flashing cursor I get two weird ASCII characters and a flashing cursor.

Tried running the Win 7 recovery disk again with same results: it doesn't see partitions to repair. I should mention that it is prompting me to load drivers when I try to do this. I guess I should see if I can put them on a CD or USB drive. 

At least I can still boot Ubuntu.

If you have any other suggestions please let me know. Again, thanks for the help.

---

### Post by ceenvee703 on 2010-06-02
Here is another symptom that may help.

Since Win 7 disk was claiming to need drivers, I thought I would check the Seagate site. There, I found an ISO for "SeaTools" to help you diagnose problems with Seagate drives:

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

Downloaded and burned the ISO with Brasero. Rebooted with it. 

SeaTools claims I have no hard drive in my computer.

---

