---
title: "Ubuntu 20.04 installation problem"
date: 2020-05-20
forum: Installation &amp; Upgrades
---

### Post by ulissipus on 2020-05-20
Could I have some advice on how to install Ubuntu 20.04 over Windows 10? I have been using Ubuntu for some 15 years and have installed, uninstalled, reinstalled many different editions and flavors of it. Last week I made a clean install of the 20.04 edition in my laptop and it works flawlessly. Now I want to do away with W10 on my desktop and have Ubuntu instead. No dual booting.
But installation always stops and freezes at "Installation Type" screen. Instead of the usual options of what you want to do with Ubuntu, I get a blank, frozen screen. If I try and click on one of the fields, then I get from the background a message "Sorry Ubuntu 20.04 has experienced an internal error etc". The only possible way of moving forward is to turn off the computer, which of course stops the installation process.
My machine is a Dell Inspiron 2530. 
I once got an error message "Install Ubuntu 20.04 is not responding" and the option to "Force Quit" or "Wait". Nothing happened when I waited.
Windows 10 boots with no problem from the USB drive. The USB key is not damaged either.

---

### Post by oldfred on 2020-05-21
Is that new enough to be UEFI or just BIOS.
Have you updated UEFI/BIOS to latest available from Dell?
What video card/chip are you using?

Is hard drive ok.
What does Disks, Smart Status, show - in icon in upper right corner of Disks. It can run lots of tests, but all I know is whether it says drive is good or bad.

---

### Post by ulissipus on 2020-05-21
Thanks for your reply. I am no techie and everything I've read about managing partitions in Windows is so complex and complicated that, for the time being, I will keep Windows 10. I have not yet had the time to go through your advice and suggestions, but I will do it. If I come across a clear, straight to the matter wayof working with partitions, I will certainly do it!
The hard drive is ok, so is the USB key. I think the HD is a bit of mess from the partition point of view: too many, sometimes too small, with repeated characteristics.
Many thanks again.

---

### Post by oldfred on 2020-05-21
Post this to see your partitions from the Live installer's terminal.

sudo parted -l

---

### Post by ulissipus on 2020-05-22
[B]Post this to see your partitions from the Live installer's terminal.
sudo parted -l [/B]

You mean the problem could be with the USB installation DISK? In my ignorance I thought it was 'wrong' reading from the Windows hard disk - and that I would have to dab with its partitions...

---

### Post by oldfred on 2020-05-22
Windows requires some partitions, so you you post your partitions we may be able to suggest which are required & which you may have made.
Of course before any install or major change to system, you need good backups.

---

### Post by ulissipus on 2020-05-22
The partitions in my HD are as follows:

- 500MB - Healthy (EFI System Partition)
- 40MB - Healthy (OEM Partition)
- 750MB - Healthy (Recovery Partition)
- OS ( C: ) - 872.47GB - NFTS - Healthy (Boot, Page File, Crash Dump, Primary Partition)
- 503MB - Healthy (Recovery Partition)
- 48.83GB - Unallocated
- 8.33GB - Healthy (Recovery Partition)

I'm afraid I don't know how to post an image of he HD. As it is, I have not yet found how to manage partitions. I've looked up different methods but I cannot merge, delete, format a partition.

---

### Post by oldfred on 2020-05-22
Those all look like typical Windows UEFI/gpt partitions.

Scroll down about halfway and you see a graphic of Windows partitions.
Vendors often also have additional recovery partition(s).
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

So do not change any Windows required partitions. My one old Dell with Windows said I could remove the Dell recovery after I made the Dell backup.

If just expermenting with Linux, the 48GB unallocated would be ok for / (root). But if later deciding to use it more & save lots of data, especially large media files you will need more space.

---

### Post by ulissipus on 2020-05-25
I've been reading and watching videos in YouTube about partitions & formatting hard disk in order to install Ubuntu but still have come to no conclusion. As I said, I am no techie. I feel paralyzed by fear that I may do something and end up with a pc in which Ubuntu is not installed and does not work with Windows...
 
