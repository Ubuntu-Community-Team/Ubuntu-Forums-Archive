---
title: "Installing Ubuntu on a bootable external SSD drive"
date: 2017-10-03
forum: Installation &amp; Upgrades
---

### Post by HawkFest on 2017-10-03
**In short: the external SSD drive can't boot my PC**. The following exposes the context (the technical environment), then the goal which consists of creating a bootable external SSD drive hosting Ubuntu Linux and plugged via a USB 3.1 G1 port, and finally the problem, including some details involved in the process (partitioning of the external SSD drive and setup).

**CONTEXT**

The OS and Machine that'll be mostly using this external drive, is a **Windows 10 Home (EFI), hosted on a GPT high speed 1TB HDD**, in a recent HP Laptop (2017 Intel's 7th generation i7-7500U. Namely the HP Envy x360 m6-aq105dx, with **16GB DDR4 RAM, 2xUSB 3.1 ports of wich one is a power port**, and a third USB 3.1 G2 Type-c port). That's also from where I want to create the bootable external drive (as I did for 2 bootable flash drives that work flawlessly).

I have an SSD (the Silicon Power Slim S60 2.5" 240GB). I've put it in an exclosure for external SATA III drives offering a USB 3.0+Power combo mini-plug (it can draw power from the PC's USB port which is also a power port). It works fine, I've partitioned that drive flawlessly using Paragon Hard Disk Manager 15, and it makes up for an extremely efficient external drive. If all works well I'll create another of such SSD drive but with a 1TB SSD (so as to get more NTFS space for sharing files).

**GOAL**

What I want to do is make that external SSD boot the PC in Linux (namely Ubuntu), as a safe guard in the event my PC becomes corrupted or whatever could happen. That way I'd always have a portable OS + Office apps, production tools and utilities at hand (it's smaller and slimmer than most traditional external enclosures as it's designed out of the size of an SSD). I'll also - and mostly - use it with my portable Laptop, since the SSD will have an NTFS partition for sharing files (about 100Gb out of a total size of 224Gb). Most importantly, it'll be for one of those days when I feel like using Kubuntu or Ubuntu rather than my laptop's Windows 10...

**PROBLEM**
The external drive can't boot the PC. While using a LiveCD Thumb Drive, Installing Ubuntu on an internal hard drive is successful, but not on the external SSD drive: the later can't boot the PC.

1- I know the USB boot priorities are well set: the PC can boot with smaller flash drives I've already created using [Rufus-2.17]("https://rufus.akeo.ie/") : one for installing Ubuntu systems - like a LiveCD (SanDisk 8GB USB Flash); the other one for booting with Paragon Recovery Media (a 4GB USB Flash generic Kingston); both into a FAT32 single partition.

2- The external SSD Drive that must be able to boot the PC is configured as a "**Basic MBR Hard Disk**". It has been partitioned as follow:

[IMG]http://imageshack.com/a/img924/2862/xDrxXo.png[/IMG]

partition 1....Ext4....Primary....1229Mo..... "/boot" (for installing Grub on the MBR?), min. at 100MB
    partition 2....Ext4....Primary....51200Mo....."/" root for Ubuntu
    partition 3....Ext4....Primary....40960Mo....."/" root for Kubuntu
    partitionE....None....Extended....135546Mo.....EXTENTED PARTITION container sized at 135545Mo
        Partition 4....Ext4....Extended....8704MB...."Utmp" /tmp Temporary files for Ubuntu
        Partition 5....Ext4....Extended....8704MB...."Ktmp" /tmp Temporary files for Kubuntu
        Swap....Swap....Extended....24576MB....Swap for Ubuntu and Kubuntu
        Partition 6....NTFS....Extended....93561MB....FShares

It can be noticed that I've prepared a second root partition for Kubuntu. I'll install both on the same /boot partition (ending the global installation with Ubuntu), and both will share the same Swap (but not the same /tmp)

**MY QUESTION**
What are the considerations, prerequisites and steps so as to create an external SSD drive (mine is a 225GB), with a boot sector / partition which can boot a PC so that whatever OS installation procedure over it would work (in my case it would be Ubuntu or Kubuntu)?

---

### Post by ubfan1 on 2017-10-03
Your host machine is running in UEFI mode (2017 laptop, running W10 on a GPT disk) -- you should install additional OSes in UEFI mode.  To boot a device in UEFI mode, you need an EFI partition on it (300M, FAT342).  Why mess around with an MSDOS partitioned external disk?. You can do this, but why? Just make the SSD GPT too.   Now HPs have known problems with booting non-Windows OSes in UEFI mode -- basically they require a specific name (Windows Boot Manager), but for an external disk, you do not need any specific boot entry, just the device default of /EFI/Boot/bootx64.efi (that / is starting at the EFI partition, /boot/efi is where that partition usually gets mounted).  An install bug ignores the grub location, and uses the first disk.  Just copy everything over to the second disk (yea Windows stuff too, it easily fits and makes a good backup).  Then ensure the /EFI/Boot/bootx64.efi is a copy of grubx64.efi, (check sizes).  If not just copy it over from /EFI/ubuntu/grubx64.efi.  If you are running with secure boot, use shimx64.efi instead for bootx64.efi, and put a copy of grubx64.efi (no name change) in /EFI/Boot .  That device setup should now boot the SSD.  

As for the partition setup -- why are you using separate /boot and /tmp partitions anyway?  Maybe /boot for encrypted LVMs but otherwise why?    Just leave /boot and /tmp in their own root fs.

---

### Post by HawkFest on 2017-10-03
Thanks for your reply. My reasons for older BIOS compatibility (older machines prior to let's say 2015), are of my own needs which are maybe not the same as yours : a requirement for my work, e.g. in case I'd need specific analysis tools, benchmarking and recovery tools, or simple personalized working environment for whatever office work I could have to do wherever, with any PC at hand could it be in my client's premise or even an internet cafe PC if not "wherever" (on top using it the way I've described, in the OP). But thanks for your concern anyways. I'll only use generic drivers except maybe with Kubuntu : since I'd have two OS, I thought that a multi-boot would be better from a single place as a boot-loader, where modifying the same "grub" or some update would work for both Linux Distribution. That's what I do on another PC and it works fine, I also used EasyBCD to make Windows' boot-loader have an entry for Ubuntu and Kubuntu - which are in a second internal disk. Only problem was that updating Kubuntu corrupted the grub: I then found out on these forums and such, that Ubuntu should be installed last (which is what I want to do: right now I'm trying to boot onto Kubuntu, I haven't installed Ubuntu yet). 

 About the tmp folder your right: an SSD isn't like a mechanical HDD and thus there's no need for a partition containing temporary files in order to gain in performance (it could be useful for some scenarios involving volumes of multiple SSD-HDD, in having the /tmp on some other disk or cache volume). And thanks for the GPT consideration: I already thought of this, for the extreme situation I couldn't find a solution. In which case your reply will be handy. In the mean time I'll continue to seek for a solution, thanks again.

---

### Post by ubfan1 on 2017-10-03
OK, for compatibility with older machines, you can use MSDOS partitioning, but still set the SSD up with an EFI partition (300M, FAT32).  That way, you can install the grub_efi bootloaders into the EFI, and alsoi install grub-pc into the MBR sector of the disk so it boots both legacy and UEFI if required.  Even circa 2015 machines should be able to boot off GPT partitioned disks, but some older machines cannot.  If you do decide GPT is acceptable, you will need another partition (1M, no format) flagged grub-bios for the legacy grub to install it's core.img file (which is put outside the partitions on an MSDOS partitioned disk).  When both boot mechanisms are present, the machine settings will determine how the SSD boots -- some machines set the mode, some allow you to set an order preference when both are present.  Just don't expect to boot a UEFI Windows from a legacy grub.
  The last OS installed tends to grab the grub configuration, not Ubuntu over Lubuntu etc.

---

### Post by oldfred on 2017-10-04
Since about 2010 I have used gpt. And back then it was only a BIOS based system.
Windows only boots in UEFI mode from gpt.
But Ubuntu will boot in BIOS mode or UEFI mode from gpt.
With BIOS on gpt, you have to have the bios_grub partition.
With UEFI on gpt you have to have the ESP - efi system partition.

You can have both grub-pc and grub-efi-amd64 installed but often they get out of sync & have issues.
I just prefer to have a larger flash drive with full install and multiple ISO as bootable repair tools. 
And have one in BIOS boot mode and one in UEFI boot mode.

       Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

---

