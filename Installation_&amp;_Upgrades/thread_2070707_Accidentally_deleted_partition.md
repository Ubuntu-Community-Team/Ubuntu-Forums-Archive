---
title: "Accidentally deleted partition"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by robirahman on 2012-10-13
I accidentally deleted the hard disk partition containing Ubuntu in Windows' Disk Manager, and now cannot boot either operating system. When I turn on the computer the following error is displayed:

error: no such partition.
grub rescue>

Does anyone know if it is possible to bypass GRUB and boot Windows? I can create a live CD if it helps. Thanks!

---

### Post by ajgreeny on 2012-10-13
Use a live disk of ubuntu, install testdisk to that and you may be able to restore the partitions back to where they were before.

Whatever you do, do not install anything to the hard disk or do anything else with it other than attempting to restore the old partition table.  If you do you could lose any chance you have of restoration.

PS: I've never used testdisk, but you can find info and more details at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by oldfred on 2012-10-13
ajgreeny's suggestion of testdisk is good if you want to recover Ubuntu.

If you just want to boot Windows :( , You just need to install a Windows or Windows like boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

This also has instructions on downloading as a full repairCD. From it you can install a Windows like boot loader that will boot Windows.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

