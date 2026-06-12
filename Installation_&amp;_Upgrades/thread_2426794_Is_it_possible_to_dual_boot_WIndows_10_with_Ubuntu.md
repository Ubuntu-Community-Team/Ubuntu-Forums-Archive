---
title: "Is it possible to dual boot WIndows 10 with Ubuntu?"
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by angel-cake on 2019-09-13
Hello, I have Ubuntu 19.04 as my OS on my laptop. I used to have Windows 10 as my main OS and Ubuntu as a partition, however a problem with my hard disk occurred that made me unable to access Windows and decided to install Ubuntu as the definitive OS. 
So far, I have gotten used to Ubuntu, but I want to have Windows 10 as a partition because I don't want to stop completely using Windows.
Is it possible to install Windows 10 as a partition, having Ubuntu as my main OS? I have googled for solutions, but all I see is the other way around, so I came here looking for a slight chance of hope. [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] 
Btw, my laptop is of 64-bit architecture.

---

### Post by oldfred on 2019-09-13
UEFI or BIOS? 
Major differences, depending on type of system  & how Ubuntu is installed.
Post this:
sudo parted -l

If hardware is UEFI, easier to dual boot newer Windows in UEFI mode. Only Windows 7 worked reasonably well with BIOS. 
Issues with Windows 10 in BIOS mode are the fast start up which is always on hibernation. You also have the old MBR(msdos) partitions (Windows 7 may also). 

Either way you want both a Windows repair disk & Ubuntu live installer to be able to make repairs, or restore boot loaders.

Windows 10 typically wants lots of partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by angel-cake on 2019-09-13
hello, the result of sudo parted -l is this:

```
Model: ATA WDC WD2500BEVT-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary               boot, lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1028MB  1028MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 249GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  249GB  249GB  ext4

```
And hardware is BIOS

---

### Post by TheFu on 2019-09-13
BTW, Ubuntu 18.10 support ended 2 months ago. If it has internet access, expect to be hacked. There have been a number security fixes since then that aren't in that release.

If you want more than 9 months of support from release, stay with LTS versions.  18.04 is the current LTS.  **No** 2019 releases are LTS.

As for the output from fdisk, it looks like you installed using LVM and it is using all the available storage in sda1.  I don't know of any way to reduce the partition size safely when LVM is used, so I don't see any method to make room for Windows partitions.  I always use LVM on my physical machine installs.

If the computer has sufficient RAM and a fast enough CPU, you can run Win10 inside a virtual machine. This is a fairly safe thing. I would use virtualization for the Win10/8 OS running under Linux.  That is my recommendation.  It doesn't risk partition complications.  Plus, you'll get to keep using LVM.

For the future, it is always recommended to install Windows as the first OS on a computer if you want to dual boot.  If you do want to dual boot now, because 18.10 isn't supported, I would backup my data and a list of manually installed packages, then wipe the disk during the Win10 installation.  Then make some room for Linux and install it next-to Windows.  LVM can't be easily used in a dual boot setup. Most people wouldn't care about that.

---

### Post by oldfred on 2019-09-13
Not so easy.
LVM is logical volumes and is not compatible with Windows.
And it is not particularly easy to shrink as I understand it. But I do not really know LVM.
One of LVM's main advantage is when it controls entire drive.

You also have MBR(msdos) partitioning.
Is system very old as Windows has standardized on UEFI/gpt since Windows 8 released in 2012. You can install Windows 10 in BIOS mode, but then anytime Windows has issues, grub will not boot it and you have to temporarily install a Windows boot loader to MBR, fix Windows & restore grub.

With UEFI, you should always be able to directly boot Windows from UEFI, if grub will not boot it. And many minor repairs can be done from its internal repair console, but you still need a separate flash drive with Windows repair console.

You can try to shrink LVM, but someone that knows LVM will have to explain.

Or totally reinstall Ubuntu in standard partitions.
And then it depends on whether system is UEFI or old BIOS and how you want to install, UEFI or BIOS.

---

