---
title: "Windows 10 UEFI dual boot setup"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by Naxxramas on 2016-10-03
Windows 10 Home 14393.222
ASRock B85M Pro4 2.50
i5-4690
Samsung PC3-12800U 8GBx2
PX-128M5S 1.05
WD10EZEX
SanDisk Ultra II 960GB (plan to buy it)
R9 280X
AOC 2777


I've been googling dual boot which most of them were about MBR/BIOS setup. Forgive me if I brought up the same questions in previous threads. I am thinking of trying Ubuntu 16.04.1 first for hardware compatibility. I have installed Windows 10 as GPT in UEFI mode. Hardware firmware and drivers are updated to latest version. I am currently using Intel's integrated graphics. I will use 280X after Ubuntu installation.

Windows 10 currently occupies about 21.5 GB of my SSD. Applications are installed on OS drive and will install single-player games on HDD. I am planning to purchase a used SanDisk drive which is shown above. It will mainly be used for multiplayer games. I will be gaming recent titles in Windows 10 and the rest for Ubuntu like web browsing, NAS streaming and DOS games or WINE. I'll most likely play classic games in WINE that aren't even fully supported on Windows 10. Fast boot and secure boot are disabled in BIOS and OS. I will not be using hibernation both in Windows 10 and Ubuntu. Unallocated space will be made by shrinking SSD volume in Windows disk management. Ubuntu partitions will be manually set as you see below. I'm not sure what I need to do with other mount points and allocate how much space for it. Btrfs file system will be used instead of ext4.

OS drive: Recovery Partition (450MB), EFI System (100MB), MSR (16MB), C: (118.69GB)
Ubuntu  : / (25GB), swap (4GB), /boot (500MB), /efi (fat32 250MB), /home, /usr, /var, /tmp
efibootmgr (boot loader)

[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)

Dual boot setup is based on the two links above. I'm not sure if it's okay to install Ubuntu using Rufus instead of what the author told to do. I have some additional questions. What is more stable to dual boot - two OS in one drive or separate? Are there any stability issues or Windows 10 running in hibernation? Ubuntu has main partitions in SSD and mount points like /home in HDD - is this ok? Native Linux supported games still performs lower than Windows 10 and when will Ubuntu have better gaming performance in the future?

---

### Post by Bucky Ball on 2016-10-03
Windows 10 can NOT run in hibernation. That will lock the drive and NO OS will have access to it. You should boot to Win and make sure hibernation is OFF prior to installing Ubuntu.

Ubuntu 16.04 installed in UEFI is what you're after? You have a lot of info there, but let's go for this.

You have Win10 on the SSD. Yes, you want both OSs on the SSD as that is fastest. HDD for storage. No need for Rufus. EFI will take care of that. Or should.

Hibernation off, boot to BIOS and switch fast start and secure boot off. Have you created an install disk or USB? That should appear as a boot option and there should be an option with (UEFI) next to it. That's what you want as Win is installed in UEFI so Ubuntu MUST be installed in UEFI.

When you boot from install media that should get you to a list of options. Choose 'Try Ubuntu' and see if that gets you to a desktop. If all good, we can look at installing. Use Windows tools for this, not Ubuntu/Linux ones. There is a disk management tool in Win that can do this from memory. 

To install Ubuntu you want free space so yes, shrink the Win partition and leave free space for Ubuntu. It is a good idea to defragment the Win partition several times prior to shrinking it, preferably with something with a bit more grunt than the default Win defragger, but it will do.

---

### Post by oldfred on 2016-10-03
You can only have one ESP - efi system partition per device or drive.
Do not create separate partitions for system folders, or no /boot, /var etc.
You may want separate /home but then have it on HDD. I keep /home inside / (root) on SSD so configurations are loaded quickly, but have a large /mnt/data partition on HDD where all my data is.

The separate data partition cannot be done during install where /home can be, so data partition is a bit more advanced as you have to create partition with gparted either before or after install (ext4 or NTFS or even two partitions), create mount point like /mnt/data, edit fstab so partition is auto mounted in same place on every reboot and link data folders into /home so system looks & works like all data is on SSD, but data really is on HDD.

In my link below to many more links on UEFI installs, I have links to everydaylinux user. But I will add his newest with SSD & HDD. I would suggest a full backup of Windows before deleting recovery partitions.

I used to always suggest with more than one drive, each system should be on separate drives. But if only one drive is SSD, then better to have both systems on SSD, but configure so all data on HDD for both Windows & Linux.

---

### Post by Naxxramas on 2016-10-04
> **Bucky Ball said:**
> No need for Rufus. EFI will take care of that. Or should.

To install Ubuntu you want free space so yes, shrink the Win partition and leave free space for Ubuntu. It is a good idea to defragment the Win partition several times prior to shrinking it, preferably with something with a bit more grunt than the default Win defragger, but it will do.

