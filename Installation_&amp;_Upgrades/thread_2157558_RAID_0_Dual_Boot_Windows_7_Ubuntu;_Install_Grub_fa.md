---
title: "RAID 0 Dual Boot Windows 7 Ubuntu; Install Grub failed"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by 3246251196 on 2013-06-25
[LIST]
[*]More information: AMD64 ; P8Z68-v pro ASUS ; NON-uefi ; 2 * WD 150Gb SATA drives ; ICH8/9/10R SATA RAID controller
[*]I select RAID as the value for "SATA MODE" in the Advanced BIOS menu
[*]I reboot
[*]I intentionally encounter the "Intel Rapid Storage Technology ROM 10.6.0.1091" screen and configure 100% of the available space of the two drives to be RAID 0 and I will now call this logical drive Volume0
[*]I proceed to install Windows 7 as normal
[*]I select more than half of the available space on Volume0 to be allocated to this Windows 7 installation
[*]Windows creates 2 partitions, as by default: SystemReserved (100Mb) and my Windows 7 partition
[*]After customising things etc etc in Windows I reboot, having inserted an Ubuntu Server AMD64 12.04 DVD
[*]Ubuntu boots up and I go through the normal procedure (i have not appended any BOOT options when I boot into the ncurses-type installation screen)
[*]I get to the Partition section of the screen: everything looks find, I see it can see my 300GBish partition: there are the two windows partitions and an unused (FREE SPACE)
[*]I set up a swap partition out of that free space
[*]I set up a root partition out of that free space
[*]I set up a logical boot partition (just because I have been running out of ideas and do not fully understand this) - logical only because I cannot create more than 4 primary partitions on this logical volume
[*]Things install etc etc
[*]I get to the GRUB section of the installation
[*]Where should I install grub to?
[*]I see that "/dev/md" is already selected
[*]I go into shell and see that only a special file: "control" exists in /dev/mapper
[*]I go into /dev/md and see that there are a bunch of ln -s to things such as "/dev/md126", /dev/md126p1, /dev/md126p2 etc etc - even a /dev/md127
[*]I have tried installing GRUB to /dev/md126 and to other partitions like /dev/md126p1 etc , even /dev/md/md126 and /dev/md/md126p1 etc etc
[*]Each time grub fails to install
[/LIST]


[LIST=1]
[*]What is the difference (if any) between /dev/md and /dev/mapper.
[*]Am I using a FAKERAID? The screen "Intel Rapid Storage Technology ROM 10.6.0.1091" would suggest so because of the ROM part which suggests that this is just a bunch of software? I do not know.
[*]**ANSWERED ] **I have used a Software raid before and noticed that I had to use mdadm, is mdadm for SW raids and dmraid for FakeRaids? (EDIT::: [http://us.generation-nt.com/answer/what-difference-between-mdadm-dmraid-help-173289421.html](http://us.generation-nt.com/answer/what-difference-between-mdadm-dmraid-help-173289421.html) )
[*]I like having a /boot partition right at the beginning! I always have. is there anyway to set up RAID 0 with let's say 99% of the total space of the two disks, and have a NON-RAID space left over so that I can have a dedicated /boot partition (I know I could find this out but it would mean removing this Windows installation at the minute) 
(EDIT:: [http://forums.anandtech.com/showpost.php?p=32237489&postcount=11](http://forums.anandtech.com/showpost.php?p=32237489&postcount=11) -- it looks more and more like i really do need a dedicated boot partition of some sort that is NOT part of RAID. If I am able to leave a little bit of space and use 99% capacity for RAID 0, leaving 0.5% on SDA and 0.5% on SDB, I could just do a standard /boot ext4 on sda... - only if this is possible ;;; Or i might just keep a USB stick inserted and use that as /boot)
[*]**ANSWERED ] **does GRUB get installed over-the-top-of the MBR (in the same way that the Windows Boot Loader would?)? Or, does GRUB get installed anywhere and the MBR just points to the GRUB partition? (EDIT::: [http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-difference-between-mbr-and-grub-798042/](http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-difference-between-mbr-and-grub-798042/) )
[*]What can I do in the previous steps to install GRUB.
[/LIST]

Thanks.

---

### Post by 3246251196 on 2013-06-27
Bump for this.

Especially with regards to whether or not I need a separate device JUST for a /boot partition. I have been told that GRUB 2 can deal without the boot partition. But it looks to me like in order to successfully get this dual boot working with RAID 0, I need to have a dedicated /boot partition on a NON-raid device; I am wondering if it is possible - question 4 - to have 99% capacity as RAID 0 on the 2 devices, leaving 0.5% normal on each device and using one of those for a /boot partition.

---

