---
title: "ubuntu 22.04. boot fails after GRUB Menu"
date: 2024-01-26
forum: Installation &amp; Upgrades
---

### Post by luisvls on 2024-01-26
Hi Everybody,

PROBLEM:
The boot on my ubuntu 22.04 computer does not work anymore. When I boot up, I see the GRUB menu, where I can enter the UEFI or change to 'advanced Ubuntu'. But after passing this stage, the monitor simply freezes when it shows "Ubuntu" and its logo. Although this is a very pleasant view, I'd rather have my working desktop/terminal environment. 

BACKGROUND:
Since weeks, the Computer needs a fsck on /dev/sda2/ sometimes when I was rebooting it. For a matter of fact, some months ago, I wiped the hard disk and reinstalled Ubuntu (upgrade from 18 to 22) to get rid of the same problem. The problem being manual fsck from time to time and culminating in failed start up during boot. 
A probably irrelevant aspect: the broken start up was observed after a messed up/failed conda installation. Not sure if or how conda envs can affect boot-ability of an ubuntu computer.

I would appreciate any help, since the wiping/reset-up of ubuntu was obviously not a solution.

Cheers

foly93

the pastebin address:

[https://paste.ubuntu.com/p/cBWT8p7Mw6/](https://paste.ubuntu.com/p/cBWT8p7Mw6/)

---

### Post by yancek on 2024-01-26
Your boot repair show you have an EFI install with the EFI partition on sda1.  It also shows 2 separate installs of Ubuntu 22.04 (sda2 and sdb3).  sdb2 looks like an EFI partition as it is a vfat filesystem but boot repair shows the partition is empty.  You said you reinstalled but you have 2 separate installs.  Is that what you meant to do?  They are on different drives so you could easily boot either from the BIOS if you installed Grub from sdb3 to the EFI on device sdb.

Which Ubuntu are you booting, do you know?  If you are having to run fsck, the physical drive may be bad and need to be replaced but we can't advise as we don't know which drive you are booting from.

---

### Post by luisvls on 2024-01-26
I think I might installed Ubuntu twice, when I "fixed" it last time. So therefore there are two Ubuntu Distributions. I am booting from sda2, sdb3 was an older Installation that I Just did for Data Recovery after the First Booting Problem emerged. I am using IT for Data Recovery again right now, since I can mount sda2. I also think that a physical Problem is present at the sda2 Drive. I am gonna Exchange it I guess.

Thanks for your Help,

---

### Post by oldfred on 2024-01-26
Did you check drive's status with smartstatus?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)

[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)
sudo apt-get install smartmontools
sudo parted -l ## to identify the internal harddrive, here shown as 'sda'
sudo smartctl -t long /dev/sda
sudo smartctl -a -d ata /dev/sda ## To display detailed SMART information

I notice you have only ESP & / (root) on a 6TiB drive.
Years ago there were issues with boot files beyond 2TB, but I think those have been resolved. Back then it did not always appear as intial install may have files inside 2TB, but update put then further into drive.

But we still typically do not suggest very large / partitions. Better to keep / relatively small. I used to suggest less than 30GB but now with snaps and more larger apps, 50 to 60 is probably the minimum. I use Kubuntu and do not have any snaps and df -h shows I am using 15GB of 30GB in /. I have all data in separate partitions. Default install using entire drive goes back to years ago when drives were a lot smaller. Or dual boot where sharing drive with Windows, so only root partition would not be huge.

---

