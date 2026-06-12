---
title: "booting up ubuntu"
date: 2004-12-06
forum: Installation &amp; Upgrades
---

### Post by jelavich on 2004-12-06
I have a dual boot using grub :XPP & Unbuntu.  My XPP is working fine, but everytime I  boot up ubuntu, I get this message during the "booting up" screen:

modprobe: FATAL : Eroor inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: FATAL : Eroor inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: FATAL : Eroor inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: FATAL : Eroor inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

(I meant to repeat them)  Anyways, so half the time the computer just keeps on going with loading process and ubuntu seems to work just fine.  The other half of the time the loading process just stops completely and I have to manually turn off my computer and reboot it.  It's really annoying.

So, I have three questions. 
1) What is "shpchp" and "pciehp" ?
2) What is wrong with my computer/linux?
3) How can I fix this problem?

Thanks.

---

### Post by dataw0lf on 2004-12-07
shpchp and pciehp are both hot plug drivers.  This is a common error on boot; in fact, it's covered briefly in the Ubuntu Linux Wiki: [http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
dataw0lf

---

### Post by Hikaru79 on 2004-12-07
Wow!! What a relief. I've been getting those errors ever since I first installed, and I've always been kinda worried about it >_> Feels good to know that it's nothing really serious!  :D

---

