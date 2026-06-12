---
title: "Ubuntu doesn't boot after &quot;Install along Windows 7&quot;"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by Evilhugbear on 2012-07-29
Hey guys,

I decided to try Ubuntu again after a while, and I downloaded the 64-bit Ubuntu 12.04 version.

I had Windows 7 installed previously, using roughly half of my first HDD (500ish gigabytes), and left the other half unallocated to for Ubuntu to use. I didn't make any partitions for Ubuntu.

After I booted up Ubuntu's LiveCD, I saw there was an option to Install Ubuntu along Windows 7, and decided to try that. Everything seemed to install correctly, so I rebooted. However, after I rebooted, it just instantly went into Windows 7.

Any idea on how to fix this?

I have a UEFI motherboard, if that matters. And in Windows 7's Disk Management, it shows 2 new partitions (435.2GB Healthy Primary Partition, and a 7.99GB Healthy Primary Partition).

If you need any more info, just ask :D.

---

### Post by arpanaut on 2012-07-30
Take a look at what is linked in this post:
[http://ubuntuforums.org/showpost.php?p=12123617&postcount=8](http://ubuntuforums.org/showpost.php?p=12123617&postcount=8)

You may want to look at the entire thread too, as you seem to be facing the same issues.
And hope that oldfred sees your thread and comes to the rescue as he seems to have the best info about EUFI in respect to grub2 and Ubuntu.

Good Luck!

---

### Post by drmrgd on 2012-07-30
Dual booting with a UEFI system is a little more complex than it was with just a straight up BIOS system.  So, you're going to have to tinker a little bit to get this to work.  

The first thing I'd recommend is to be sure to have a Windows installation CD (or recovery CD at least) so that if you completely hose the boot loader, you won't be stuck.  It's pretty easy to do, but pretty easy to fix if you have a recovery CD.  

Here is some very useful documentation that helped me get setup (note the difference in my set up was that I wanted to have two HDs instead of just one):

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

The basic goal will be to have Grub2 (which should be installed by default when you install 12.04) be the primary boot loader, and then use it to chainload the Windows 7 EFI boot loader.  This also means that you have to be sure that you've installed 12.04 in UEFI mode.  To do this, make sure that you load the .iso in UEFI mode from the BIOS menu (which I guess really isn't BIOS anymore!). 

Hope that helps you get started.

---

### Post by oldfred on 2012-07-30
You may have installed in BIOS mode so UEFI boot does not see grub in the MBR. Or grub may not have installed its efi loader into the efi partition.

From Boot-Repair post link to the report from BootInfo. He has added some of the fixes for UEFI, but that is still a work in progress. If Ubuntu is otherwise installed correctly, you may just have to copy the grub efi boot file into the efi partition and not totally reinstall. Not sure if Yanni has added that to BootRepair or not. He had updated it recently to add a dual boot entry so grub can boot Windows with efi partition.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

