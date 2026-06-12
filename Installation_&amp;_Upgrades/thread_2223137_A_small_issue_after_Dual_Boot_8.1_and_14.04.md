---
title: "A small issue after Dual Boot 8.1 and 14.04"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by rigel4 on 2014-05-09
Dear Mates,

I have Installed Ubuntu 14.04 to a separate drive (Sata 3 320GB)

I turned off Fast boot previously to clear that cache on the Windows Drives.

Secure boot is still enabled as is EFI.

I have re attached 128GB Samsung SSD.

I have re attached 1TB Data Drive.

If I reboot my computer I can tap F8 and choose the SSD to boot Windows (All is Well Here)

I can also Select the 320GB Ubuntu drive and boot Ubuntu  (All good here too)

So my question is how can i get Grub or BIOS to give me a choice of OS's

Any assistance gratefully received.

Motherboard is Asus Maximus V1 Formula

---

### Post by oldfred on 2014-05-09
Grub does not work with secure boot currently.

Is Ubuntu installed in UEFI or BIOS boot mode?
 You can only dual boot from grub menu if both systems are in same boot mode. UEFI & BIOS are not really compatible, so once you start booting in one mode, you cannot change without a warm reboot and choosing in UEFI menu. Some systems even require you to turn on/off UEFI or BIOS modes to correct boot a system in the mode set in UEFI/BIOS. Others will auto switch.

Post link to BootInfo report to see details.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rigel4 on 2014-05-09
Thanks for the info above!
I'm sure i will find what i need in there.

---

