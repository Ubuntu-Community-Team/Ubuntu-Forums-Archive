---
title: "Boot-repair problem installing Ubuntu 22.04"
date: 2023-03-27
forum: Installation &amp; Upgrades
---

### Post by jlbarros15 on 2023-03-27
Hello! I hope someone can help me.

My PC has three hard disks:
[LIST=1]
[*] A 960 GB SSD with Windows 10
[*]A  2 TB one for Data
[*]A 1 TB one where Ubuntu 18.04 was installed
[/LIST]

Everything was working fine until I decided to install Ubuntu 22.04.

I used Live USB to install Ubuntu 22.04 with the "Erase Disk" option. I customized the 1TB drive partitions but they didn't work. When starting it sends me to grub rescue. I don't know how to use that tool.
I used boot-repair but it didn't work.

This is the summary of boot-repair: [https://paste.ubuntu.com/p/PxMfbxd9v7]("https://paste.ubuntu.com/p/PxMfbxd9v7/")

Thanks for any help
Jose Barros

---

### Post by oldfred on 2023-03-27
You have mixed up UEFI & BIOS.
And you have some drives as MBR(msdos) and one as gpt.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.
I  started converting new/reformatted drives to gpt in 2010 with BIOS only system.
The only reason to use MBR is if an old system and you need Windows. And Windows now does not really work on those old systems.
BIOS/MBR was allowed only since some large users wanted newer Windows but be able to install to many older systems also. Many new systems now are UEFI only.
Ubuntu also lets you use MBR with UEFI boot, and should not as you get into these kind of issues.

Conversion from MBR to gpt normally erases system. So you have to have good backups.

If sda is new install with not much data, I would convert to gpt & reinstall.
You need an ESP - efi system partition with gpt partitioning. 

Long term I would plan on converting sdb to gpt, but that is not essential, but gpt has some advantages.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

