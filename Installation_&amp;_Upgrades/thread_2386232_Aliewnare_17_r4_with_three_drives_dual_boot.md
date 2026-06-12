---
title: "Aliewnare 17 r4 with three drives dual boot"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by ihorpoleznov on 2018-03-02
Hello!

I just bought Alienware 17 r4 with three disks (HDD + 2 * SSD). I'd like to install a second operating system - Ubuntu. But with this there are many problems. Is there an instruction how to do this without damaging Windows? For example, [here]("https://www.dell.com/community/General/Dual-booting-Windows-10-and-Ubuntu-17-04-on-NVMe-SSD-Dell/mp/5110984#M915749") is a similar question, but I want to know that such changes will not affect the performance of Windows.

Thanks!

Disk0 - HDD, Disk1 - SSD (with Windows) and Disk2 - SSD (i want install ubuntu here)
[ATTACH=CONFIG]278750[/ATTACH]

---

### Post by oldfred on 2018-03-02
Not sure why disk 0 is shown before the boot drive.
That may cause issues as grub in UEFI boot mode wants to install its boot files into the ESP - efi system partition on drive seen as sda. But it looks like you boot drive may be sdb??

Only use Something Else install option.
Still use only Windows to shrink any NTFS partitions & reboot immediately and run chkdsk on any resize partitions.
Make sure all drives are gpt partitioned.

See link in my signature for more info on UEFI installs.

Also best to manually partition in advance and include an ESP - efi system partition on your drive. It probably will not be used unless you disconnect the other drives when installing. Which also may be the safest way to install.
But UEFI usually forgets UEFI boot entries if a drive is disconnected. But most find Windows, but not necessarily any other systems automatically.

Make sure you have latest UEFI from Alienware and have changed from RAID/Intel SRT to ACHI. Install Windows AHCI driver before change.

 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

