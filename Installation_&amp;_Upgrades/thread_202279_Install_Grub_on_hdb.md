---
title: "Install Grub on hdb"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by kievking on 2006-06-23
I want to install 3 OS on hdb. I created three ext3 partitions and a swap partition. I tried to install Dapper first, but I wasn't given the option to install the bootloader(grub) on hdb - it defaulted to hda(XP). Then I tried to install Fedora5, and I got the same lack of bootloader options.  I did this before with 5.10 and Fedora4 without any problems, now the latest releases won't allow me to do so. How do I change the bootloader location to hdb? I DON'T want to make any changes to hda.
Do I have to install grub manually after I install the operating systems? If so, how do I get the kernel info without booting into the OS?

---

### Post by jvl on 2006-06-23
I believe grub gets installed into MBR of the first disk according to the BIOS settings. Try changing the boot sequence.

---

### Post by kievking on 2006-06-23
Thanks, I'll try that.

---

### Post by kievking on 2006-06-23
That's all I needed to do........thanks again

---

