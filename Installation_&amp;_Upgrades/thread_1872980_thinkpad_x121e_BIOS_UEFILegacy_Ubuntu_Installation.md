---
title: "thinkpad x121e BIOS: UEFI/Legacy Ubuntu Installation doen't start"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by nearlymagicman on 2011-10-31
I just bought a new Thinkpad x121e and immediatly tried to install Ubuntu 11.04 (64Bit) but unfortunately it didn't start afterwards (like topic already implied). After a bit of research I found a thread stateing that a 32-Bit installation might succeed but that also failed on me. I also already tried to switch my BIOS from starting UEFI to boot legacy only, but this didn't succeed either. Furthermore I tired to install the LTS version (both 32 and 64bit) but this also wont work. I am installing either via USB-Stick or -Drive.

I am quite sure that this is no problem with the installation but with GRUB or whatever Boot-Routine is used as any installation does recognize the one before. As far as I can see the BIOS does not have any MBR protection.

&#8364;:After a bit of research I figured the main differences between my PC (on which Ubuntu works) and my thinkpad:
*the thinkpad uses a GPT Partition table which my PC doesn't use
*my thinkpad has a Legacy/UEFI BIOS


If any further information is needed i will be happy to provide them.

thx nearlymagicman

---

### Post by xrat on 2011-11-07
Same problem here. I wish I knew what is going on but right now I don't have the time to investigate. I followed the recommendation of [http://forums.lenovo.com/t5/Linux-Discussion/x121e-unable-to-boot-Linux-Ubuntu/td-p/578335](http://forums.lenovo.com/t5/Linux-Discussion/x121e-unable-to-boot-Linux-Ubuntu/td-p/578335) and re-installed the system without changing and disk/partition related settings. It worked.

In a German forum someone [suggested]("http://forum.geizhals.at/t759784,6526209.html#6526209") to change the respective BIOS setting from "UEFI/Legacy Boot" to "Legacy Only".

---

