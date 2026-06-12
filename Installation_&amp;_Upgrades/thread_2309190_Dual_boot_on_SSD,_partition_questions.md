---
title: "Dual boot on SSD, partition questions"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by timbalisto on 2016-01-08
I have done a lot of research and have found a lot of conflicting/outdated information. I am building a new budget gaming desktop (the components are still arriving in the mail), as my current desktop from 2006 is showing its age. I will be installing Windows 10 and Ubuntu 15.10, and I have some questions regarding dual booting on an SSD. 

I will have a 120GB SSD for the operating systems, and a 1TB HDD for storing personal files. On past systems, I have partitioned my main HDD as NTFS for the first partition, EXT4 for the second partition, and a small swap partition for the third. should I do the same for my new system?

I've read that the SSD should not have a swap partition, as it can wear out the SSD with too many read/write cycles.  I never use the hibernate function, but I do use the suspend function all the time. The new system will have 8GB of RAM, will I even need a swap partition?

Most guides I've read about installing Ubuntu on an SSD say to have a separate partition each for /home, /, and EFI. That seems excessive, I would prefer to have / and /home on the same EXT4 partition. I've never seen an EFI partition, but my new system has UEFI. The guides I read about it are from 2010-2014, so I don't know if that info is outdated. I plan on partitioning the SSD with an Ubuntu live USB before installing the operating systems (Windows first, then Ubuntu). Do I need to manually make an EFI partition in addition to the NTFS, EXT4, and (possibly) swap partitions?

Here are the specs on the system I'll be building:
CPU: Intel Pentium Processor G3258 4 BX80646G3258 (dual-core, 3.2Ghz base frequency)
Motherboard: ASUS H81M-E MicroATX DDR3 1333 LGA 1150
GPU: EVGA GeForce GTX 960 Superclocked Gaming ACX 2.0 4GB GDDR5 128bit PCI-E 3.0
Storage: Silicon Power 120GB S60 2.5" 7mm SATA III 6Gb/s Internal Solid State Drive, and my old sata 1TB HDD from my current rig.
Memory: Crucial 8GB Single DDR3 1600 MT/s PC3-12800 CL11 Unbuffered UDIMM 240-Pin Desktop Memory

Any help would be appreciated. Thanks.

---

### Post by oldfred on 2016-01-08
A year ago I built a new UEFI system with Asus Z97 motherboard & i5, with 120GB SSD & 1TB HDD. I do not use Windows, but it has requirements for several partitions. I also have several copies/versions of Ubuntu on both drives. Not sure of detail difference with H81, but expect UEFI settings are probably similar.

If not familiar with UEFI, please review link in my signature and follow many of the links to even more info.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)
Is your current HDD, gpt or MBR? Better once you change to UEFI to have all drives as gpt, but if not a boot drive it does not have to be. There is a way to convert MBR to gpt, but I have not used it. Backups, of course are required.

I put 2GB swap on HDD. But even with my older system and 4GB of RAM, I never used swap. But new SSD have lives similar to HDD, so it does not really matter where swap is. And if not using it, it cannot wear out. :)

I did have to make many settings in UEFI to get it to boot Ubuntu installer on flash drive in UEFI mode. I turned off fast boot in UEFI, so I could still get into UEFI to change settings or choose a boot until fully configured. The "other" operating system is also to turn off Secure boot. Did not try with Windows setting, as Ubuntu should boot with secure boot on, but easier without secure boot for now.

Some Asus screenshots:
[http://ubuntuforums.org/showthread.php?t=2245911&p=13136696#post13136696](http://ubuntuforums.org/showthread.php?t=2245911&p=13136696#post13136696)
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by timbalisto on 2016-01-08
With help from the above poster, I've found that I have to have the SSD as gpt, an EFI partition, then my two OS partitions. The 1TB HDD is MBR and just for storage, no booting. Which means I don't have to switch it to gpt, which would be a pain because it's already mostly full. 

Using the Ubuntu installer, I can create an EFI partition and Ubuntu will set the boot flag, ESP codes, and fstab automatically. If I don't use the installer, and just use gparted on its own from live usb, do I have to configure boot flag, ESP, and fstab manually? I would like to setup all the partitions before installing the operating systems, because shrinking a partition takes forever (although, I don't think it would take that long on an SSD?).

 If I were to start with a blank SSD and install Windows 10, it would create an EFI partition, the main OS partition, and a recovery partition (which I don't want). After Windows is done installing, can I delete the recovery partition, shrink the Windows partition, create the Ubuntu partition, and have Ubuntu use the EFI partition that Windows made?

Do I need the swap partition? A lot of guides say that it's better to have a swap partition and not need it, than to need a swap partition and not have it. The system will have 8GB of ram and I never use hibernate, just suspend. If I do make a swap partition, can I get away with making it only 1GB? Some guides say to make swap double the ram size, but that just seems ridiculous.

---

### Post by leclerc65 on 2016-01-08
I put the swap on the HDD, and set swappiness=1 to avoid swapping as much as possible.

---

### Post by yancek on 2016-01-08
> If I were to start with a blank SSD and install Windows 10, it would  create an EFI partition, the main OS partition, and a recovery partition  (which I don't want). After Windows is done installing, can I delete  the recovery partition, shrink the Windows partition, create the Ubuntu  partition, and have Ubuntu use the EFI partition that Windows made?

Yes, that should work.  You shrink the windows partition using its Disk Management tool and leave unallocated space.  Not much point in creating a partition for Ubuntu from windows as you will need to format it during the install of Ubuntu.  Windows is incapable of formatting to a Linux filesystem.  If you have the windows installation DVD, delleting the Recovery partition should not be a problem.  Up to you.

With 8GB of RAM, you should be able to get by without swap or with a small swap.

---

### Post by ubfan1 on 2016-01-08
I have no idea what the Windows installer does, so just starting with the blank SSD and letting it do its thing seems best.  Then you can alter things as needed.
  Think of swap as additional, slow memory.  If you have many running, mostly inactive programs, or a program with a hugh amount of data (think database), you can benefit from having swap (or if you hibernate of course).  Do you use any swap for the games you run?  If so, better put it on the SSD for performance (quick data access).

---

### Post by oldfred on 2016-01-08
Windows creates these partitions, not sure if created in advance if it then uses them correctly.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Yes, if you partition in advance you have to create all the partitions. I do have a couple of flash drives, gpt with only the ESP - efi system partition to boot ISO on the same partition. 

But once Windows is installed it would be like any other install. Do not shrink Windows too much, it likes lots of room. My one PC with Windows 8 is now nagging me to update to 10 but I had to move partitions around to give it more room. I had shrunk it to 40GB and did not plan to use it. But updates filled it and I know update to Windows 10 will require lots more space.

With Ubuntu you may have issues with nVidia. My older nVidia card GT620 worked with the open source driver, but newer cards seem to need nVidia driver. Best to use ppa to install or just use newest in Ubuntu repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by timbalisto on 2016-01-08
I'll be using Windows for gaming, and Ubuntu for everything else, so video drivers shouldn't be too big of an issue.

Thank you all. This has been incredibly helpful. I'm marking the thread as Solved.

---

