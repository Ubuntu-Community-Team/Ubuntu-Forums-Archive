---
title: "minimal ubuntu hangs durning boot"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Sovereign Entity on 2010-05-24
I installed minimal ubuntu on a 80 Gb drive partitioned as 12 Gb root and 2 Gb swap the rest is free space. I also have 2 250 Gb drives i raid 1. The system is 2.4 Ghz Athlon 2, 1 Gb memory Gigabyte motherboard Ga- 7vaxp. The system hangs after Verifying DMA pool data.....
Boot from CD. 
 But if i disconnect the raid I get error loading OS

---

### Post by ronparent on 2010-05-24
Hardware or software raid?

---

### Post by oldfred on 2010-05-24
Did grub install to one of the raid drives for booting or do/did you specify grub to install to the 80GB drive and set it to boot in BIOS?

---

### Post by Sovereign Entity on 2010-05-24
The raid was set in the bios but ubuntu saw it as 2 drives not as raid 1. But the install set it durning the install. And I'm not sure where grub was installed but i have formated the drive and now trying to install again without the raid drives.The install keeps failing and the disk checksum okay. I was wondering do some of these packets come over the net or is everything on the disk?

---

### Post by ronparent on 2010-05-24
first off, both your observations are correct for the current state of 10.04. With the raid connected, gparted (the partitioner use by the live cd) does not see the partitioned raid. The installer does. 

With the raid disconnected, it should have no effect on the install. The install should proceed normally. Any problems encountered will be inherent with the hardware in play. Once installed, presumably on the 80Gb drive, the grub will be installed to boot from that drive and the installed system should be bootable. Can you boot the live cd?

We may have to clear up whether you may need some special boot parameters to allow 10.04 to work on your computer. Once working, you should have no problem mounting any of the raid partitions from within 10.04. Also a grub **update** should find any OS installed on the raid and be able to boot to it (providing the 80Gb drive is set to boot in bios).

---

### Post by Sovereign Entity on 2010-05-24
Thank to everyone First off I disconnected the raid just to eliminate that as a potential problem.And after many tries i did get the minimal ubuntu installed and booting. I have also installed xorg, LXDE as a desktop,gnome display manger and synaptic. All seemed to work but i cant start snaptic from the run terminal.Fail to execute child process( No such file or directory) And how do I mark this as solved.

---

