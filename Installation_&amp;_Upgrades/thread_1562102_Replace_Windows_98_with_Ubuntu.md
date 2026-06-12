---
title: "Replace Windows 98 with Ubuntu"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by yetisouth on 2010-08-27
I have a dual boot system with Windows 98 on C:\ (FAT32), and Windows XP pro SP3 on the same drive on a logical partition (it is E:\ the D:\ drive is on the second HDD) formatted in NTFS. Now I want to ditch Win98 by just deleting it, except of course boot.ini ntldr etc. How can I now install Ubuntu into the now empty c:\ drive without screwing up Windows XP. It is my work computer, so I REALLY must not screw it up!
By the way, I also use Paragon Drive Backup with the backup capsule. It changes the MBR to boot into the backup capsule. So, screwing up the MBR is also no option. Can somebody help me - LINUX is TOTALLY new to me.:popcorn:

---

### Post by dv3500ea on 2010-08-27
First make sure your computer meets the [system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for Ubuntu. If not you can always use Xubuntu or Lubuntu which are lighter weight. I'm saying this because a computer that has Win98 on it is may be old with insufficient hardware to run plain Ubuntu.

I will assume you are using Ubuntu, not Xubuntu or another distro.

Get an Ubuntu live CD installer from this page: [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") (it explains how to burn the live CD).

Boot the live CD by inserting it and rebooting. Choose a live session to try out Ubuntu. Go to System -> Administration -> Disk Utility where you should be able to view the partitions on your hard disks. Find the fat32 partition, click on it and take a note of the device (eg. /dev/sda1).

Next, install Ubuntu. This is straightforward until you get to the partitioning. You will need to choose manual partitioning. You should format the partition (identify it by the device path you noted earlier) as ext4 with a mount-point of '/'.

It will be useful if you read the installing section of the [Ubuntu Manual]("http://ubuntu-manual.org/") before doing this.

---

### Post by yetisouth on 2010-08-27
The boot files (boot.ini ntldr ntdetect.com) are on C:\ now, that's where I will install Ubuntu. Does the change from FAR32 to ext4 not mess up the booting into XP? Will it still find the boot files?

---

### Post by dv3500ea on 2010-08-27
I don't know what these boot files are.

When Ubuntu is installed, the GRUB bootloader will be installed which will allow you to select which operating system to boot at startup.

---

