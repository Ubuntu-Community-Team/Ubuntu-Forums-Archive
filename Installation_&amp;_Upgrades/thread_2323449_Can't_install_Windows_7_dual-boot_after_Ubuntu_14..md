---
title: "Can't install Windows 7 dual-boot after Ubuntu 14.04"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by handenauer on 2016-05-05
Hello everyone,

**Previous issues:**
My laptop has had a rough year. It is an Asus F555L and originally had windows 8.1 in it. Two months ago it had the infamous [100% disk usage issue]("http://answers.microsoft.com/en-us/windows/forum/windows_8-performance/windows-8-keeps-slows-down-to-100-disk-usage-and/cd787f8d-e7b4-4872-aecb-6f0cd15ad942?auth=1") which I could not solve after a week of looking in every forum. Anyway, I finally formatted the hard drive and installed ubuntu 14.04 alone on it, which rather surprisingly has been working flawlessly since then. 

**Goal:**
However I would like to have the option two dual boot to windows (mainly for gaming).
 
**What I did:**
From an ubuntu live usb first I made an 120GB NFTS partition on my drive with gparted. I then changed the partition table from MBR to GPT with fdisk following [this tutorial]("http://www.firewing1.com/blog/2012/03/05/how-convert-gpt-disk-layout-ms-dosmbr-layout-without-data-loss-and-gigabyte-hybrid"), apparently succesfully. I have burned an windows 7 iso in a usb and after enabling "launch csm" option in the bios and making sure it was on a 2.0 USB port (...I have suffered to find out all this...) managed to boot from it.

**The problem:**
I installed windows 7 on the NFTS partiton, however I am unable to boot it,  and the option to boot windows doesn't appear on the bios.

I tried to install again windows7 and erased everything in the partition several times.
 I tried to repair windows with the windows7 iso (bootrec /FixMbr /FixBooT /RebuildBcr). 
I also tried to install boot-repair on ubuntu.

In particular when I do /RebuildBcd it says that 0 windows installations have been found, but when previously asked which windows installation I wanted to fix it was there. Also the files are there. Moreover when I boot Ubuntu (which I still works and has all my files, surprising after all this messing around) and open gparted, the NFTS partition has the boot label.

**The actual question:**
Any ideas on how to fix the windows 7 installation?

I have everything backed up and the next thing I was going to try was to format all the hard drive and install windows 7 from scratch, but I would prefer to avoid having to set up ubuntu again. Btw I also have a windows 8.1 iso but I prefer windows 7.

---

### Post by T.J. on 2016-05-05
First, I just want to **thank** you.  If everyone posted as concisely as you do, problems would be a **lot** easier to solve. :D

You did leave out two very vital pieces of information that I have to ask for: the partition arrangement and the revision of Windows 7 on the disc you are installing from.  

I suspect you may be having BCD issues because:

[LIST]
[*]Your install disc is old and  has issues with GPT formatted drives - meaning it is installing an older version and not the latest Service Pack. This might not seem important, but it can have a huge effect on booting UEFI/GPT installations.
[*]Windows - generally speaking - requires the first partition on the drive to contain the Windows OS and/or the bootloader.  I know it is ridiculous, but it is nevertheless necessary in order to avoid problems.
[/LIST]

You should probably **not** use SecureBoot if your system has it. It causes more boot issues for some than it solves. UEFI implementations can be very buggy. Windows 7 is pretty old in terms of support from Microsoft. You want to avoid potential bugs that they aren't going to fix. 

A successful dual boot usually requires that Windows has the partition setup that it wants. It's easier to install Windows first and Linux after - but it is **not** required.  Linux doesn't care where it is located.  When booting after the Linux install, Grub will load first and then transfer control to BCD to boot Windows.

Please post back and let me know if I can be of greater assistance.

--------

P.S.

