---
title: "after the grub part in setup windows boots again?!?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by Vlatko on 2006-06-19
hello!

i have a sata disk 250gb. one 50gb partition with xp, 160gb for stuff and a new 20gb for linux.

so i just went to install kubuntu breezy badger and everything went fine till the part where the system wants to reboot. at my first installation attempt i got a error: "missing operating system". this time however after grub was installed and setup said it needs to reboot nothing happened, the system loaded into windows as if nothing happened??

what am i missing? when the installer asked i said yes to install grub to the master boot record as so was suggested in numerous guides i read.

i'd appreciate any feedback. 
thanks!

---

### Post by zxee on 2006-06-19
Did you get back a "grub installed..." response after you choose that option?
It certainly seems like it wasn't. I think booting from the install disc and typing in linux rescue or selecting it if that's an option (don't recall the specifics to the breezy installer) is your best bet.

---

### Post by Vlatko on 2006-06-20
no the problem was in my second drive which is a ide 120gb seagate. that drive has no os only my personal stuff. the grub was installed on the mbr of my first disk. the problem lies in the fact ide disk are always numerated before sata(which has my windows xp). anyway changing the disk boot priority in bios, so ide drive is first, grub starts up and i can boot both in xp and kubuntu.

the problem is i don't like that my ide drive was touched during the installation. that drive contains enourmous amount of really important data and i don't like to "install" anything on it.

right know i would like to know how i can remove grub from the mbr of the ide drive. than i would do a fresh install of kubuntu only this time i will unplug the ide drive untill the install completes.

is there any safe way of removing the grub? can it be done without formatting at all?

---

