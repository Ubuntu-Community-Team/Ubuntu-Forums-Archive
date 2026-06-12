---
title: "Partitions for windows dual boot"
date: 2023-03-21
forum: Installation &amp; Upgrades
---

### Post by skywalker007 on 2023-03-21
This whole question is basically... how do I partition my disc in ubuntu to get a second bootable partition and install windows on the second partition?

I just started ubuntu, the reason for that was that the windows system on it was such a mess with so many errors that I could for practical purposes not use it.
So currently I have 22.10 newly installed on a 1 TB SSD. Now I would like to install windows as well again as I do have one or two programs that I need to get back. The disc is not partitioned at the moment.

Just some very basic questions but as they cover the same thing I want to do, I think putting them like this will help a lot.
I suppose the steps I need to go through is the following: 
1. How do I partition the disc now on ubuntu so that I can have another primary bootable partition for windows. 
2. I suppose windows will format the partition it is going to use automatically prior to the installation of the OS or do I need to format this partition myself prior to starting this process?
3. If I afterwards have a bootable flashdrive with windows, how do I install it so that it specifically uses that partition I just created for windows. I suppose if I just let it install it is going to use the C drive and simply overwrite ubuntu... or am I totally wrong in saying this.

It is just that I have never done this before. I know when I just wanted to install ubuntu on day one, it asked me if I wanted a dual boot but I said no, as windows was useless on my system anyway.

---

### Post by tea for one on 2023-03-21
Did you install Ubuntu 22.10 in UEFI mode?
In order to check:-
Boot into Ubuntu
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
What is the output?

---

### Post by oldfred on 2023-03-21
If your computer is less than 10 years old it is UEFI as Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives with release of Windows 8 in 2012. Many vendors called UEFI systems as BIOS, even though actually UEFI.

Windows only installs in BIOS mode to MBR(msdos) partitioned drives. It normally uses a boot partition and an install partition. Boot partition not required, but whichever partition has boot files must be primary.

Windows only boots in UEFI boot mode from gpt(GUID) partitioned drives. And it wants a lot of partitions.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Both systems must be in same boot if on same drive, and should be if on separate drives.
How you boot install media UEFI or BIOS, is then how it installs. That is a choice you make when you choose the install media in UEFI/BIOS boot menu.
Boot mode setting in UEFI settings is only for installed system once you reboot after installing. If UEFI Secure Boot is on, then you do not have BIOS/Legacy/CSM boot mode. 

Very new systems are UEFI only, starting with some vendors in 2020.
I believe Windows 11 default is UEFI only.

---

### Post by skywalker007 on 2023-03-21
OK, so I did check and yes it is UEFI. So if I want to install a windows OS as well, can I just then install it from the bootable flash drive and then I will have a dual boot option when I start.

---

### Post by tea for one on 2023-03-21
oldfred reminded me in post 3, the partition table needs to be gpt for Windows 10/11.

You can check via the terminal with:-
```
sudo parted -l
```

---

### Post by skywalker007 on 2023-03-21
The reply to that command

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4

---

### Post by oldfred on 2023-03-21
Shrink your ext4 partition with gparted to make unallocated space and let Windows add whatever partitions it wants into that space.
Windows does not correctly see ext4 partitions. It should just install to unallocated space, but have good backups in case it just erases drive.

---

### Post by tea for one on 2023-03-21
> **skywalker007 said:**
> The reply to that command

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4

Is your partition table gpt?
You omitted the info. from the terminal command.

---

### Post by Impavidus on 2023-03-21
Partitions can be changed with gparted. You have to use a live disk. You cannot change a partition where the running OS is installed.

---

### Post by skywalker007 on 2023-03-21
Hi

So can I just partition the ext4 disc with gparted and then install windows. Ideally windows will install on the open part of the partition.

Thanks
Johan

---

### Post by yancek on 2023-03-22
>  So can I just partition the ext4 disc with gparted and then install  windows. Ideally windows will install on the open part of the partition.


Yes.  Use GParted on the 'live' USB of Ubuntu to shrink the ext4 partition(s) to create unallocated space.  When you boot the windows installer, immediately after the licensing agreement page for windows, you will see install options and select the Custom option which allows you to select a specific partition or unallocated space.

---

### Post by MAFoElffen on 2023-03-22
> **skywalker007 said:**
> So can I just partition the ext4 disc with gparted and then install windows. Ideally windows will install on the open part of the partition.
Sort of. Let me reword what you said so things are clearer. And remind you what others have told you...

1.) Boot off of an Ubuntu LiveUSB to use GParted off of it. Why? Because you cannot shrink a root partition while it is booted off of it, because it needs to be unmounted during the shrink process... You can resize/shrink the partition(s) of the drive, when you are booted from the LiveUSB. That drive will be unmounted.

2.) You do not need to add a partition for Windows to install to. You 'can' (look at the references links below) but you do not need to... You can leave the unallocated space just as is. The Windows Installer media will see the unallocated space on the drive, and suggest that you can install Windows to that unallocated space.

3.) If you do add a new partition, then you would need to know how Windows see's that, and know if you needs to allow space for it's reserved system partitions... to point the Windows Installer to, to install to it. (Also refer to the reference links below) Easier to leave it unallocated, and let the Windows installer figure out what it needs to partition in the unallocated space (for it's reserved system partitions and such).

4.) It already has an EFI partition, which it will share with Ubuntu...

RE:
[https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11)
[https://pureinfotech.com/install-windows-11-custom-partition/](https://pureinfotech.com/install-windows-11-custom-partition/)

Note: Be aware that Windows needs some of those other partitions to be able to recover from, after a Windows update causes a system crash, to prompt you to do a Windows boot repair or system rollback... 

Does that make more sense now?

---