If I might make one off-topic comment? Windows does not "play nice" with non-Microsoft products. In rare cases with 7, it merits abandoning a dual-boot for a KVM. If you have the necessary hardware support, and do not care about Blu-Ray/HD DRM used in streaming from Vudu, etc, I recommend it over dual booting. (SD streams work fine, btw.) I especially recommend not dual-booting with Windows 10.

---

### Post by oldfred on 2016-05-05
Windows 7 does not support Secure boot. If you have setting like "Windows" and "Other" in UEFI that really is secure boot and if for Windows 7 in UEFI boot mode must use "Other". 

Windows 7 default install is BIOS/MBR. You have to copy to flash drive and modify for UEFI boot.
Enabling CSM is BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Windows only boots from gpt partitioned drives with UEFI. So if you want UEFI, you have to convert Windows 7 installer.
Windows only boots from MBR partitioned drives with BIOS. If you install in BIOS mode it may convert drive to MBR, and leave gpt backup partition table. Then Linux tools complain as you have both MBR & gpt. About only way to fix that is with fixparts.

So what do you really now have, and what do you want. BIOS or UEFI?
      
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by handenauer on 2016-05-05
Hi, thank you for your reply.

I had to disable secure boot to boot from the usb, so this is not the problem.
I was attempting to install windows on the third partition of the table so this might be the problem! Unfortunately this means that the solution still is to format everything.

I didn't know about KVMs. I have been using Oracles VirtualBox for certain windows-only programs but was never able to install games. I will definetly try that out.

---

### Post by handenauer on 2016-05-05
I have BIOS and MBR partition table. And I don't care wether BIOS or UEFI as long as I can have the dual-bot windows7-ubuntu

---

### Post by T.J. on 2016-05-05
> **handenauer said:**
> Hi, thank you for your reply.

I had to disable secure boot to boot from the usb, so this is not the problem.
I was attempting to install windows on the third partition of the table so this might be the problem! Unfortunately this means that the solution still is to format everything.


Quite likely, this is especially important in getting older versions of Windows to behave. If you have some experience with tools such as Clonezilla, you may be able to copy the existing Windows partition to the first, then use Microsoft's bootrec to fix the startup. Another possibility would be installing Windows on the first partition on a different disc.  

 I am truly sorry to be the bearer of bad news.



> I didn't know about KVMs. I have been using Oracles VirtualBox for certain windows-only programs but was never able to install games. I will definetly try that out.

I stopped using VirtualBox for similar reasons. Their video drivers for guests are absolute crap, IMHO.  I also admit, that I am biased against Oracle and Microsoft and that is a factor in it.  After having been a programmer for years, I refuse to run Windows natively, even by dual-boot. It is too prone to issues.

 If your motherboard is capable of IOMMU, and you have two GPUs (discrete or onboard); you can create a hardware enhanced VM setup capable of playing any game you wish.  The general overhead depends on the efficiency of your disc and configuration. It's very small if you optimise.  It not, it is about 15%. I've tweaked mine only slightly, and I can play things such as Fallout 4 with no problems. So the games would play at 85% to 90% of native speeds, depending on optimisation, with no rebooting required. 

An example is here: [https://www.youtube.com/watch?v=17qxEpn4EGs](https://www.youtube.com/watch?v=17qxEpn4EGs)

You would also have Windows virtualised, meaning that if you switch to different hardware, you would not need to reinstall Windows, merely copy the virtual drive file to your new Linux machine, and reinstate your settings for the KVM.

---

### Post by handenauer on 2016-05-06
Finally I decided to:

1. Format the whole drive.
2.Create two partitions with the windows installation disk (150gb/350gb).
3. Install windows on the first partition and check that it works. Good.
4. Boot from Ubuntu live usb.
5. Format 2nd partition to ext4 and create a third swap partition.
6. Install ubuntu
7. Fix the grub

I have not everything set up and running.
Every step is well explained in other questions in the forums, so in the end I think this post is of limited usefulness...

---

