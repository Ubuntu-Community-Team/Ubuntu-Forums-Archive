---
title: "Parallel Installation with Win 8 and 7 UEFI"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by garbage98 on 2013-11-26
Hi,

I am in big problems to install Ubuntu Precise Pangolin along with Win 7 and Win 8. I have to admit, that I'm using quite new hardware, to be more specific my motherbord is an EVGA X79 Dark with UEFI BIOS. Before I start to explain what I already tried, let me mention that I have set up a parallel OS installation many dozens times... I'm not an expert but not an bloody amateur either.

My computer is equipped with four SSDs each holding one OS. Win 8.1, Win 7, Ubuntu Precise and Ubuntu Saucy. To hold things clean, I usually install each OS separately detaching the other drives during installation. This results in independent installations which I can manually select in BIOS by the primary boot device. After the setup I have the choice between GRUB2 and the Windows Boot Manager to manage my environment. Normally I prefer the Windows Boot Manager over GRUB2 as it is easy to set up over the tool EasyBCD.

Now my problem: I installed all operating systems separately as usual. Please notice that I followed the instructions for setting up an UEFI bootable device from the German Ubuntu Wiki ([http://wiki.ubuntuusers.de/EFI_Installieren](http://wiki.ubuntuusers.de/EFI_Installieren)). Now every system boots up when choosing the right primary device. But now comes the tricky part. I created all the entries with EasyBCD and was able to boot Win 8, Win7 and Saucy. But the option for Precise will boot Saucy or result in a corrupt GRUB... depending the installation was done without or with the UEFI preparation. I decided to try the other way round and set up the GRUB bootloader to handle my system. Unfortunately, selecting Win 8 resulted in an error message, too.

As I played a lot around to get this working, I have to admit, I came short on new ideas what to try. Any input in this matter is highly appreciated. Thanks!

---

### Post by oldfred on 2013-11-26
Is Windows 8 still hibernated. That will cause issues booting from grub.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Do not run any of the auto repair options with multiple drives. It will want to install grub into every drive. You can use update MBR even if UEFI and choose which system to update and which drive to install boot loader into.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

If you have secure boot on, that can also be an issue.

 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

---

### Post by garbage98 on 2013-11-28
Hi,

first thanks for the information.

I have a Boot-Info [capture]("http://paste.ubuntu.com/6488821/") but let me explain it a little bit.

All in all I have five SSDs and one HDD as well as a USB multicard reader atattched on my device. /dev/sdc and /dev/sdj are for data storage only, there is no OS intendet here. /dev/sda holds my primary OS Win7 with it's own Windows bootloader. As this is the exit strategy, I strongly prefer to keep this bootloader on this device for emergency single OS booting. /dev/sdk is my Win8 drive. Originally I planned to keep the Win7 boot loader on /dev/sda to boot Win8 but didn't manage to get it work this way around. That's why I'm using the Win8 bootloader on /dev/sdk. As described in my first post, I can boot Win8, Win7 and Ubuntu 13.10 this way. Adding Ubuntu 12.04 with EasyBCD on Win8 will boot the Ubuntu 13.10 installation... I am 100% sure I have selected the right drives when configuring it this way. Last but not least, I have Ubuntu 10.04 installed on /dev/sdb. As described earlier, I can install it with or without the UEFI preparation and it is booting when I choose this device as primary boot drive in the BIOS. Unfortunately I cannot boot any other OS with the GRUB installed on /dev/sdb... Selecting one of the other entries results in an error.

I hope, my explanation helps a little bit for better understanding. Regarding hibernation and secure boot: I switched both off, but have to admit, I cannot find secure boot in my BIOS. Nevertheless I switched all thigs in question off.

Thanks for your support!

---

### Post by oldfred on 2013-11-28
You have mixed MBR(msdos) and gpt drives.

You also have this, which may be an issue on an old gpt partitioned drive that Windows converted to MBR. Windows only removes primary gpt partition table and leaves backup and then Linux tools see both MBR and gpt and get confused. You can use fixparts to remove backup partition table.
 Line 203
GUID Partition Table detected, but does not seem to be used.

But your install in sdb looks like a UEFI boot with gpt partitioning and an efi partition. Once you start to boot in one mode UEFI or BIOS you cannot switch as they really are not compatible. So grub menu or EasyBCD cannot boot an install in another mode, just those other installs in the same boot mode.

Windows only boots from gpt drives with UEFI boot mode.
Both Windows & Ubuntu only boot from MBR partitioned drives with BIOS boot mode.
But Ubuntu will boot from gpt partitioned drives with UEFI if you have an efi partition or with BIOS if you have a tiny 1 or 2 MB unformatted partition with the bios_grub boot flag.

So your motherboard must be UEFI capable. Currently only new Windows 8 pre-installed have the UEFI secure boot option turned on, other systems with UEFI do not yet have that. 
Then when installing you have to make sure you boot in the mode UEFI or BIOS that you want your install to be. I think Windows and know Ubuntu installs in the same mode as you boot install media (once system is booted UEFI then it is only UEFI).

You can dual boot with one system UEFI and another BIOS, but have to boot from UEFI menu. Some UEFI auto switch or offer both, but you may have to turn on or off UEFI or BIOS/CSM/Legacy boot modes before changing boot mode.

I do not yet have an UEFI system, but all new drives are partitioned with gpt. My newer SSD has both an efi partition for future use and the bios_grub partition for current booting. Then I can easily move my SSD to a new UEFI system and have an efi partition at beginning of drive without having to totally repartition or move lots of partitions around to make space for the efi partition. Best if efi partition is at beginning of drive.

Windows (except XP) will read gpt data drives from BIOS boot. So I only suggest MBR partitioning for new systems on a BIOS boot Windows drive or a drive that may have Windows in the future in BIOS boot mode. All other new drives should be gpt, and have an efi partition at the beginning of drive in case you want an install on the drive.

I also prefer installs on separate drives like you have done, and have the boot loader (MBR or efi) on the same drive. Or every drive can boot without any other drive. I do mount partitions from other drives and if that drive fails I may get errors on data partitions not mounting but can still boot.
Do not run auto fix from Boot-Repair as it will want to install one boot loader to every MBR. It assumes you do not know what drive you  are booting from in BIOS so to make system work just install grub everywhere. You can use it, by turning off auto fix and in advanced repairs choose an operating system and install its boot loader to the same drive. 

Boot-Repair can convert your UEFI install in sdb to BIOS by uninstalling grub-efi and installing grub-pc. But you have to create the bios_grub partition first as it cannot create partitions and grub will not install to the MBR correctly in gpt partitioned drives without the bios_grub partition.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

      
 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