What do you mean by EFI will take care of it instead of Rufus? I thought I had to write Ubuntu's disk image to my flash drive using Rufus shown as the link below. The partition scheme will be set as GPT for UEFI. After that reboot to UEFI settings to boot in flash drive. I am going to format my HDD as GPT for better compatibility with the system. Do I defrag it just like you said prior to allocating any space on the drive?

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Naxxramas on 2016-10-04
> **oldfred said:**
> You can only have one ESP - efi system partition per device or drive.
Do not create separate partitions for system folders, or no /boot, /var etc.
You may want separate /home but then have it on HDD. I keep /home inside / (root) on SSD so configurations are loaded quickly, but have a large /mnt/data partition on HDD where all my data is.

The separate data partition cannot be done during install where /home can be, so data partition is a bit more advanced as you have to create partition with gparted either before or after install (ext4 or NTFS or even two partitions), create mount point like /mnt/data, edit fstab so partition is auto mounted in same place on every reboot and link data folders into /home so system looks & works like all data is on SSD, but data really is on HDD.

In my link below to many more links on UEFI installs, I have links to everydaylinux user. But I will add his newest with SSD & HDD. I would suggest a full backup of Windows before deleting recovery partitions.

I used to always suggest with more than one drive, each system should be on separate drives. But if only one drive is SSD, then better to have both systems on SSD, but configure so all data on HDD for both Windows & Linux.

I've been reading your post on UEFI installation. Some new info I've learned are kinda confusing. Do I just create "/", /home and swap as the only partitions in Ubuntu since Windows 10 GPT/UEFI already installed ESP? What is /mnt/data really used for? I don't think I will be using a lot of space in the first place however I thought allocating extra partitions from other drives were very easy just like in Windows. Does it have to be ext4 or NTFS as I want to use Btrfs as file system for majority of the partitions. Is each system on separate drives much stable than two systems in one drive? As for the guide in everydaylinux; Doesn't linux install GRUB loader by default for UEFI then what is the need for efibootmgr? Is the guide up to date?

---

### Post by Bucky Ball on 2016-10-04
Yes, my mistake. I don't use Rufus so got confused. UNetbootin, Universal USB Installer, Rufus are a few you could use to create the bootable USB.

---

### Post by oldfred on 2016-10-04
How you boot install media from UEFI is then how it installs.
If Secure boot is off, you should have two boot options in UEFI for flash drive. UEFI:name and just name(BIOS boot) where name is label or brand of flash drive.

Default install is just / & swap. If a newer user it is easier to use a separate /home as that is set up during install with mount point & correct ownership & permissions. Some advantages to a separate /home is then you can reinstall or upgrade install and use same /home.

Grub automatically installs to drive seen as sda, but I always include both the ESP & bios_grub partition on all drives. So then later drive can be used to have boot files without major restructure to add ESP. UEFI suggests ESP be first partition, but does not have to be. But if formatting new drive easier to add it, and with sizes of new drives 100 to 500MB is not much.

When I first started with Ubuntu, I had XP 10 years ago. I soon added a shared NTFS data partition so I could have Firefox, Thunderbird & photos available in both systems with same data. Then when installing more Linux / partitions, I added a Linux formatted data partition. Over time Linux data partition had more data. And when I shut down XP, I also removed all NTFS partitions.

Is there some reason for BTRFS? Ubuntu uses ext4 as its standard.
Not sure if all issues have been fixed, now older thread.
       BTRFS, not ready for prime time
[URL="http://ubuntuforums.org/showthread.php?t=2111487"]http://ubuntuforums.org/showthread.php?t=2111487
[/URL]
 6-Way File-System Comparison On The Linux 4.1 Kernel
[http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1) 

Newer review:
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-FS-5-Way](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-FS-5-Way)

[URL="http://ubuntuforums.org/showthread.php?t=2111487"]
[/URL]

---

### Post by Naxxramas on 2016-10-05
root 20GB, swap 4GB and /home 5GB. 29 gigabytes in total - is this ok? In your previous posts you mentioned /chkdsk after partition shrink, does this apply to SSDs as well? Last time I ran HD Tune, there weren't any bad sectors however C7 Interface error was found. It wasn't a critical warning though. My HDD is in hibernation mode in Windows 10 before I access it and I had Windows 7 applications installed before clean installing SSD. Anyway I plan to format HDD as GPT partition scheme and allocate 300GB for Windows and leave the rest as free space. I haven't run bad sector tests on HDD for a while. I won't be sharing any files between two operating systems. Currently using chrome but I'll be using firefox in Ubuntu. 

I've wanted to use Btrfs as it said it will replace other file systems in Linux which would mean better performance and reliability. After reading the posts you've linked, I'll just use ext4 as default file system. There are a lot of sites that say Btrfs is very stable however with small userbase and little support, ext4 seem to be the best option &#128542;

---

### Post by oldfred on 2016-10-05
If /home not twice the size of / then keep /home inside /. I use 25GB for / but then have a very large /mnt/data partition with all the user data normally in /home. 

My /home is then just the hidden user settings and very small & easy to back up. I also move a few hidden folders like Firefox & Thunderbird profiles which also can get larger. 

Windows is the one that requires chkdsk after any partition resize. It has to update the PBR - partition boot sector which has start & size of partition.

---