### Post by TheFu on 2019-09-13
Oldfred - LVM is laid out like this:
```
Disk
&#9500;&#9472;&#9472; Partition1
&#9474;   &#9492;&#9472;&#9472; Physical_Vol (whole partition)
&#9474;       &#9492;&#9472;&#9472; Volume_Group(named)
&#9474;           &#9500;&#9472;&#9472; Logical_Vol-1
&#9474;           &#9500;&#9472;&#9472; Logical_Vol-2
&#9474;           &#9500;&#9472;&#9472; Logical_Vol-3
&#9474;           &#9500;&#9472;&#9472; Logical_Vol-4
&#9474;           &#9500;&#9472;&#9472; Logical_Vol-5
&#9474;           &#9492;&#9472;&#9472; Logical_Vol-Z
&#9500;&#9472;&#9472; Partition2
&#9500;&#9472;&#9472; Partition3
&#9500;&#9472;&#9472; Partition4
&#9500;&#9472;&#9472; Partition5
&#9492;&#9472;&#9472; PartitionZ

```
Above is a simplistic layout.  LVs can be used as a partition for almost all day-to-day uses. They are mounted like partitions. File systems are put onto them just like partitions.  dd/ddrescue can be used to clone an LV, just like with a partition.

Resizing Logical Volumes, LVs, is relatively easy. Changing Physical Volumes, PVs, isn't.  In order to reduce the partition size, all the PVs, VGs, and LVs need to be moved.  There is a **pvmove** command, to move all of them from 1 partition to another - in the OPs situation, moving to a different disk with a partition marked for LVM use is how I'd do it.  But that needs another disk and if that is possible, I'd probably just connect it up, disconnect the current sda, and load Windows onto the new disk.  Then I'd do whatever was needed to run Ubuntu and do a grub-install and update-grub onto the Windows boot disk.  Oldfred is the guru at that stuff.

What does all this added complexity get us?  VGs can span disks. LVs can be RAID1, RAID5, RAID10, easily grown or moved to other storage. And for servers, the LVM snapshot capability is the backbone of enterprise backups that don't require services to be taken down to get a clean backup.

Clear as mud?

---

### Post by angel-cake on 2019-09-13
Thanks for your time @TheFu and @oldfred. 
I made a mistake, i am indeed using Ubunutu 19.04, nevertheless, that doesn't change the fact that is hard to do the job. I think I am just going to leave this laptop with Ubuntu, as it is already an old model, since I have to change to a new one anyway.

---

### Post by TheFu on 2019-09-13
If the machine has more than 4GB of RAM and at least a C2D from 2011 or later, then you can run a virtual machine which should work well enough.  More RAM is helpful. I suppose Win10 needs at least 60G to be happy, but I don't actually know.  I don't have any Win10 here and don't have any plans ever to install it.

19.04 support ends in January, so Nov/Dec plan to move to 19.10. ;)

---

### Post by Skaperen on 2019-09-13
if Windows 10 can run in a virtual machine then that is the way i recommend doing it.  it saves a lot of headaches and lets you run both at the same time.

the next LTS is 20.04.  most of us are using 18.04 until then.  i always recommend a fresh re-install after making *two* backups of all your personal stuff and a copy of all your configs from the old version.

i keep my **[COLOR=#0000cd][FONT=courier new]/home[/FONT][/COLOR]** filesystem in a separate partition.  when i do install 20.04 after it comes out, i will make a copy of the **[COLOR=#0000cd][FONT=courier new]/[/FONT][/COLOR]** partition into **[COLOR=#0000cd][FONT=courier new]/home[/FONT][/COLOR]** somewhere, make 3 backups of **[COLOR=#0000cd][FONT=courier new]/home[/FONT][/COLOR]**, install 20.04 reformatting everything (so every partition is running fresh), and restore **[COLOR=#0000cd][FONT=courier new]/home[/FONT][/COLOR]**.

i don't run Windows.  if i did, it would be in a virtual machine, only, probably **[COLOR=#0000cd][FONT=courier new]qemu/kvm[/FONT][/COLOR]**.

---

