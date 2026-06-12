---
title: "Major headache with new installatino with multiple hard drives and GRUB Error 17"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Jack33 on 2008-05-04
Okay so i just installed kubuntu latest release, however i did it with the drive i installed kubuntu on as the not being the master or whatever. Anyways, i switched my drive configuration so i could actually get GRUB to try to start but now it just gives Error 17. I just want to reinstall grub so it fixes this, I am going to give all the bios hard drive posts.
Also Note: I am using a PCI IDE card that has 1 ide cable connected to it holding 2 drives. I will list this in the post as well.
Here we go:
the main bios post shows:
ide channel 0 Master: WDC WD1200JB-75EVA0 15.05R15
ide channel 0 Slave : WDC WD2500JB-00GVa0 08.02D08
Ide Channel 1 Master : HP DVD Writer 640 JS04
IDe channel 1 slave : none

Ide channel 2 Master : None	
Ide Channel 2 Slave  : None

After that the PCI IDE card Post shows: 
Ultra 100 Promise PCI Controller:
D0 Maxtor 6Y120P0  LBA 117246MB Ultra DMA 5
D1 WDC WD1200JB-00GVC0 LBA 114473MB Ultra DMA 5 
D2 Not Detected
D3 Not Detected

IDE Bus Master Enabled

Finally if i go into bios setup and look at the boot device priority:
Ch0 M. : WDC WD1200JB-75EVA0
Ch0 S. : WDC WD2500JB-00GVA0

---

### Post by Patb on 2008-05-04
Jack, see how you go with one of these:

[Reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351")

[Restore messed MBR]("http://ubuntuforums.org/showthread.php?t=24113")

Cheers, Pat

---

