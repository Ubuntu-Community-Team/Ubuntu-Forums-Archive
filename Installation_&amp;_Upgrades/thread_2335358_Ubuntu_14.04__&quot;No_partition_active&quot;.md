---
title: "Ubuntu 14.04  &quot;No partition active&quot;"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by danieljf24 on 2016-08-27
I installed only ubuntu 14.04 system on my computer (4T disk). As something wrong happened with the power supply, I cannot enter into the system when I restart the system.
It prompt " No partition active    Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".

I tried to fix by "lilo" and "boot-repair" tool, but it still not work.
The "boot-repair" returned info is post in   [http://paste.ubuntu.com/23100635/](http://paste.ubuntu.com/23100635/)

Thanks in advance for your kind help.

---

### Post by mook765 on 2016-08-28
You installed Ubuntu in CSM-mode (legacy-mode)
Your hard-disk has a capacity of 4 GB.
To be able to access the whole drive you must install in UEFI-mode.
You can  use Boot-Repair to solve this, but you have to create ESP-partition first.
Your Partitions are pretty big, this is not necessary, 40 GB for Ubuntu are more then generous.
34 GB for swap is a lot too, but if you want you can do.
To convert your install to UEFI, please refer to [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")
If you want to do a new install you have do boot the installation-media in UEFI-mode.
If you want to use Boot-Repair to help you, you have to boot Boot-Repair in UEFI-mode too, but you have to create ESP-partition first.
If you want to prepare partitions with gParted from your Live-CD/USB you have to boot in UEFI-mode.
You may delete the "Bios Boot Partition" (sda1) this partition is not needed.

---

### Post by oldfred on 2016-08-28
You can boot in BIOS mode from gpt partitioned drives.

But not sure if Lilo will even work with gpt. Lilo is a Windows type boot loader and wants to see a boot flag, which in Windows is the active partition. But with gpt the boot flag is used to assign the very long GUID to indicate to UEFI that a partition is the ESP - efi system partition. Definition of boot flag partition then is totally different between MBR and gpt.

If you are booting in BIOS mode you will need bios_grub partition which is for the BIOS version of grub on gpt partitioned drives.

If you run Boot-Repair's fixes make sure Internet is working, best if hardwire Ethernet, not wireless. You should use the advanced mode and do a full uninstall/reinstall of the BIOS version of grub or grub-pc and include latest kernel as part of reinstall.

---

