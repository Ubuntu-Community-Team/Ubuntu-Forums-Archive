---
title: "Must boot to CD first before getting to grub on the HDD"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by mk4umha on 2008-06-16
Hi,

i have a weird problem. If I want to boot, i must use the Ubuntu install cd then select boot to HDD. Once that happens I can select the OS's to boot from from the grub menu on the HDD

If I try to boot directly to the HDD, I get a grub 22 error. Have you guys seen this problem before? How do i fix this?

---

### Post by Partyboi2 on 2008-06-17
maybe [[COLOR=Blue]this[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#22") might help

---

### Post by powerpleb on 2008-06-17
Sounds to me like you need to set Ubuntu's drive to have a boot flag. Do this in Gparted (partition editor in the Administration menu)
Right click on root (/) partition, select Manage Flags and check the boot option.

---

### Post by mk4umha on 2008-06-17
I have an AMD board with the Nforce5 chipset. I have 2 drives that I setup as raid in the BIOS. On cold starts, I must boot to the CD to get to Grub. Once I get into Ubuntu and reboot, the raid flashs red telling me it cant see the drives. Once that happens, it will boot to the haarddrive without needing the CD.

What do you think would cause it to boot into grub without a CD when the raid doesnt recognize the drives?

---