I have meanwhile downloaded AOMEI Partition Assistant, which gives a more detailed view of the partitions:
Disk 1 - Basic GTP - 931.51GB
Volume 1 - *:ESP - File System: FAT32 - 500MB 
Volume 2 - *: - File system: Unallocated - 40MB - no mount point
volume 3 - *: - File system: other - 128MB - no mount point
Volume 4 - Z:WINRETOOLS - File system: NTFS - 750MB
Volume 5 - C: OS - File system: NTFS - 872.47GB
Volume 6 - *: - File system: NTFS - 503MB
*: - Device name: none - File system: Unallocated - 48.83GB - no mount point
Volume 7 - *:PBR Image - File system: NTFS - 8.33GB

You advise not to change Windows required partitions. But if I don't do something to them (delete, merge, format), then I am stuck: Ubuntu installation will be rejected. 
As I said, I do not want to experiment: I am trying to install Ubuntu as the OS, instead of Windows.

Ideas, suggestions?

---

### Post by CatKiller on 2020-05-25
> **ulissipus said:**
> Now I want to do away with W10 on my desktop and have Ubuntu instead. No dual booting. 

Did you remember to turn off Fast Startup in Windows, and to set the drive access to AHCI in the UEFI setup? Oldfred's suggestion to run *sudo parted -l* from the installer was to make sure that your computer is in the right state to read/write to the hard drive in the installer, which it wouldn't be if either of those things weren't true. I'm sure Windows can read its own partitions fine regardless, so looking at the partitions from Windows isn't that helpful. 

> But installation always stops and freezes at "Installation Type" screen. Instead of the usual options of what you want to do with Ubuntu, I get a blank, frozen screen. If I try and click on one of the fields, then I get from the background a message "Sorry Ubuntu 20.04 has experienced an internal error etc". The only possible way of moving forward is to turn off the computer, which of course stops the installation process.
My machine is a Dell Inspiron 2530. 
I once got an error message "Install Ubuntu 20.04 is not responding" and the option to "Force Quit" or "Wait". Nothing happened when I waited.

The installer crashing isn't necessarily anything to do with the partitioning step, even though that's where it happens. It might just be crashing for some other reason.

---

### Post by oldfred on 2020-05-25
All those partitions are standard & normal. 
Many use Windows to shrink largest NTFS partition and install Ubuntu.

But have you updated UEFI from Dell to latest version.
As CatKiller suggested, these are required.
Are drives set to AHCI, not RAID, nor Intel RST in UEFI settings.
Windows fast start up is off.

No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Dell BIOS recovery 
[https://www.dell.com/support/article/uk/en/ukbsdt1/sln300716/bios-recovery-options-on-a-dell-pc-or-tablet?lang=en](https://www.dell.com/support/article/uk/en/ukbsdt1/sln300716/bios-recovery-options-on-a-dell-pc-or-tablet?lang=en)

---

### Post by CelticWarrior on 2020-05-25
> **oldfred said:**
> All those partitions are standard & normal. 
Many use Windows to shrink largest NTFS partition and install Ubuntu.

But have you updated UEFI from Dell to latest version.
As CatKiller suggested, these are required.
Are drives set to AHCI, not RAID, nor Intel RST in UEFI settings.
Windows fast start up is off.

No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Dell BIOS recovery 
[https://www.dell.com/support/article/uk/en/ukbsdt1/sln300716/bios-recovery-options-on-a-dell-pc-or-tablet?lang=en](https://www.dell.com/support/article/uk/en/ukbsdt1/sln300716/bios-recovery-options-on-a-dell-pc-or-tablet?lang=en)


This is really all you need to know for a dual-boot system (and, of course, boot the installer in UEFI mode). You can use the unallocated portion to install Ubuntu, it's more than enough space. 
If you want to have only Ubuntu it's even easier. No one understand why are you making it so difficult. Just boot the installer in UEFI mode and later select the option "erase and install...". That's all, really. Why are you worried about Windows partitions in this case? It makes sense for dual-booting; it makes no sense at all for installing Ubuntu only.

---

