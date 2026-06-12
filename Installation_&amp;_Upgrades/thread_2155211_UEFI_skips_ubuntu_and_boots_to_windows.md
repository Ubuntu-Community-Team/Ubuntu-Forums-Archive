---
title: "UEFI skips ubuntu and boots to windows"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by Atomic_kemo on 2013-06-17
I installed Ubuntu 13.04 with Windows 8 in UEFI mode
I created "/" partition, there was the widows efi partition so I didn't create one, I chose to install the bootloader on the efi partition
After restarting Windows boots normally
I restarted again and found Ubuntu in boot menu, but when I select to boot Ubuntu it loads Windows.

---

### Post by Atomic_kemo on 2013-06-17
I installed Ubuntu 13.04 with Windows 8 in UEFI mode
I created "/" partition, there was the widows efi partition so I didn't  create one, I chose to install the bootloader on the efi partition
After restarting Windows boots normally
I restarted again and found Ubuntu in boot menu, but when I select to boot Ubuntu it loads Windows.

---

### Post by TNFrank on 2013-06-17
Windows 8 with it's UEFI bios gave me all kinds of problems trying to install Ubuntu using wubi and I couldn't even over write Win8 and just install Ubuntu because of the UEFI that basically blocks the deletion of the Win8 Op Sys.  I finally just gave up and returned the Windows 8 computer for a full refund and picked up a couple Win7 machines and had zero problems over writing the Win7 OS with Ubuntu 12.04.  I'm sure someone here knows a few tips or tricks for getting Linux to work side by side with Windows 8 but IMHO it's pretty tricky.

---

### Post by fantab on 2013-06-17
I think you have to choose Ubuntu EFI/Grub EFI from the BIOS/UEFI, which should give you a Grub menu to boot either boot Windows or Ubuntu. Check your BIOS/UEFI to enable this.

If this doesn't help then you can use [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") utility. Run the utility and choose '***Recommended Repair***', and it that doesn't help then from boot-repair first run '***BootInfo Summary***' and post the link it generates here.

---

### Post by oldfred on 2013-06-18
Threads merged. Please do not create duplicate threads.

---

### Post by Atomic_kemo on 2013-06-18
Without reinstalling:
1) Disabled secure boot
2) Booted Ubuntu
3) Boot-repair
4) Booted Windows

everything works

sorry about the duplicate threads

---

