---
title: "Ubuntu Server 20.04 LTS - Boot Repair - Lost windows boot"
date: 2022-06-10
forum: Installation &amp; Upgrades
---

### Post by cicero8 on 2022-06-10
Hi,

I purchased a thinkcenter M70q ([https://tinyurl.com/m5h48emh](https://tinyurl.com/m5h48emh)) that came pre-isntalled with windows 10 Pro.

Afterwards, I purchased a 32GB Flash Drive and a 500GB Samsung External SSD, and connected the SSD via USB 3.2 Gen 2.

I created a bootable ubuntu flash drive using etcher.

Then installed ubuntu server 20.04 LTS:
- when performing the install I had two choices for drives (one marked Samsung, and another that was bassicly gibrish (a bunch of numbers which I identified as the internal drive)), I selected the one marked as samsung
- I unselected the LVM option, and kept the rest of the settings at their "default" value

Result:
[LIST]
[*]**lsblk**
[LIST]
[*]SDA/SDA1 (465.8GB)
[*]nvme0n1/nvme0n1p1 (1GB)
[*]nvme0n1/nvme0n1p2 (475.9GB)
[/LIST]

[*]**sudo fdisk -l /dev/sda**
[LIST]
[*]disklabel type : dos
[/LIST]

[*]**sudo fdisk -l /dev/nvme0n1**
[LIST]
[*]disklabel type : gpt
[/LIST]
[/LIST]
From what I can gather it seems to have created a 1GB partition on my internal drive for the OS, and ignored my request to use the external drive (hindsight 20/20, I probably should have removed the internal drive?)
I also can't seem to see the windows partition on the internal drive which existested for the windows OS

[B]Fixing using boot repair:

[/B]BootInfo Summary : [https://paste.ubuntu.com/p/QhCTH43V6h/](https://paste.ubuntu.com/p/QhCTH43V6h/)

**Should I try to run recommended repair? **I'm a bit worried, I don't have the windows 10 pro product key, as it came pre-installed on this server...

Ideally, I want to be able to boot either windows or ubuntu, and I would prefer not to have to purchase a new windows 10 pro product key. 

Edit: 
Turns out the drive inside my thinkcenter is also a samsung 500GB SSD lol. I'm pretty sure I ended up reformating the entire drive and loosing windows. Not the end of the world in my case, but definitely a good lesson lol.

---

### Post by oldfred on 2022-06-10
UEFI systems have the Microsoft product key in the UEFI. So no new key required.
You can download the Microsoft ISO and create an install flash drive. Its more difficult to create a Windows flash drive from Linux as Microsoft has made its .wim file over 4GB which then does not fit on a FAT32 partition. And you have to use FAT32 for UEFI installs. The Microsoft tools automatically split the .wim file to make it work.

Also installs to any second drive where you want to separately boot that drive, particularly external drives, must be aware of this bug. Old but they do not seem to want to fix it. Many work arounds posted in bug report. You can often in UEFI disable a NVMe drive so as if you unplugged it. Or remove ESP's boot flag. Best to partition in advance using gpt (not MBR/msdos) to make sure you have an ESP on external drive. If external drive only drive seen, auto install options will then work.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Windows needs multiple partitions, so erase drive & let Windows create the partitions it wants.
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

[https://askubuntu.com/questions/1274878/make-windows-10-bootable-usb-in-ubuntu](https://askubuntu.com/questions/1274878/make-windows-10-bootable-usb-in-ubuntu)
[https://askubuntu.com/questions/1359706/my-toshiba-laptop-wont-read-my-windows-10-boot-disk/1359829#1359829](https://askubuntu.com/questions/1359706/my-toshiba-laptop-wont-read-my-windows-10-boot-disk/1359829#1359829)
Split .wim with Linux tools.
[https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html](https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html)
The .wim too large, Windows commands to split
[https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en](https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en)
Split .wim
[https://ubuntuforums.org/showthread.php?t=2468464](https://ubuntuforums.org/showthread.php?t=2468464)
Create installer
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.57809194.1251095709.1512369991-1898146045.1512369991#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.57809194.1251095709.1512369991-1898146045.1512369991#0)

---

