---
title: "Dualboot with Windows 8 UEFI"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by amandus on 2013-04-02
Hi
When install Ubuntu and dual boot with windows 8, is it better to share the EFI partition that Windows 8 have or is it better creating one for Ubuntu too? Having two EFI partitions?

I can´t get it to work, Ubuntu boots but not Windows 8, I have two EFI partitions. I have tried the Ubuntu boot rescue disk but it does not work either

[SOLVED]

I installed Arch instead followed this tutorial.[URL="http://www.neuraladvance.com/2012/11/17/arch-linux-windows-8-uefi-lvm/"]
http://www.neuraladvance.com/2012/11/17/arch-linux-windows-8-uefi-lvm/[/URL]

---

### Post by oldfred on 2013-04-02
You only can have one efi partition per hard drive. Your link is for two hard drive install. 

If you boot Ubuntu in UEFI mode it will install grub2's efi boot files into the existing efi partition, in a separate ubuntu folder. With two drives you should install grub'2 efi files to the same hard drive as the Ubuntu install and then modify the chain load to Windows to see the other efi partition on the Windows drive.

---

### Post by amandus on 2013-04-03
I modified the tutorial for my needs, using sda disk instead and ordinary partitions.

---

