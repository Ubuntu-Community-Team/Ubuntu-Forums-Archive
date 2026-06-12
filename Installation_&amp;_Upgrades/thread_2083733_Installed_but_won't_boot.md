---
title: "Installed but won't boot"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by ELD on 2012-11-13
I have installed Ubuntu on my new pc but when booting i get this:

"Reboot and select proper boot device"

---

### Post by dannyboy79 on 2012-11-13
your bios is not pointing at a boot device. do you have more then 1 hard drive? During the install, where did you install grub2 to? Which version of Ubuntu did you install? You may be able to fix this using Boot Repair CD, download iso and burn it to a disk.

---

### Post by ELD on 2012-11-13
Only 1 hard drive, installed grub2 to the hard drive. Ubuntu 12.10.

---

### Post by oldfred on 2012-11-13
You can just add Boot-Repair as suggested by dannyboy79 to your Ubuntu liveCD or USB flash drive. It is installable in many liveCDs or is a full repair ISO.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by ELD on 2012-11-14
Managed to fix it by re-installing and getting the installer just to do partitions for me, i must have missed something :)

---

