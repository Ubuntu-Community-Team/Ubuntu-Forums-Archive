---
title: "Classic dual boot problem, only Windows 11 boot"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by neosoyo on 2024-10-29
Hi there, i'm switching from Pop-OS to Ubuntu, i tried install it on the same partition that Pop-OS uses, maintaining the /home partition

Now only Windows is detected to boot, i guess i've messed up with /boot/ partition?


[https://paste.ubuntu.com/p/X7RgCKyhH4/](https://paste.ubuntu.com/p/X7RgCKyhH4/)

I'm not worried with the ubuntu installation, i can repeat the process if partitions are wrong.

thanks for the help,
saulo

---

### Post by grahammechanical on 2024-10-29
It seems that you have two EFI System Partitions (ESP) Which is not good. It should not happen.

> nvme0n1p1       2048     206847     204800   100M EFI System
nvme0n1p5 2457837568 2459885567    2048000  1000M EFI System

confirmation

> 1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
5:1258GB:1259GB:1049MB::BOOTEFI:boot, esp;

When we install Ubuntu we tell the installer where to put the boot files. They should go in the EFI System Partition. Which I am suggesting should be nvme0n1p1. Both Windows boot file and Ubuntu boot files can exist side by side in the EFI System Partition without problems.

You can re-install Ubuntu or you can try using the UEFI settings utility boot manager section to select nvme0n1p5 which may or may not load Ubuntu. If Ubuntu loads you can run

```
sudo update-grub
sudo grub-install /dev/nvme0n1p1
```

That might put the Ubuntu boot files in the correct EFI System Partition. You can then use GParted from a Ubuntu live session to remove nvme0n1p5. The size is far to big anyway - 1000MB.

Regards

---

