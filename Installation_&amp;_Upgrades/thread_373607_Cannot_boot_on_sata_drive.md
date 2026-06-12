---
title: "Cannot boot on sata drive"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by ksenos on 2007-03-01
Hello...

I wanted to install from scratch ubuntu on a sata disk but I got some serious problems. My motherboard is an _albatron px865pec pro_ which is supposed to support sata. The boot cd started normally and detected the new hard drive correctly (as a scsi disk - /dev/sda). I also have a second disk with winxp configured as a primary slave drive. I got it like this because I had ubuntu on a primary master disk which I removed it after installing the sata drive. Like I said the installation went without any problems. But when I try to boot from the sata drive (I needed to upgrade my bios to be able to boot from it) the grub shows up and crashes telling me that "err 15: file not found". I tried an option in the bios setup, the SATA ONLY opton and the message changed to "drive not found" (or something like that). Could someone suggest a solution? Thanks in advance...

---

### Post by ksenos on 2007-03-01
It seems i ve been lucky. On the grub screen I changed the (hd1,0) to (hd0,0). Perhaps on the setup the grub gets confused and names the sata drive as hd1. But since i configured bios to use the sata drive as primary boot device this changes to (hd0,0) (or something like that). Anywayz, solved :-)

---

