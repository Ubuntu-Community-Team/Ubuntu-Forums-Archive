---
title: "Partition Confusion Help Me Identify Them"
date: 2020-07-02
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2020-07-02
Hello people. I've got an Acer Aspire One laptop running Ubuntu Budgie. It is dual booted with windos. I want to get rid of Budgie and try the new LTS while keeping the existing windos. 
I used the Discs utility to see the partitions. I can't identify all of them. Here is what I copied:

[COLOR=#000000][FONT=Arial]Name: ESP Partition 1... 105 MB FAT  32-bit-version[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Size 105 MB- 44 MB free[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device /dev/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Type EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Contents FAT(32-bit version) Mounted at /boot/efi[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Name: Partition 2 17 MB Unk…[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Size 17 MB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device /dev/sda2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Type Microsoft Reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Contents Unknown[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Name: Acer Partition 3: Ba… 99 GB NTFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Size 99 GB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device /dev/sda3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Type Basic Data[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Contents NTFS Not Mounted[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Name: Filesystem Partition 5 900 GB Ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device /dev/sda5[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Type Linux Filesystem[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Contents Ext4 (version 1.0) Mounted at Filesystem Root[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Name: Recovery Partition 4 1.1 GB NTFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device /dev/sda4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Type Microsoft Windows Recovery Environment (System)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Contents NTFS Not Mounted[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]


These were typed in the order they appear on the graphic. 4 came after 5. 

We can see that the word Microsoft is listed in partitions 2 and 4. I know that the 900 GB partition is the one I use in Ubuntu Budgie for file storage.
When I installed Budgie it listed the partitions with a slider mechanism that allowed me to shrink the windos partition to around 100 GB. The other big one was for Budgie at 900. Everything else just popped in automatically.

Here partition 3 has 99 GB and partition 1 has 105 GB. One of those two must be for the windos storage. How can I tell which is which? Once that is known, I want to know what the other is. It probably is the Ubuntu Budgie OS and doesn't really need to be that big. 

Another question is what is UUID and why does partition 2 not have one? 

Ultimately I'm wanting to remove the Budgie sections, keep the Microsoft sections, and put the 20.04 LTS in the place where Budgie was. I don't want to lose the windos sections because I don't have a way to prove it was the original OS on this machine. I don't want to pay them for a new version. 

If you understand these things please assist. I would be grateful. [/FONT][/COLOR]

---

### Post by Impavidus on 2020-07-02
Partitions 2 and 4 are indeed Windows related. I don't know their exact functions. Partition 3 is your main Windows partition. That's where most of the system is stored, along with your documents.

Partition 1 is an EFI partition. Note that it's 105 megabytes, not gigabytes. It's there for technical purposes, telling your computer how to find and load an operating system. It's required and shared by Windows and Linux.

Partition 5 is your main Linux partition and the only one used exclusively by Linux.

A UUID is a random number used as an identifier for a filesystem (or for something else). It has no meaning, other than that it must be unique for this computer.

I prefer to have separate partitions for OS and documents, but this is not required.

---

### Post by Smallwheels on 2020-07-02
Thank you Impavidus. Does this mean that I must keep partitions 1-4 to save windos and the only one that can be deleted is 5?

---

### Post by Impavidus on 2020-07-02
Yes. You don't really have to delete it first, as you can tell the installer to format it. Ubuntu Budgie will have put a bootloader in partition 1, but the installer should know how to handle that.

---

### Post by Smallwheels on 2020-07-02
Impavidus I don't understand. I've got a live USB thumb drive ready to go. I gave it a try and like it more than Budgie. When I get to the point where it asks me to either try it or install it what will happen? Will it show me the sectors on the existing drive and give me a choice of where to put the new OS? I know that it should go on the 900 GB partition. Will that be the only section that will be formatted? I know that formatting will erace everything. Can it do that on only one section? Is there a way to cancel the installation before going any farther?

---

### Post by Impavidus on 2020-07-04
I always try before installing, then start the installer from the live session. But it doesn't matter.

The installer doesn't make things very difficult. If it detects your Ubuntu Budgie system, it may propose to replace it. That's the easy option. If you first delete the current Ubuntu Budgie partition, the installer may offer to install Ubuntu alongside Windows, which will put it in the unallocated space that used to be the Ubuntu Budgie partition. Or you can select something else, tell the installer to use partition 4 with mountpoint / and format it. I prefer this manual option as it allows me to use more complex partitioning. Formatting can be done one partition at a time. It doesn't matter how you do it. While you're still at the partitioning screen, you can cancel. After that, the changes get written to the hard drive.

Some people screw up, many others succeed on their first attempt. It isn't really hard. But prepare for a screw-up anyway. Have you created backups of all your important files?

---

### Post by Smallwheels on 2020-07-10
This is good information. Thank you for giving me some insight. 

I looked at the installation again by clicking custom installation. It is using Gparted for creating partitions or altering partitions. 

Here is the message listed as instructions: Select which partition to use across all drives. Selecting "format" will erase ALL data on the selected partition. You mus at least select a Root (/) partition, plus Boot (/boot/efi) partition that is at least 500 MiB and on GPT disk. It is also recommended to select a Swap partition.

Here is what I know. I have a 900 GB partition with the old Budgie. My laptop has 4 GB RAM. I now need to know a few things. How do I create more partitions within this 900 GB space using Gparted? Which format is optimal for speed (ext4, NTFS, FAT32)? How many partitions do I need? In which order must they be created? How do I name them? (Remember there are already four partitions using windos.) How big should each be? Once these are named will the installation software know where to put everything? Is "GPT disk" just the name of Gparted and the disk/partition being utilized? I'm sure this is actually an easy task. I just don't know how to do it. 

Anybody out there with experience, your help with this would be greatly appreciated. I'm going to go to Youtube and try to find some tutorials. I doubt there will be any as specific as I need, but all knowledge is useful. It might help me to ask the right questions. Thank you.

---

### Post by yancek on 2020-07-11
If you want to simply replace the current Ubuntu with a newer version on the same partition, you need to select /dev/sda5 as the root filesystem indicated by the symbol ' / ' in the installer.  If you want more partitions in what is currently sda5, you can use gparted which is on the live usb.  Simply type:  sudo gparted in the terminal land it will open.  Select the resize option then shrink sda5 and create new partitions in the newly created unallocated space.  You already have an EFI partition so the installer should detect that and create a directory there for the Ubuntu EFI boot files.  Not sure about the swap partition as I believe current Ubuntu versions create a swap file.

THe default filesystem for Ubuntu would be ext4.  You can't install Ubuntu (or any Linux) on a proprietary windows filesystem (ntfs, vfat) and expect it to work.

The drive must be a GPT drive as you have windows installed in EFI mode and that only works on GPT drives.  You don't have the 4 partition limitation as a GPT drive can have up to 128 partitions. The order in which they partitions are created doesn't really matter.  Since you seem to be quite new to this process, you might go with the basic install and create only a singly / partition or if you want, also a separate /home or /data partition.

Ubuntu has documentation online explaining in detail how to dual boot UEFI with windows at the link below, much better and more accurate info than you will find on youtub.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Impavidus on 2020-07-11
A GPT disk is a disk with a GUID (globally unique identifier) partition table. This is a hard drive partitioned the modern way and yours is.

The /boot/efi partition will be partition 1. It's already used by Windows and will be shared by both. It's already FAT32. Don't format it, or Windows may not boot.

Other than that you only really need one partition, the root partition, but it can be convenient to use more. I use three partitions: root, swap and home. The swap partition must be about 2-4GB. Much smaller and it won't be useful, much larger doesn't add anything. If you don't create a swap partition, the installer will make a swap file on the root partition, which is also fine. If you don't separate documents and OS, make the root partition everything you've got available. Else, make the root partition about 25GB and use everything else for a data or home partition. That's what I've done. A home partition is used for all user files, including configuration files. You may want to keep some unallocated space on the hard drive for future use.

Unless you've got a very good reason to do otherwise, the root and home partition should be of type ext4. If you want a partition to be accessible from Windows too, it must be ntfs, but root and home cannot be ntfs, so you can never share them with Windows. If you want to share data between Ubuntu and Windows, make sure you've got an ntfs partition for that, separate from the Windows OS partition. You can call it a data partition in Ubuntu, Windows will call it D: or E: or something like that. Gparted has a simple GUI to create, delete, resize or move partitions. Shrinking or moving the left edge of a partition is very slow, so if the partition has no valuable data, it's better to delete it and create a new one.

It doesn't matter in which order you create partitions. Maybe easiest to create them left to right, as they will be numbered left to right. Labels don't matter, just use something that makes sense to you. When you tell the installer to use a partition, you have to give it a mountpoint, which indicates how it will be used: /boot/efi for the efi partition, / for the root partition, /home for the home partition and a few other options. If the mountpoint where you want to use the partition isn't on the list, leave it unused. This can be fixed after installation.

---

### Post by oldfred on 2020-07-11
Always boot in UEFI boot mode.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If modifying size of NTFS partitions best to only use Windows tools. While gparted often can change NTFS partitions when there is an issue users blame Linux. Issue in most cases would have also occurred with Windows.
General rule - Windows tools for Windows & Linux tools for Linux.

If instructions you are using mention 4 primary partition limit those are now very old BIOS/MBR instructions. Microsoft has required vendors to install in UEFI/gpt since Windows 8 released in 2012.

Details on Windows partitions, if interested.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

The ESP - efi system partition is shared by both Windows & Ubuntu. The 100MB is not generous, but will work for dual booting. But some boot loaders other than grub2, like POP!OS  which uses systemd boot,  need larger ESP, so if starting totally over a larger ESP is suggested.

---

### Post by Smallwheels on 2020-07-25
I found a video that explained root, swap, primary, boot, and a few others. Notes were taken. It showed the purpose of each type of partition and how to create them using Gparted. I went into the live USB and tried working with the largest partition and dividing it. That failed. The program wouldn't give me the choice to divide it. 
The tutorial video wasn't very old. So perhaps the tutorial had outdated information. 

While seeking tutorials, another video was found. It was about how somebody had given up Windoz for a GNU/Linux distro. It was inspiring. When I went to do a clean installation with just GNU/Linux it failed.
It got to 70% and failed. The existing partitions and Windoz OS were gone. Upon restarting there were no boot loaders so the laptop just grabbed the live USB and booted into it. I tried again and got the same error message. Fortunately I created a Windoz recovery drive. All that could be done was to insert the recovery drive and see if it would work. It did. It took a long time but now the HDD is 100% Windoz 10... again. :( At least this starting point should make it easier to dual boot the computer or do a clean installation. By the way, the check sum was checked and it was an uncorrupted live version. Holy cow. I'm actually grateful that Microsoft created a way to save a computer for us ignorant people.

---

### Post by oldfred on 2020-07-25
Only if doing a server install or encrypted entire drive with LVM may you need /boot.
And installer now uses a swap file, so separate swap partition not required.
With UEFI systems the ESP - efi system partition (shared with Windows if dual booting) and / (root) are all you need. 
Do not over complicate it.
If a bit more advanced you can add a separate /home partition, but additional partitions add complexity and more effort maintaining system use.

If Windows has its fast startup or hibernation on, that will cause issues.

Some have issues with one flash drive, one download, one particular port on system and various issues that we cannot confirm but they report. When they change or redo then it works.

Some systems also need boot parameters to work.
Acer are almost identical across all models.
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by pbear42 on 2020-07-25
> **Smallwheels said:**
> I went into the live USB and tried working with the largest partition and dividing it. That failed. The program wouldn't give me the choice to divide it.
Sounds like you misunderstood the tutorial (or it's spectacularly wrong).  GParted doesn't *divide* partitions, and never did.  Rather, as mentioned by someone upthread, you shrink the partition, which can take a long time, then create new ones in the newly-freed space.

Also, sounds like you restored the pre-Budgie Windows system.  If so, heed **oldfred's** advice to use Windows tools to shrink the Windows partition (right-click Start and select Disk Management), then use GParted to create the new ones for Ubuntu.  I prefer to complete all partition work before running the installer.

---

