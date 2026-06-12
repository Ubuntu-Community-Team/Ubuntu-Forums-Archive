---
title: "Dual-boot problem"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by yildiz.a on 2012-03-23
I've a serious problem with my laptop.

I use a dual-boot configuration as Windows 7 & Ubuntu 10.04 LTS.

Today, when I powered on the computer, it has failed to show grub and started to reset BIOS itself.

I've installed Ubuntu 10.04 LTS again alongside Windows 7 and grub appeared but Windows 7 didn't come up on the menu.

After that I used Windows 7 CD to use command prompt and ran "bootrec.exe /fixmbr". Then the machine started with Windows 7 (didn't show grub).

I put Ubuntu 10.04 LTS CD again and tried to install Ubuntu, but no filesystem is shown in the hard disk.

Could you help me about this?

Is it recoverable for Windows part?

Thank you.

---

### Post by oldfred on 2012-03-23
You should not have to reinstall to make repairs. May be best to see your entire configuration. Post link to run of boot_info script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Manual repairs:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by yildiz.a on 2012-03-23
Thank you for your help.

I used boot-repair disk and now grub shows Windows 7.

---

