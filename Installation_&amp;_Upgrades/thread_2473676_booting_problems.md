---
title: "booting problems"
date: 2022-04-10
forum: Installation &amp; Upgrades
---

### Post by angent on 2022-04-10
hello
my old disk was frequently spamming me initramfs problems, so i decided to move to new one
i copypasted my 2 ubuntu (20.04) partitions from one disk to another using gparted
it worked well
then i deleted these partitions from old disk, and it stopped booting.
boot-repair diagnosis: [https://paste.ubuntu.com/p/9TNDrjcbtv/](https://paste.ubuntu.com/p/9TNDrjcbtv/)

---

### Post by grahammechanical on 2022-04-10
What disk is the old disk and what disk is the new disk? This is what I see.

#1 An operating system is on sda5 but there are no boot files in sda1

#2 there are boot files in sdb1 but there is no operating system on sdb.

If the boot priority is on sda then the BIOS/UEFI cannot find the boot files to boot the OS on sda. If the boot priority is on sdb then the BIOS/UEFI can find the boot files but the boot files cannot find and OS to boot.

Did you delete the partitions from the wrong disk?

Regards

---

### Post by oldfred on 2022-04-10
I think sdb1 is just the USB live installer or Boot-Repair's disk.

Your mount of the ESP in fstab has different UUID than the UUID of the ESP.
I think you were still booting from the ESP on old drive.

Change ESP entry in fstab to UUID of ESP on sda.
Reboot in UEFI mode and use Boot-Repair to reinstall grub in UEFI boot mode.

---

### Post by tea for one on 2022-04-11
[COLOR="#0000FF"]Line 287[/COLOR] - The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode.

The clue is mentioned in the above line.

As advised by [COLOR="#0000FF"]oldfred [/COLOR] - Reboot in UEFI mode and use Boot-Repair to reinstall grub in UEFI boot mode.

---

