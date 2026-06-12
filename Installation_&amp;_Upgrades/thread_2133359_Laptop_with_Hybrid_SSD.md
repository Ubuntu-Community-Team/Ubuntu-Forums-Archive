---
title: "Laptop with Hybrid SSD"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by dragnus on 2013-04-07
Hey,

I have a Laptop with 2*750 gb hard drives. It also has a [COLOR=#444444][FONT=arial]SanDisk [/FONT][/COLOR][I]iSSD P4.

[/I]This is used as a cache in Windows. I was hoping to install Ubuntu onto this SSD.
This SSD is only 8gb in size.

I tried different methods, such as installing only the "/" onto the SSD and the rest onto main hard drive. But it would not work.

When booting from a live ubuntu disk, the SSD drive is visible. It is also visible in windows under the partitioning options.

However, it is not visible in the BIOS, so i cannot boot from the device.
And as I said, after installing previously, it seems that the boot loader did not work as I was told that there is no operating system installed on the laptop.

Any ideas?

Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2013-04-07
you may be able to put the mbr on the hdd and have it boot the ssd with / on it

---

### Post by fantab on 2013-04-08
Is it **[SSD]("https://en.wikipedia.org/wiki/Solid-state_drive")** [Solid State Drive] or **[SD]("https://en.wikipedia.org/wiki/Secure_Digital_card")** [Secure Digital]? BIOS won't boot SD cards. You can try putting GRUB boot-loader on HDD and Ubuntu on the card and try, like suggested in post #2.

If its SSD and Hybrid then there may be RAID and/or Intel SRT on the system. Please confirm. Either can cause kind of issues you are having.

---

