---
title: "Is GRUB compatible with GPT and MBR at the same time?"
date: 2018-09-21
forum: Installation &amp; Upgrades
---

### Post by unalfaruk on 2018-09-21
I have a SSD and a HDD, my SSD is formatted as GPT and my HDD is formatted as MBR. 


When my drives were formatted as MBR, I could use dual boot (Debian 8 and Windows 8.1) in UEFI mode without problems. A day, I installed Win10 and it formatted my disk as GPT and after that day I have always "shutdown" problems. I returned to Windows 8.1 again, but after a short time my Windows starts to not shutdown. I tried all solutions to overcome but there is no fix still.


Now my question is that having two different formatted drives may be the problem for GRUB or any boot or shutdown/unmount process?

---

### Post by yancek on 2018-09-21
Grub is a bootloader and its only purpose is to boot the different OS's on the computer.  Doesn't have anything to do with shutting down.  Have you tried posting at a windows forum about the shutdown problem with windows?

It is best to have both (all) systems installed using UEFI/GPT or Legacy/MBR.  Are you still using Debian with your windows 8?  Is Debian installed Legacy/MBR or is it UEFI?  Do you have problems also with shutting down Debian?  Do you have fastboot/hibernation enabled in windows?

---

### Post by oldfred on 2018-09-21
I think your issue is UEFI vs BIOS.

I started to use gpt with BIOS boot of my Ubuntu 10.10 and grub booted Windows XP on a MBR drive.
I then started converting all drives to gpt with bios_grub partition which is required by grub for BIOS boot. When Microsoft started requiring UEFI/gpt with Windows 8 I started adding the ESP - efi system partition for UEFI boot on new drives, even though still booting in BIOS mode. Then I only would have to update grub to convert to UEFI boot.

Windows 8 or 10 will only boot from gpt partitioned drives. 

Ubuntu can boot in UEFI mode from MBR, but UEFI highly recommends gpt. We have seen a few users that have a second MBR drive and install Ubuntu in UEFI, but it is using the ESP on the first drive, so booting from gpt, but using MBR for rest of system. Not really recommended, but may work.

---

