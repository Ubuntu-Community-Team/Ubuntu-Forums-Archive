---
title: "A grub dual boot problem"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by dimmaz88 on 2014-08-12
Hi, I recently re-installed ubuntu 14.04 from 12.04.

I have windows 7 installed on a separate hdd, and ubuntu on an ssd. I had a few issues with ubuntu 12.04 so thought I'd update it.

Since installing it I don't get the boot menu. Both drives are UEFI although I don't know if that makes a difference in this case.


I've tried using the live boot repair cd, but that didn't work. It said I need to create a <1mb partition..... Not sure of the rest of it but it baffled me.


Any help is appreciated.

Thanks


EDIT: I've just noticed in the bios it won't let me select the windows hdd as a boot option. However, it is recognized in another menu.

---

### Post by oldfred on 2014-08-12
If Boot-Repair is asking for the bios-grub partition, you are trying to convert an UEFI install to BIOS install. Grub does not correctly install in BIOS mode to gpt's protective MBR without the 1MB unformatted bios-grub partition.

Did you reinstall in UEFI mode? How you boot installer is how it installs.

And UEFI and BIOS are not compatible. So you can only boot from UEFI/BIOS into systems installed in different modes. And some require you to turn on or off UEFI or BIOS/CSM/Legacy boot modes. Secure boot only is available with UEFI. If dual booting best to have secure boot off also.

Post ths link from Boot-Repair's BootInfo Summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

