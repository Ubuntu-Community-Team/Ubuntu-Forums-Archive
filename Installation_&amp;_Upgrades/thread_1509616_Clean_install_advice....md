---
title: "Clean install advice..."
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by cozski on 2010-06-14
Hello

I am intending to install Lucid on 3 desktop PCs for a local organisation, using the USB install method. One PC has XP installed on it and the other Windows 7 (although it doesn't run properly). Can I just install Lucid over the top and ask it to erase the other systems or do I need to erase the other OS first? I don't have either of the original Boot/Installation discs - can I erase using a simple Fdisk command? If so, can anyone point to to a How To?

Thanks in advance...

Coz

---

### Post by mick222 on 2010-06-14
When installing the partitioner asks if you want to erase all partitions .
I'd set up separate /home partitions as it makes upgrading easier.

---

### Post by darkod on 2010-06-14
Yes, separate /home partition makes possible to do new clean install but to keep your personal files and settings in your Home folder, which in that case will be on the separate /home partition.
But in order to do that, you need to use Manual Partitioning. When the list of partitions show, you can delete all of them if you want, and create new partitions.

For root / partition, 15GB is enough.
For swap 2GB or 1.5 x RAM memory size if planning to hibernate regularly.
For /home, the rest of the disk.

In the installer there is automatic method option Erase and use whole disk, which will do what you want, delete the whole disk and install ubuntu on it. But it creates standard / + swap setup, without separate /home.

---

### Post by cozski on 2010-06-14
Okay, seems straight forward enough... thanks :)

---

### Post by cozski on 2010-06-14
Just as a follow on... in the boot sequence I dont have the option to boot from USB and I'm not able to create a CD image to boot from the CD drive. I also dont have internet access at the moment. Is it usual for there not to be a boot from usb option even though there are usb pots?

---

### Post by darkod on 2010-06-14
> **cozski said:**
> Just as a follow on... in the boot sequence I dont have the option to boot from USB and I'm not able to create a CD image to boot from the CD drive. I also dont have internet access at the moment. Is it usual for there not to be a boot from usb option even though there are usb pots?

Older computers might not be able to boot from usb. In boot devices the option is usually called usb-hdd even if you use usb stick, you need that option. Just having usb ports doesn't mean a computer can boot from usb.

Look around again in BIOS.

---

### Post by cozski on 2010-06-14
Okay, I'll have a look thanks.

---

