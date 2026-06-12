---
title: "Ubuntu LiveCD not detecting SATA hard drive"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by zchenyu on 2008-08-11
For some reason, Ubuntu 7.10 LiveCD doesn't detect my SATA HD. I get a couple messages from dmesg:
> end_request: I/O error on device fd0, sector 0
Buffer I/O error on device fd0, logical block 0
The message is reported several times throughout dmesg.

fdisk -l returns blank

I found that a GParted LiveCD detects the drive perfectly fine. I dual-boot with Windows XP.

---

### Post by prshah on 2008-08-11
> **zchenyu said:**
> 
fdisk -l returns blank

what does ```
sudo fdisk -l
``` give you?

---

### Post by Ptero-4 on 2008-08-11
the fd0 part indicates that it cannot see a floppy drive there (which if that were a Mac, laptop or mini-atx computer would be expected since those types of computers lack floppy drives).

---

### Post by zchenyu on 2008-08-11
sudo fdisk -l gives the same thing (blank)

> the fd0 part indicates that it cannot see a floppy drive there (which if that were a Mac, laptop or mini-atx computer would be expected since those types of computers lack floppy drives). 
Thanks for clearing that up. Then I suppose the snippet of dmesg I showed is irrelevant to this issue.

---

### Post by zchenyu on 2008-08-11
Ok, I got an Ubuntu 8.04 CD but to no avail. I also tried adding the "acpi=off noapic" options to the kernel boot command, also without results. Any other ideas?

---

### Post by zchenyu on 2008-08-12
Ok, I got it to work :)
As future reference for others who may encounter this problem, I did the following:
- Changed the drive setting in BIOS to AHCI (as opposed to IDE)
- Added following kernel boot options: acpi=off noapic udev cdroot dodmraid

---

### Post by deep_friar on 2008-08-12
[QUOTE=zchenyu]- Changed the drive setting in BIOS to AHCI (as opposed to IDE)
- Added following kernel boot options: acpi=off noapic udev cdroot dodmraid [/QUOTE]

Tried using these directions myself, because I was having the same problem:

Changing the SATAII configuration from IDE to AHCI was the only change I needed to make;
udev, cdroot, and dodmraid proved irrelevant;
and either acpi=off or noapic was resulting in failure to boot from CD (I was getting kicked out into a BusyBox terminal and receiving recurring salvoes of error messges).

This was with an ASRock P43Twins1600 motherboard and Hitachi Deskstar 320 GB SATA HD.

---

### Post by andreiashu on 2008-10-14
> **zchenyu said:**
> Ok, I got it to work :)
As future reference for others who may encounter this problem, I did the following:
- Changed the drive setting in BIOS to AHCI (as opposed to IDE)
- Added following kernel boot options: acpi=off noapic udev cdroot dodmraid
Thanks !! the AHCI solution worked without a problem. No other stuff where required.

---

