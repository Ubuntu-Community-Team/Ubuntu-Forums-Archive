---
title: "Help Setting up Dual Boot with UEFI Windows 7"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by spassermorten on 2017-02-09
As the title suggest I've run into some problems setting up a dual boot with ubunutu unity and windows 7, the UEFI variation. 

I'm booting off of a USB that I set up using the universal usb installer. I can boot off said usb and carry through the installation but I'm not entirely sure how to partition my ssd. The different sources I've read do not seem to agree on procedure for a UEFI system. I've tried a couple different combinations, including the dreaded automatic partition resizing, each of which ending with me not being able to load into grub.

I've also checked through my bios seettings, and funnily enough it's right now setup to accept either BIOS or UEFI on startup and it actually prioritizes BIOS. The other part thats kind of strange is what I assume to be the windows UEFI boot partition, 100 mb, is type FAT32 instead of EFI. Maybe it's just me but that seems kinda wrong.

Would love to hear some suggestions from people with more experience.

---

### Post by oldfred on 2017-02-09
The ESP - efi system partition is formatted as FAT32.
When you add the boot flag if using gparted or if gdisk use code ef00, then a FAT32 partition becomes the ESP/efi partition. And you should only have one per device/drive.

Windows 7 default install is BIOS from DVD. You have to copy DVD to flash drive and move a couple of files around to make it UEFI bootable. Windows 7 does not support UEFI Secure Boot, so you must have Secure boot off. And how you then boot install media UEFI or BIOS is how it installs.
 Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736) 
Windows in UEFI mode needs several extra partitions. Best then to install Windows first.
      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 
    
Ubuntu's default install is just / (root) & swap. With UEFI it also must have the ESP, but will share the ESP with Windows if already created. Again how you boot install media is how it installs.
If you want more than default partitions you have to use Something Else. I find using gparted to create partitions in advance somewhat easier, but you still have to use Something Else and specify (change button) which partition to use as / (root). Installer uses ESP if already there and swap if already existing.

Many that understand partitions suggest separate /home as then a new install can reuse that partition. But I use data partition(s) instead, and often have multiple installs all using same data.

For more UEFI info see link in my signature below.

---

### Post by spassermorten on 2017-02-09
To start off thanks for all of the advice/help, I can see I'm probably not the first person you've helped with this.

If I'm not mistaken my OS should already be in UEFI, looked up some stuff online and it said I could verify that in a folder called panther within my c drive. That being said in my bios settings it also says under "UEFI/BIOS boot" and it is set to both. Is there any reason I should change that and restrict it to only BIOS or only UEFI?

It would make a lot of sense if I was already in UEFI with respect to the extra partitions too, bc when allocating a partition for ubuntu there were maybe 3 or 4 unnamed partitions associated with windows that I haven't created.

Also when picking the source for the boot loader installation thats meant to be the FAT32 partition and not the one it requests that is "reserved for BIOS boot area" right?

Thanks again.

---

### Post by oldfred on 2017-02-09
You always install grub to a drive like sda, almost never to a partition like sda1. 
With UEFI it only installs grub to the ESP - efi system partition on drive seen as sda.
With BIOS on gpt partitioned drive, the grub install is still to a drive like sda, but it must have a bios_grub partition for another part of grub, core.img. The core.img is normally in the sectors after the MBR with MBR(msdos) partitioning, but gpt does not have that space.

If you are seeing bios_grub that would be a BIOS install, not a UEFI install.

You only control whether you are installing UEFI or BIOS boot mode, by which mode you boot install media.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

