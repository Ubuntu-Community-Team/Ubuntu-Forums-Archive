---
title: "[solved] ata1.00 slow, please wait/sata controller"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by sjalmond on 2008-08-16
I've been fighting this bug for two weeks, and I've finally solved it. There's several mentions of the problem on Google, but apparently no mentions of solutions... until now. Another first for UbuntuForums?


* Synopsis
PC won't boot with sata drives plugged to sata controller
Plug sata controller in a different slot


* Affected hardware/software:
[Some or all of]
Ubuntu 2.6.24-19-server [PC and/or LiveCD]
440BX chipset (motherboard)
SIL3512 PCI controller
Samsung Spinpoint HD501HJ SATA (sata2, sataII) harddrive [x2]


* Symptoms
Bios can see PCI controller
Controller's RAID utility can see drives
Drives work in other computer(s)
[i.e. problem is config, not parts]
System will boot to initramfs
ata0.00 and ata1.00 complain again and again and...
 - slow response, please wait
 - SRST, DRDY
 - UDMA/133, then /100, then /66, then /33, then /33...


* Cause
Don't know. Thought the controller couldn't translate from sata2 to PCI. Actually, maybe, it was an IRQ conflict


* Solution - step that worked
Unplug the PCI controller (4th slot from CPU). Plug it in a different slot (3rd from CPU).


* Solution? - steps that didn't work [enough?]

/boot/grub/menu.lst:
 - add "acpi=off noapic nolapic irqpoll" to kopt=

partition:
- partition and format disks with LiveCD/other PC

harddrives:
- jumper to 150 [units?]
- set to 150 [?] with SSpeed CD

modules:
- libata, sata_sil installed and in /etc/modules


* Other things I tried

grub:
 - boot with 'hda=noprobe', etc
 - set root to (hd2,0) and all combinations


* Ongoing issues
1) device letters (sda1, etc) have changed. Changing /boot/grub/device.map didn't seem to help - but I'm still working on this


Any thoughts, comments, suggestions on the above welcome, otherwise excuse me while I feel smug (and slightly surprised) for a bit  :-D

---

