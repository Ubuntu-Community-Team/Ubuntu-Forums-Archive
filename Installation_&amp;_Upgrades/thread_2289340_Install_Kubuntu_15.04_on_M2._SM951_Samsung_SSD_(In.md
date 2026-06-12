---
title: "Install Kubuntu 15.04 on M2. SM951 Samsung SSD (Intel HM87 (Lynx Point) mainboard)"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by tectown on 2015-08-03
Hallo guys,  following question: What can be the the reason, when the Samsung SSD M2. SM951 MZHPV512HDGL drive where I want to install a Kubuntu system on is not detected by the installer? I made a bootable USB stick with unetbootin and started the system with nomodeset in the bootoptions. The disk system started but the harddsik was not recognized. The ssd is not shown in the bios as well, but this seems to  be normal because it has not an own controller. What can I do to get thinks working?   Thank you for your help!

---

### Post by fjgaude on 2015-09-01
> **tectown said:**
> Hallo guys,  following question: What can be the the reason, when the Samsung SSD M2. SM951 MZHPV512HDGL drive where I want to install a Kubuntu system on is not detected by the installer? I made a bootable USB stick with unetbootin and started the system with nomodeset in the bootoptions. The disk system started but the harddsik was not recognized. The ssd is not shown in the bios as well, but this seems to  be normal because it has not an own controller. What can I do to get thinks working?   Thank you for your help!

From what little I know about the m.2 SM591, Neither my Z87 nor Z97 motherboards see the device as a drive. When I load grub and select the desired drive to boot, then use grub-update, the drive shows when I reboot in the grub menu. It acts as a good data drive, very quick and fast, with over 2000MB/s read speed using the **disk** utility with 0.030msec seek time. Now that is fast. I put the item in a PCIe x4 adapter and still no boot, just a data disk.

I've spent days trying to adjust the BIOS on Asus Z97 to get it to recognize the drive but to no avail.

I hope someone here can help... I don't use Windows on my machines, except VBox to virtualize XP and 8.0.

---

### Post by megahertz2 on 2016-06-30
On my Z170 MB, with SATA=AHCI it boots. With SATA=RAID it doesn't. Try to set SATA=AHCI on your MB to see if it is detected by the installer.

---

### Post by fjgaude on 2016-06-30
I have an SM950 booting on a Z170 Skylake and gosh, is this thing fast, likely because both of read and access times, 2000MB/sec and 20Microsec. Of course it an NVMe SSD M.2 in an adapter with heat sink.

---

### Post by oldos2er on 2016-07-01
Old thread closed; 15.04 is no longer supported.

---

