---
title: "Errors during bootup, please help"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by eBast on 2005-01-30
Got Ubuntu working after loading nVidia drivers, now the bootup process shows some error messages, eventhough the machine is booting properly..

the messages are :

modprobe: FATAL: Error insreting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drive rs/pci/hotplug/shpchp.ko) Operation not permitted

modprobe: FATAL: Error insreting pcichp (/lib/modules/2.6.8.1-3-386/kernel/drive rs/pci/hotplug/pcichp.ko) Operation not permitted

Please go through these and advice me..... :-?

---

### Post by Frihet on 2005-01-30
I am very new to this distro.  I ignored the same two errors and everything installed correctly.  Are you using a laptop?

---

### Post by eBast on 2005-01-30
[QUOTE=Frihet]I am very new to this distro.  I ignored the same two errors and everything installed correctly.  Are you using a laptop?[/QUOTE]

No its a desktop.  But I really would like to know what those errors are for....

Athlon XP 2000+
Asus a7n 266 vm
512 mb ram

---

### Post by WW on 2005-01-30
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
[http://www.ubuntuguide.org/#modprobefatalerror](http://www.ubuntuguide.org/#modprobefatalerror)

---

### Post by orion_114 on 2005-01-30
I have never had the error but just looking at the message I recon it could be related to some PCI device you have in your machine ?
Have you got any weird PCI devices installed ?
Try maybe removeing any un-needed PCI devices and rebooting to see if that is causing the problem.

---

### Post by eBast on 2005-01-30
[QUOTE=WW][http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
[http://www.ubuntuguide.org/#modprobefatalerror](http://www.ubuntuguide.org/#modprobefatalerror)[/QUOTE]

Thankyou very much, I should have searched the forum before posting  :o ... Any way thanks.

---

