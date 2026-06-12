---
title: "Dual booting with Vista - 2 SATA HDDs"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by sirali on 2007-10-19
Hi,

I have Windows Vista Business x86 installed on a 160GB SATA HDD with 2 partitions.

I bought an 80GB SATA HDD to install Ubuntu on it.

I manually partitioned the 80GB HDD as follows:
- 15GB ... / 
- 60GB ... /home
- 3GB ... swap

After the setup has finished...I restarted and then a BOOT Failure message came up. I can't boot into Vista nor Ubuntu...

By the way

The 160GB was marked SCSI 1 (0,0,0) (sda)
while the 80GB was marked SCSI 3 (0,0,0) (sdb)

Help please...

---

### Post by Pumalite on 2007-10-19
Your error message would help.

---

### Post by sirali on 2007-10-19
Disk Boot Failure. Insert System Disk And Press Enter

---

### Post by Pumalite on 2007-10-19
See if you can get Grub switching the boot order of your drives in BIOS.

---

### Post by sirali on 2007-10-19
Thanks it works now :)

---

