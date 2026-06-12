---
title: "Resize system partition and transfer from MBR to UEFI without reinstall - Ubuntu"
date: 2020-07-30
forum: Installation &amp; Upgrades
---

### Post by mshotlekov on 2020-07-30
Hello all! I'm using dual boot Windows 10 + Ubuntu 20.04. Actually I'm only using Ubuntu, but as I bought my PC with Windows pre-intalled it's still there. I really do not need MS OS, so I want to remove it, because it is occupying 160 GB of HDD. Beside that the PC is UEFI capable, but Windows is installed in MBR, so is the Ubuntu in order to be able to use dual-boot. So what I'm asking is if there is possibility to remove Windows, to merge Linux and Windows partitions and transfer from MBR to UEFI without need of reinstall Linux?!

---

### Post by CelticWarrior on 2020-07-30
Welcome.

Backing up and reinstalling is really really faster and much safer than all the things you want to do.

---

### Post by pbear42 on 2020-07-30
Agreed.  It can be done.  I have done it, as a demo on a test system.  But it's complicated.  Perhaps the most complicated part is reinstalling Grub, as the current system is missing a couple of image directories in /usr/lib/grub.  Consequently, grub-install will insist it's an MBR installation (even though you have booted in UEFI) and demand a BIOS boot partition.

If what I just wrote makes perfect sense and you'd like details, I can do that.  Honest, though, reinstall will be easier and faster.

---

### Post by grahammechanical on 2020-07-31
The difference is between UEFI boot and Legacy boot and then between MBR (Master Boot Record) partitioning GPT (GUID Partition table).

If Windows 10 was installed in UEFI mode then Ubuntu must also be installed in UEFI mode. Otherwise, you will have difficulty dial booting. I am not sure if Windows 10 when preinstalled would be installed in Legacy boot mode.

Now it is possible to convert an MBR formatted drive to a GPT formatted drive without losing the OS. How easy this is and how successful, I cannot say.

[https://itectec.com/ubuntu/ubuntu-how-to-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from-efi/](https://itectec.com/ubuntu/ubuntu-how-to-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from-efi/)

I have two drives. One MBR formatted and one GPT formatted and I can successfully boot between different versions of Ubuntu on each drive.

We partition drives from a Ubuntu live session using Gparted. That will let you delete the Windows partitions and in the process remove Windows 10. You can then move, expand the Ubuntu partition or create new partitions to use the unallocated space.

[https://gparted.org/display-doc.php?name=help-manual](https://gparted.org/display-doc.php?name=help-manual)

Regards

---

