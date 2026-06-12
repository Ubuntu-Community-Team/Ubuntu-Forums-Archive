---
title: "Problem installing Ubuntu on Dell E7440"
date: 2024-07-20
forum: Installation &amp; Upgrades
---

### Post by ulfholt on 2024-07-20
I have been playing around with Ubunto for some years, never to become an expert, since most of the programs I am running are based on Microsoft. I have a Dell Latitude E7440 which I have been using for a frustraing time with version 22.04. Problem is that Ubuntu crash with no kind of warning, and I am not able to install 24.04 from a USB drive (getting information: Cannoft find a file medium containing a live file system) and if I try to update using the network, the system will turn off, and I am not able to boot or to reinstall. Had to put the disk into a windows machin and use diskpart to clean the disk. I was then able to reinstall 22.04 using the USB-drive. I first tried 24.04 but got same message as before. I tried other versions of Linux, but same problem, so for me it looks like the disk is screwed up in some way or another. 

I have use Dell hardware checking, and no errors found.

Can someone help me find a solution. Please remeber I am not an expert, though I usually find my way around - have been working with computers on several different platforms since 1987, though I am retired now (76 years)

Best regards

Ulf H.

---

### Post by oldfred on 2024-07-20
Dell typically has worked better than many other systems. But most can have Ubuntu installed with some settings.

Are you installing in UEFI boot mode to gpt partitioned drive?
And have at least ESP & / although with larger drive separate /home or data partition may be somewhat better.

Have you updated UEFI & SSD firmware to latest available?
Compare to vendors's support site
sudo dmidecode -s bios-version
udisksctl status

Dell typically needs UEFI update, if SSD also SSD firmware update. 
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). 

Dell issues often common across many similar models.
Dell 7490 Intel RST issues Inspiron does not work, Latitude does.
[https://askubuntu.com/questions/1204648/install-ubuntu-on-dell-inspiron-14-7490](https://askubuntu.com/questions/1204648/install-ubuntu-on-dell-inspiron-14-7490)
[https://ubuntuforums.org/showthread.php?t=2462146](https://ubuntuforums.org/showthread.php?t=2462146)
[https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true#M17730](https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true#M17730)

---

