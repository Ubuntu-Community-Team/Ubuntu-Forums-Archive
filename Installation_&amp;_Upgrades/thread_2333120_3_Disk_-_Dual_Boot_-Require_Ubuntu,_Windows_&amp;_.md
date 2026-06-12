---
title: "3 Disk - Dual Boot -Require Ubuntu, Windows &amp; Data - What the would people recommend?"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by serafini-c on 2016-08-07
Dear Ubuntu Forum,

I getting two SSDs 240GB I am thinking one for Windows 10 and the other with Ubuntu (Not sure which one yet). The third spinning disk (1TB) will be just data.

I am thinking of having only one SSD disk plugged in when installing each OS. I am trying to avoid mistakes when installing Ubuntu and Windows. Please advice if you think this wrong way to install the OS?

The data disk I am not sure what I should be installing? Since I want both OS's to view the disk my guess would be some sort of Samba file structure. Could people please advice what I should be doing with this Data Disk?

The last question is what would people recommend with mananaging this dual boot setup? Should I boot into Ubuntu by default and will the GRUB detect the Windows OS? I have heard some people saying I should install GRUB on all disk?

I have used linux a little but have loved it (lubuntu mainly) and want to jump more into it. So my work station is finally going to have linux on it. I just have some apps for work that still require windows so at the moment cant pull the full plug yet on Windows. Cross platform software has help with the transition LibraOffice, Thunderbird, Gimp, Inkscape, GNUCash, Clementine, OBS.

Thanks for reading this post.

Kind Regards,
Paul Serafini

---

### Post by Pumba! on 2016-08-07
Hello Paul, I will give you my two cents.

What i would do is first install W10 in one SSD, having just that disk connected.
Then I would install the second disk, boot the Ubuntu Live installer and procced to install it using the whole 2nd drive. I would also install grub in that disk.
Then, you should be able to select your first boot drive in the BIOS, and if you choose the disk that has W10 it will boot directly into it, ignoring Ubuntu. On the other hand if you choose to boot primarily from the Ubuntu HDD, it will boot to Ubuntu by default, but grub should offer you to boot into W10.

Finally, regarding the 1TB disk, you can format it as NTFS either from W10 or Ubuntu, and you will be able to access it's data from either operating system.
Please excuse my english, and I hope this is helpfull.

Pablo

---

### Post by grahammechanical on 2016-08-07
You also have to give consideration to something else. Does the motherboard use a BIOS or a UEFI boot system? With UEFI all operating systems have to be installed in the same mode. With Windows 10 installed in EFI mode Ubuntu must also be installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With UEFI and disks/drives with GPT partitioning boot files go in an efi_boot partition. The Ubuntu installer defaults to installing Ubuntu efi boot files into the efi_boot partition on sda. And I have heard that even if we direct the installer to put the efi boot files into the efi_boot partition on sdb it will ignore the instruction. Windows efi boot files and Ubuntu efi boot files can co-exist in the same efi_boot partition.

A factor to consider is whether you are going to use the Erase disk and install Ubuntu option to install Ubuntu onto the second SSD or the Something Else option where you have to create your own partitions. Make sure you do not erase the drive with Windows 10 on it.

Regards

---

### Post by oldfred on 2016-08-07
All good advice above.

Whether UEFI or BIOS be sure to install Windows SATA drive into first SATA port probably labeled SATA0, Ubuntu drive in 2nd & data in 3rd. Do not skip ports. I skipped ports or have installed DVD in between drives and had drive order issues.

If UEFI and you unplug a drive, UEFI's NVRAM forgets its entries. Most will refind them with a cold boot (full power off/on), but not warm reboot. Power must be off anyway when plugging in drives.
But UEFI has a fast boot setting. That skips all the hardware checks for changes to configuration. And it does allow faster boots when system rarely changes configuration. But new system with many changes being made, much better to have UEFI fast boot off, at least until fully configured.

With Windows 8 or later make sure fast start up (hibernation) is off (different than UEFI fast boot). Linux NTFS driver cannot see hibernated NTFS partitions including others mounted like another drive's NTFS as it also is left hibernated.

I consider it better to use UEFI with gpt partitioning. But even if you want the 35 year old BIOS with MBR partitioning for Windows you can use the newer gpt partitioning for Ubuntu (and data) with BIOS. But gpt requires additional partitions to support boot mode. I have only partitioned new drives and even larger flash drives with gpt for about 5 years. First with older BIOS sytem then newer UEFI systems. But I still put both the ESP - efi system partition and bios_grub partition on every drive as first two partitions.  Windows has its own requirements.

Lots of UEFI info in link in my signature.

---

### Post by serafini-c on 2016-08-22
I have not been getting notifications about this forum post so I am sorry for the late reply. 

Thank you all for the help you provided but I have not actioned anything yet.  

 
 
 Reviewing these posts I am sure that I will be able to carry these recommendations out. 

I will try and update this forum post on how I got on.  

 
 
 I will end this forum post as successful.
 
 
 Thank you all again the Ubuntu Community.  
 
Kind Regards,
Paul Serafini

---

