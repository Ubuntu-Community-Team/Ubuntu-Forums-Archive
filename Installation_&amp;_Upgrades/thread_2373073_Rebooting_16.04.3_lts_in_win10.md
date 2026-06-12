---
title: "Rebooting 16.04.3 lts in win10"
date: 2017-10-02
forum: Installation &amp; Upgrades
---

### Post by maxman2 on 2017-10-02
Sys Intel G640 2.8ghz, 12gb ram, 2TB partitioned HDD.

Installed 16.04 on partition .dev/sda8 ext4, rebooted twice into ubuntu, then reboot only shows win10 or win7. Have run ubuntu boot repair- didn't fix the issue.

Attempted to reinstall 16.04 on same partition but install shows " Root folder not found" - 203gb partition. HDD is device for bootloader.

As I'm new to ubuntu, at a loss how to proceed.

Any help will be appreciated.

---

### Post by oldfred on 2017-10-02
UEFI or BIOS?
What brand/model system?
What video card/chip?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by maxman2 on 2017-10-03
Posted: [Http://paste.ubuntu.com/256668611](Http://paste.ubuntu.com/256668611)

When tried to check just after posting paste indicated url was not available. 

Thank you.

---

### Post by oldfred on 2017-10-03
Too many digits? 
Did you copy & paste the link?

If not there, you can manually copy report to pastebin site, it typically is too large to post here.

---

### Post by ian-weisser on 2017-10-03
Extra 1 at the end of the URL.
Boot-repair's suggested repair seems appropriate. Do it.

---

### Post by oldfred on 2017-10-03
Did Windows do an update & restore its boot loader to MBR.
And if Windows 10 make sure fast start up or always on hibernation is off, or you will not be able to boot Windows from grub nor mount any NTFS read/write.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


That the extended partition does not start on sector boundry is not an issue but the other three partitions should be adjusted. What tool did you use to partition as all modern tools use correct boundaries which are required for SSD or 4K drives. Your drive is a newer 4K drive.
       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by maxman2 on 2017-10-03
1st. extra 1 on paste was / I misread my writing.
Looked at the boot info - partition 1 should show win10, partition 2( I think) should show win7- xp is more a place holder as it's 32bit.
Using easybcd I can see the linux partition but can get it to load when selected, so if I reinstall- why the issue with the root folder??

Thank you

---

### Post by maxman2 on 2017-10-03
Forgot do I need to update the MBR?

Also forgot to mention don't remember what I partition the HDD with too many years ( 3-4 at least) but was probably an older Mini tool version.


Looked thru paste info, suggested boot repair will repair the bootloader, but attempted this a couple days ago and still can't access the linux partition.

---

### Post by ian-weisser on 2017-10-03
> **maxman2 said:**
> so if I reinstall

Do you feel that you need to reinstall?
The repair to the bootloader (using boot-repair) seems quite simple.

If you maintain a dual-boot or multiple-boot environment with Windows, this issue will crop regularly. Keep boot-repair handy.

---

### Post by oldfred on 2017-10-03
Do not know EasyBCD, a few use it.
But EasyBCD uses the very old grub4dos and has to chainload to grub installed into a Partition Boot Sector(PBR), not the MBR (if one drive). But grub2 is much large than the old grub legacy and does not fit into PBR, and it converts to blocklists which are unreliable.

Windows only boots from one primary NTFS partition with the boot flag. If multiple installs of Windows (and newer, so not XP's boot.ini), then Windows updates boot partition with last install's files & BCD and updates BCD to boot other Windows, but will not boot Linux. EasyBCD seems to be a work around.

Grub will boot Windows, but cannot boot hibernated Windows or Windows that needs chkdsk. And Windows 8 or 10 regularly turns on fast start up with its updates, so you have to turn that off before rebooting or have a Windows Repair disk with its repair console.

---

### Post by maxman2 on 2017-10-03
If I understand, trying to run unbuntu on win10 is a continuing problem. Even if an external boot is made on a usb drive - the issue remains?
If I dual boot on another unit with xp 32 bit(which will not have updates to xp) can I expect the win boot loader to overwrite mbr/boot record?

---

### Post by oldfred on 2017-10-03
Older system would not be a problem. And all you need to do is have both a Windows repair flash drive and the Ubuntu live installer as repair disk. You probably should have both of those anyway.

And newer UEFI systems are not a problem as updates may reset Windows to first in boot order, but with UEFI you still have both boot loaders to select from UEFI if grub does not work to boot Windows. Or if Windows has defaulted to first then UEFI still has Ubuntu as boot option.

---

### Post by maxman2 on 2017-10-04
Thank you for your help!

Prefer to stay on win10 pc as newer processor - current HDD formatted mbr. If I convert data to GPT, will I still encounter same problems booting UEFI with Win10 installed?

---

### Post by oldfred on 2017-10-04
It is not particularly easy to convert a Windows BIOS install to UEFI boot. 
Windows only boots from MBR partitioned drives with BIOS and only from gpt partitioned drives with UEFI. So you basically have to convert to gpt and do major updates to Windows.  I have seen where it has been done, but probably better to backup & just reinstall or stay with BIOS/MBR for now.

But if newer processor generally better to always install in UEFI mode with gpt partitioning.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604) 

[https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

