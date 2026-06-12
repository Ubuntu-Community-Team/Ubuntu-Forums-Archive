---
title: "New SSD install, some grub questions"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by Chew N Tobacca on 2019-02-08
I feel like this topic has been beaten to death on these and other forums, but I can't seem to find any solutions pertinent to my situation. Here's the story: I'm putting in a SSD as my new primary drive. Currently I have a dual-boot setup on a 1TB HDD using Windows 7 Ultimate and Kubuntu 12.04 (yea, I know). Now I'm gonna do an install of the newer LTS 18.04 and would like to be able to access all three systems. I can easily swap the drives to let the BIOS use the SSD as primary, and clone the Windows partition to the new SSD and do the fresh install of the 18.04, no problem. But what I'm wondering is, how do I allow the installer to place grub on the SSD (will be /dev/sda) and ignore the existing grub on my current HDD (will be /dev/sdb)? My 12.04 still uses grub 1.99, not grub2.

I hope I'm making sense. Let me rundown once more. My goal is to have Windows 7 and 18.04 on the new SSD, and keep the 12.04 accessible as a third OS and have the old HDD for extra storage, etc. I'm just not sure how to handle the grub loader. Any suggestions are appreciated in advance!

Thanks,
Chew

---

### Post by Dennis N on 2019-02-08
You could disconnect the old HDD before installing. Then reconnect it after you install. 

Disconnection also avoids the potential problem where the new Ubuntu's grub will find a swap partition on the HDD and appropriate it instead of using a new-style swap file.

---

### Post by oldfred on 2019-02-08
If you use any of the default installs, it will install grub to the drive seen as sda.
The drive seen as sda is usually the first SATA port or SATA0. So the order you plug drives into motherboard may make a difference.
Also some BIOS/UEFI promote your flash drive installer to sda and then grub may not default install to correct drive.

With multiple drives always best to use the Something Else install option. And on the partitioning screen at bottom in the combo box choose the correct drive, but almost never choose a partition.

Older instructions on partitioning may suggest a swap partition. But with 18.04, it now uses a swap file. But if you have a swap partition it will be used.

If new drive may eventually go into a newer system that is UEFI, you may want to plan ahead and use gpt partitioning and include an ESP for future use. But to boot in BIOS mode on gpt partitioned drive, you need a 1 or 2MB unformatted partition with the bios_grub flag.

The only place to still use the  old MBR(msdos) partitioning is if you want Windows in BIOS boot mode. Windows only boots in BIOS from MBR and only boots in UEFI with gpt. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Chew N Tobacca on 2019-02-11
Thanks for the good info. I didn't realize I was that far behind the times; seems like I've some homework to do. Yes, my motherboard (ASUS m5a97 r2.0) does indeed support UEFI. Also, I forgot to mention that I also currently have a secondary drive which has a swap partition and the win7 page file.

---

### Post by Chew N Tobacca on 2019-02-12
All the UEFI and GUID partition table info makes pretty good sense; thanks again for the great info! Most of it seems pretty straight forward. So, back to the original question: What do I do with the existing grub that boots my 12.04/win7 system? Can I simply remove it and have the new one from the 18.04 do all the work? Or do I leave it be? 

Thanks again,
Chew

---

### Post by oldfred on 2019-02-12
If you have old installs, those will probably be BIOS with MBR partitioning.
Only BIOS grub will boot BIOS installs, and only UEFI grub will boot other UEFI installs, but not BIOS installs.

New UEFI is not compatible with BIOS, but UEFI has CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Windows in BIOS/CSM boot mode will only boot from MBR(msdos) partitions.
Windows in UEFI boot mode will only boot from gpt partitioned drives.
Ubuntu can boot in either UEFI or BIOS from gpt partitioned drives if you have correct supporting partitions.

The only place to have MBR is if you want to boot Windows in BIOS mode, or a few just want MBR since well known.
If drive is only for Ubuntu or may be moved to a system made after Windows 8 released in 2012, so better to use gpt.

Back in 2010 I started to convert all new drives or totally reformatted drives to gpt with bios_grub partition for BIOS boot. When Windows required UEFI/gpt in 2012, I added an ESP - efi system partition so I could move drive to a new system later without totally repartitioning.

---

### Post by Chew N Tobacca on 2019-02-19
Thanks, oldfred, I believe you have answered my questions. For now, I think I'm going to stick with the old MBR type partition, since it's all set up that way already and has done me well thus far. I plan to build a new system in another few years, as my 5-year old system is starting to get dated. I'll modernize myself at that point.

---

