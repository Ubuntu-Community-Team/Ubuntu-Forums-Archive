---
title: "Install Issues on all SATA set-up"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by dchw_dude on 2008-06-08
The other day I thought I would switch over to Linux on my desktop. Unfortunately, it seems that I am having some trouble. It freezes at "Waiting for root filesystem" as I install. The MD5 on the disk checks out, have tried a few burns as well. Windows Vista installed without trouble.

The distro is Kubuntu 8.04. I have an ABit IP35-E Motherboard. Some Googling revealed other IP35-E issues circulating around that JMicron SATA controller and people with all SATA drives. Unfortunately that is my case. It was suggested in many forums that you add "--irqpoll" as a boot option, but that does not work. It has also been suggested that I put my drives into AHCI mode. Unfortunately that is not a BIOS option on the "E" version of the ABit p35 board.

More googling revealed that some have found success by installing with the alternate install disk, and then adding "all_generic_ide" to the kernel line in /boot/grub/menu.lst. After burning the Alternate CD the Install will begin, but still the same issue. The install wont recognize my drives, it asks me to load a module for the cd-rom. I try the one labeled "cd-rom" and it goes back and says that setup cant find my drives. checking the /dev directory shows no cd rom device listed.

Tracking it down, I see that the IRQ for SATA 1-4 on the ABit IP-35 boards is "double-booked"(anyone else can verify?). Since the IP35-E only has SATA ports 1-4 . . . this was causing other people trouble, but I could not find a resolution.

Am I just SOL on installing Kubuntu? What do you all suggest?

Specs:
Abit IP35-E
Intel Q6600
EVGA NVidia 9600GT
600 GB WD Caviar
CD-Rom and HDD both run SATA.

---

### Post by odin79 on 2008-06-10
I had the same problem. To get Hardy to work I had to install Guttsy and then upgrade from there. My dvd-rom still doesn't work though. I tried the "all-generic-ide" option, but then my harddrive speed will be REALLY slow.

I have SATA-disks.

Can anyone help?

Please?

---

### Post by Pumalite on 2008-06-10
Have you tried changing SATA ports?

---

