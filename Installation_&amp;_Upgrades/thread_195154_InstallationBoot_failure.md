---
title: "Installation/Boot failure"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by shri_nath on 2006-06-12
Hello I just downloaded the iso image of the alternate amd 64 cd (ubuntu 6.06)
The installation goes through with no problems. Then it asks me to remove the cd and restart. After that I get the following message :
"Disk Boot Failure, Insert Sytem Disk and Press Enter"

I have following hardware configuration:

Motherboard: Asus A8N SLI Premium. This has built in SATA ports and built-in two network interfaces

CPU: AMD Athlon 64 FX-55
Memory: 1GB Corsair PC3200 DDR DIMM
Video Card: PCI Express
SATA Hard Drive 1: Seagate Barracuda 7200.8 250 GB
SATA Hard Drive 2: Seagate Barracuda 7200.8 250 GB
SATA Hard Drive 3: Seagate Barracuda 7200.8 250 GB
SATA Hard Drive 4: Seagate Barracuda 7200.8 250 GB
Optical Drive 1: Sony
Optical Drive 2: Pioneer

Your help will be appreciated as I have wiped out my WindowsXP and the machine is not usable now. Thanks
shrinath

---

### Post by frodon on 2006-06-19
I have the same problem than you since this morning.

There're 2 possibilities :

1- Your disk with the MBR is dead. If it's the case you will have to change the disk by another one and re-install your OS.
2- There was a failure when writing the MBR on your disk and the MBR is corrupted which make the disk unusable. To solve that there's 2 way :
2.1 : re-install GRUB/MBR with the ubuntu install CD or the live CD : [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
2.2 : Fix the MBR with your windows CD : [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Good luck ;)

---

### Post by rcarring on 2006-06-19
I notice that all the drives are SATA. Isn't there an existing issue with trying to write grub to the mbr of a sata drive?

Perhaps installing grub to a floppy might work. USB floppy drives are very cheap.

---

