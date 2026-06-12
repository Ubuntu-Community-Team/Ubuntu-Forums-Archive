---
title: "Dual boot with Windows 10"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by anazzani on 2017-07-22
Hi all.

First post here.

I just installed Win10 pro on a new PC.

I have two disks:

SSD 240GB
HDD 1T

I'd like to use the SSD as boot device for both Windows and Ubuntu, while using the HDD as generic data drive.

When I installed Windows, I formatted only half of the SSD, so I now have 120G of unallocated space on the SSD and the whole uninitialized HDD.

Also I don't have a DVD drive, so I will have to create a bootable USB stick for Ubuntu (as I did for Windows).

1) do you see any problems with this setup?

2) do I have to make some specific configuration to setup the dual boot (I never tried before) or simply installing Ubuntu on the 2nd SSD partition is enough?

3) how should I format the HDD so that it's readable and writable by Windows and Ubuntu?

TIA.

Alessandro

---

### Post by yancek on 2017-07-22
If you do have unallocated space on the SSD where you also want to install Ubuntu, it should not be  problem.  Understand that this is not a standard install so you will need to select the manual installation method.  In Ubuntu, this is called "Something Else".  Using this method, you will be able to select the unallocated space you want on which to install Ubuntu.  A major question, since you installed windows 10 yourself, did you install it UEFI or the older MBR?  A pre-installed windows 10 would almost always be UEFI but the important part is that you should install both the same, both UEFI or both MBR.  The link below is the Ubuntu documentation on duala booting with windows 10 UEFI.  I'd suggest starting with that.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you want to share data on the HD with both system, you will need to use a windows filesystem (ntfs) for that partition as windows is incapable of reading or writing to any Linux fileystem whereas Linux system can do both on windows filesystems.

---

### Post by anazzani on 2017-07-22
Thank you very much for you reply.
> **yancek said:**
> A major question, since you installed windows 10 yourself, did you install it UEFI or the older MBR?Good question, but I have no idea: other than allocating half of the available space, I pretty much followed Windows defaults. How do I check this?
> **yancek said:**
> you will need to use a windows filesystem (ntfs) for that partition as windows is incapable of reading or writing to any Linux fileystem whereas Linux system can do both on windows filesystems.That's what I thought, I just wasn't sure if ntfs or fat or something else (my Windows expertise dates back to the XP era). If I try to initialize the volume in Windows, I'm prompted with a "partition style" choice:

MBR (Master Boot Record)
GTP (GUID Partition Table) <-- (Default)

So am I safe accepting the default?

Alessandro

---

### Post by anazzani on 2017-07-22
Oh wait, I just re-checked in Windows disk management and I see there's a "EFI System Partition": so this is it I guess.

---

### Post by oldfred on 2017-07-22
Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR(msdos) partitioned drive.
If you force conversion of partitioning from one to another, you then break Windows.

Default partitions are a lot different on UEFI and BIOS installs of Windows.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

If Windows is UEFI, then you want Ubuntu in UEFI boot mode. You then already have the ESP - efi system partition which will be shared for UEFI boot files.

See yancek's link in post #2 for UEFI install info.
Also more info & links in link in my signature.

---

### Post by anazzani on 2017-07-23
Thanks [yancek]("https://ubuntuforums.org/member.php?u=1928724") and [oldfred]("https://ubuntuforums.org/member.php?u=852711") for your assistance.

I think everything's working now.

One final question: before installing Ubuntu I disabled "Fast boot" in BIOS. I assume this setting must remain off also after installation, correct?

Regards.

Alessandro

---

### Post by yancek on 2017-07-23
Maybe someone else more familiar with windows will respond.  My understanding is that if fastboot is "on", you will not be able to mount or access any windows partitions from Ubuntu.  I'm not sure if there would be any other problems so you might wait for a more definitive response before changing.

---

### Post by oldfred on 2017-07-23
There is a UEFI fast boot and a Windows fast start up.

UEFI fast boot assumes no changes to system configuration. Normal boot checks all hardware and writes that data to hard drive for operating system to use.
UEFI fast boot can be turned back on, if you know how to get back into UEFI. Some systems make it really difficult as with fast boot you have no time to press a key. Both Windows & grub have ways to directly get to UEFI, but if neither work, cold boot may.

My motherboard has separate fast boot settings for cold (full power down) and warm (reboot). I set cold boot to full restart, so I can totally power down and then have time to press a key to get into UEFI or choose another boot option than default. And on warm boot, I could set it to a 3 sec delay, so if quick I can still get into settings, but not significantly slow reboot.

Windows fast start up or hibernation needs to be off, if you want to mount or use a shared NTFS data partition as the hibernation mounts all NTFS partitions. Best to only set Windows system partition as read only as the Linux NTFS driver exposes all the normally hidden system files and folders and gives users the opportunity to corrupt system. I used to turn on settings in XP see all those files  and managed to regularly break it.

---

