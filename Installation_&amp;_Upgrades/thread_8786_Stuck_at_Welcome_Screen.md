---
title: "Stuck at Welcome Screen"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by Jean-Marie on 2004-12-21
I did the basic installation and could reboot without CD Rom. First errors I get are the following:

*Starting Hotplug System
modprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko: Operation not permitted

modprob: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko: Operation not permitted

modprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko: Operation not permitted

modprob: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko: Operation not permitted

modprob: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/hwrandom.ko: No such device

*******************

Then I get stuck at

*Setting the System Clock using the Hardware Clock as reference...

although the same was already done earlier and confirmed with OK.

*******************

The only thing I can do here is to press CTRL+C after which the installation process continues till the Welcome Screen where no further keyboard entries will allow me to confirm the <Ok>.

*******************

So far I haven't found anything on the forums or google about that problem.

Did anyone solve it anyway and how?

Any help is appreciated.

Jean-Marie

PS: My System

DELL Insprion 4700 3GHz 1GB 160GB 

Partition:

1. DELL FAT 50MB
2. Windows XP Home NTFS35GB
3. SWAP 3GB for Windows XP
4. BOOT 50MB for Ubuntu
5. SWAP 2GB for Ubuntu
6. EXT3 35GB for Ubuntu
7. Free 35GB
8. Windows XP DATA NTFS 35GB
9. FAT 5GB

---

### Post by nemin on 2004-12-21
[QUOTE=Jean-Marie]I did the basic installation and could reboot without CD Rom. First errors I get are the following:

*Starting Hotplug System
modprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko: Operation not permitted

modprob: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko: Operation not permitted

modprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko: Operation not permitted

modprob: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko: Operation not permitted

modprob: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/hwrandom.ko: No such device
[/QUOTE]
I don't think I can help you with this problem, but I can tell you that the errors above probably have nothing to do with the problem, as you can read here:
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
So you don't have to spend time on fixing this :) Good luck with finding the real problem.

---

### Post by Jean-Marie on 2004-12-21
[QUOTE=nemin]I don't think I can help you with this problem, but I can tell you that the errors above probably have nothing to do with the problem, as you can read here:
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
So you don't have to spend time on fixing this :) Good luck with finding the real problem.[/QUOTE]

Thanks. Something less to worry about. :-)

I wonder if I could suspend the second "Clock Setting" since it already successfully sets it just a few seconds before.

Jean-Marie

---

### Post by stormumriken on 2005-01-01
I get the same problem on a Dell system.

When I am lost at the Welcome screen, I use a second screen (alt-F2)
where I run 'ps -efH', notice that hwclock and awk is locked in a pipe,
presumable eating whatever I write at the keyboard. I kill them both
with 'kill -9' and can continue.

I am sorry that I cannot tell you what gets wrong in the hwclock
algorithm. The simple method is to 'rm /etc/rc*.d/*clock*', but there
might be a smarter solution...

At URL [http://ubuntuguide.org](http://ubuntuguide.org) you are told how to get rid of
the error printouts (using sudo gedit /etc/hotplug/blacklist).

My machine is a Dell Dimension 4700 with a SATA HD and a
128 MB ATI Radeon X300. (I have problems also with the
Radeon in Ubuntu.)

-- Lennart

---

