---
title: "[SOLVED] Gparted can't see hard drive to make partitions to install Hardy"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by BlockBomb on 2008-08-20
Hello I just finished building my computer and I've been trying to install Ubuntu 8.04.1 onto it.  when I put in the live cd I can boot into it just fine but when I go to install it I get hung up on part 4 of 7 where it asks to set up partitions. when Gparted loads it cannot find my Hard drive.

CPU: Intel Core 2 Duo E8400
GPU: Nvidia Geforce 8800
Motherboard: Biostar T43
HD: Western Digital 400Gb S-ATA

I'm getting the feeling after reading some forums that it may have to do with the fact that my HD is S-ATA? would this be a correct assumption? I've tried multiple methods during boot such as 'pci=nommconf irqpoll' and 'acpi=force irqpoll' 'pci=nomsi'
I can't seem to figure it out. 

I'm very new to all this any help would be appreciated

---

### Post by BlockBomb on 2008-08-20
Never mind after looking through some more forums I found that changing sata #1 to AHCI in the bios it solved my problem.

---

