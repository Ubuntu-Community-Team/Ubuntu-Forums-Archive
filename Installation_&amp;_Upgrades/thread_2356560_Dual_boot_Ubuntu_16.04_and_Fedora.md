---
title: "Dual boot Ubuntu 16.04 and Fedora"
date: 2017-03-24
forum: Installation &amp; Upgrades
---

### Post by Music_Guy on 2017-03-24
Two more questions. I have seen that 'sudo update grub' should be run from the Ubuntu side to allow dual booting into Ubuntu or Fedora. Is this a generic command to use for either BIOS or UEFI installs, or should the command be 'sudo update grub-efi-amd64' for UEFI? And, will I have to install grub or grub-efi-amd64 before running that command?

---

### Post by Dennis N on 2017-03-24
1) The command **sudo update-grub** is the same regardless of BIOS or UEFI system. All it does is rebuild the /boot/grub/grub.cfg file which generates your grub menu.
2) You don't need to install grub before running the command, but if you ever did reinstall grub, then you should run it afterwards.

---

### Post by oldfred on 2017-03-24
If you install Fedora with all it defaults it uses LVM.
LVM is an advanced partitioning system that works best if it is the entire hard drive.
If dual/multiple booting, you can install Fedora in standard partitions just like Ubuntu. 
Or install Ubuntu inside the LVM manually creating the additional LVM volumes.

Gparted only works on the underlying physical partitions, all LVM partitioning must be done with LVM tools.

You can dual boot with Ubuntu in standard partitions & Fedora in LVM, but in Ubuntu must add the LVM tools lvm2 and mount the LVM so when you run sudo update-grub it can find the install inside the LVM.

If BIOS, last install will have its version of grub in MBR. Best to have system you use most as default boot.

With UEFI, all system share ESP - efi system partition and you can choose any from UEFI boot menu as it also is a boot manager.
 And you can change boot order in UEFI or with efibootmgr.
Grub is both a boot manager (menu) and a boot loader. So with UEFI you have UEFI menu and each install's grub menu.

---

### Post by Music_Guy on 2017-03-26
@Dennis and @oldfred, thanks for all of your help. I just set up my mac for dual booting into Ubuntu Studio 16.04 and Fedora 25. I'm in the process of reinstalling software in Ubuntu. Thanks again.

:D :D :D

---

