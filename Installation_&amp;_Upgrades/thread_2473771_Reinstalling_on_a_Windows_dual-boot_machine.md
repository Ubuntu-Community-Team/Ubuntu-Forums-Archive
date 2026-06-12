---
title: "Reinstalling on a Windows dual-boot machine"
date: 2022-04-13
forum: Installation &amp; Upgrades
---

### Post by chagzuki on 2022-04-13
If I clean reinstall Ubuntu on a dual-boot machine, where during the prior install Ubuntu detected Windows bootloader and grub was placed to coincide with that, will I cause any problems by repeating the process to reinstall Ubuntu? Will Ubuntu create a second entry in grub, and make a mess?

---

### Post by grahammechanical on 2022-04-13
Did you choose the install alongside option and do you intend to choose the install alongside option again? If so, then you will end up with a triple boot of three operating systems. You need to choose the Something Else option and set mount points for the Ubuntu partitions. Do you know how to do that?

I am dual booting Ubuntu 20.04 with Ubuntu 22.04. During the installation of 22.04 the EFI boot files of 22.04 would have replaced the EFI boot files of 20.04 in the EFI partition. No harm was caused. On your system the Windows EFI boot files in the EFI boot partition will not be touched. 

Regards

---

