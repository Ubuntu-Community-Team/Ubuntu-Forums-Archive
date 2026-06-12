---
title: "Mix and match IDE (2) slave HD with IDE (1) master windows HD"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2012-07-01
Any suggestions about the principles relating to me putting a second HD with Lubuntu, into an existing Windows PC?

The exact situation: I disconnected the Windows drive (which was master in the IDE channel 1) and temporarily rigged a second HD into the IDE 2 as slave (because the cd drive is IDE2 master). I installed a couple of Lubuntu versions (FWIW 11.10 and 12.04) into the additional HD.

In the absence of the Windows HD of course, the PC booted from the Lubuntu HD ok. 

I now want to reconnect the Windows HD and arrange this PC to act as a dual boot PC.

I guess both HDs are set as having an active  bootable partition, and both have a boot sector with a boot manager active.

What is the elegant way of proceeding?

I am aware of the Boot Repair disc, and it is magic enough to probably do it all at a stroke, however I would appreciate knowing what the manual actions should be for me to achieve my objective.

Comments appreciated, tia

---

### Post by oldfred on 2012-07-01
Old IDE systems used jumpers on hard drive to control master and only Master was bootable. Newer IDE have jumpers set with cable select and use a newer 80 conductor cable. Often those BIOS then allow you to directly boot either drive. 

If BIOS allows it you should be able to boot either drive. 

Otherwise you have to install grub to the boot drive to get the option to boot both Windows & Lubuntu. Best to keep Windows as sda as it has the drive coded into boot.ini. Grub tries to map device to make Windows think it is sda even when sdb but still best to keep Windows as sda.

Some versions of Lubuntu did not have the os-prober even with grub2. If sudo update-grub does not add Windows to the menu, install the os-prober.

---

### Post by candtalan on 2012-07-01
> **oldfred said:**
> Old IDE systems used jumpers on hard drive to control master and only Master was bootable. Newer IDE have jumpers set with cable select and use a newer 80 conductor cable. Often those BIOS then allow you to directly boot either drive. 

If BIOS allows it you should be able to boot either drive. 

Thanks.
This PC allows to boot from a slave HD so I guess it is the newer IDE, so after a bios Setup and save, I will try to boot and see what happens.

---

