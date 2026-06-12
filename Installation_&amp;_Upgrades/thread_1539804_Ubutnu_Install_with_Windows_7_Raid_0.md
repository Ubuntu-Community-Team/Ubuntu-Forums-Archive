---
title: "Ubutnu Install with Windows 7 Raid 0"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by galtline on 2010-07-27
I have a system with RAid 0 with Windows 7. I want to load Ubuntu on a stand alone disk. I have two disks obviously for my raid o, two storage disks and an extra disk for ubuntu. I have tired to install unbuntu but upon start up I get an error on the disk. I than had to use grub to repair my mbr. My question is how do I make this work where I can have a dual boot system. I have been running ubuntu on my laptop and its simply insane.

---

### Post by P4man on 2010-07-27
I am assuming this is a fake raid (bios raid) ?
I think in theory ubuntu since 10.04 should be able to install its bootloader there; but i would not.

Here is what I would do: physically disconnect the raid drives. Install ubuntu on the spare drive. Reconnect the raid drives, but set the bios to boot from the ubuntu drive first. Ubuntu should boot, but you will not have dual boot yet. Open a terminal and run 

sudo update-grub

and it should pick up your windows install and add it to grub bootloader.

Advantages of this approach: both your windows and ubuntu will be able to boot completely independently from each other. If you remove the ubuntu drive, it can still boot windows. If something happens to windows or your raid, you can still boot ubuntu. And if something goes wrong with grub, you can use the bios to select which drive, and therefore which OS to boot.

---

### Post by ronparent on 2010-07-27
A problem exists with 10.04 in that gparted won't recognize a raid. I posted a bug report ([https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)) and received a response that suggested a quick fix. The problem occurs because 10.04 was distributed without a package called kpartx which is needed by gparted to read a raid. The solution is to open the 10.04 install from a live cd session, use synaptics to install kpartx for the session, and continue on to run a normal installation within the session. You may run into a glitch writing the grub boot loader to the raid but this can be fixed if needed.

---

