---
title: "New install dual boot in two disks and dual GPU AMD + Nvidia"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by davide445 on 2018-12-19
Hi all
first time Linux user (second in reality, but the first try was many years ago), I have ordered a new PC parts where I wanted to install both Win10 (migrating the disk from actual PC) and also Ubuntu Budgie. This will be the configuration

AMD Ryzen 5 2600X
Mobo ASUS PRIME B450-PLUS AMD B450 AM4 
Ram Corsair Vengeance RGB DDR4 3200MHz 32GB (2X16GB) - CMR32GX4M2C3200C16
SSD1 Crucial MX300 275GB (Win10 existing installation)
SSD2 Crucial MX500 500GB (Linux new installation)
HDD Toshiba 3TB (currenlty with NTFS file system, maybe to be partitioned in half for Win and Linux access)
GPU1 Sapphire HD7950 Dual-X with Boost
GPU2 Kfa2 GTX 1070 EX 8GB
PSU Corsair TX750M 
Case Fractal Design Meshify C Midi Tower

I'm not a sys admin but just a long time Win user with some technical expertise. 
Want to understand with your more expert help if this is a too difficult configuration and might i.e. start with just one GPU, and there are specific incompatibilities that will make my life hard (i.e. GPU drivers, or RAM).

---

### Post by oldfred on 2018-12-19
Very new hardware may not easily work or will require boot parameters or perhaps even newer kernel & support software that is being updated for that new hardware but not yet in Ubuntu distribution. 

When I built my new system in early 2016, I had to install 16.04 several months before it was finalized. I knew it could still get some update that might break install, so did not consider it for any thing critical until 16.04 was finalized.
The 19.04 install does work on my 2016 system and it does have newer kernel. I still use and prefer to only use LTS long term support versions as main working install.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu) 
            Ubuntu 18.04 with updates from ppas
Ryzen 7 2700 / Ryzen 7 2700X / Core i7 8700K Linux Gaming Performance With RX Vega 64, GTX 1080 Ti
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1) 
    
With multiple drives only use Something Else install option and be sure to boot in UEFI boot mode.
You do have Windows in UEFI boot mode?

---

### Post by davide445 on 2018-12-19
Currently is in Legacy mode, but is still installed on the old PC since the new parts are coming in the next week or so.
What you tell me sounds a bit discouraging, I'm not an expert at all.
I suppose the safest way is to run Linux in virtual machine, but this is really not my preferred way since will need to run heavy computing on the Nvidia GPU.
Make sense to start step by step by first running Windows, next trying to install Linux on the second disk with just one GPU?

---

### Post by CatKiller on 2018-12-19
Mixing the GPUs in one system is not going to be great.

The AMD stuff will work fine with all open source standard things. The Nvidia won't.

You can't get the Nvidia card to clock up above the minimum speed without the proprietary driver, and the proprietary driver will likely prevent the AMD card from working.

Having your host use the AMD card and open everything, and installing the proprietary driver in a VM for computing might work.

Personally, I would just ditch the AMD card. Other than that, the hardware should work fine.

---

### Post by yancek on 2018-12-19
If you are certain that windows 10 is installed Legacy and there is no sign of an EFI partition, you would simply need to install Ubuntu in Legacy mode also.  See the link to the Ubuntu documentation below.  It gives a lot of details about dual booting UEFI but has other useful information.  Mixing a Legacy install with an EFI will lead to problems, that is also discussed/explained at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since you will be installing your windows system on a separate drive from Ubuntu, you need to decide where you want the bootloader for Ubuntu, on the primary drive or on the second drive on which you install Ubuntu.

If you are planning to use the 3TB drive only for data to be share between windows/Ubuntu, you can format it ntfs as there is software available to read/write to an ntfs filesystem with Ubuntu.

---

### Post by oldfred on 2018-12-19
BIOS/MBR is from the original PC in the 1980s. With various fixes to make it work with newer hardware over the years.
UEFI/gpt was developed originally by Intel in early 2000s as major update to booting systems. First adopted by Apple when Mac was changed to Intel chips. Then it was EFI. Now Intel released it to independent group and EFI became UEFI v1. When Microsoft required UEFI for new Windows 8 systems it was UEFI version 2 with minor version updates since then.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by davide445 on 2018-12-19
> **CatKiller said:**
> Mixing the GPUs in one system is not going to be great.

The AMD stuff will work fine with all open source standard things. The Nvidia won't.

You can't get the Nvidia card to clock up above the minimum speed without the proprietary driver, and the proprietary driver will likely prevent the AMD card from working.

Having your host use the AMD card and open everything, and installing the proprietary driver in a VM for computing might work.

Personally, I would just ditch the AMD card. Other than that, the hardware should work fine.

For sure I will need Nvidia CUDA driver to have the compute part working. I was thinking to maintain the other GPU to offload the 2D/3D working from the Nvidia while computing. But in case will not use it.

> **yancek said:**
> If you are certain that windows 10 is installed Legacy and there is no sign of an EFI partition, you would simply need to install Ubuntu in Legacy mode also.  See the link to the Ubuntu documentation below.  It gives a lot of details about dual booting UEFI but has other useful information.  Mixing a Legacy install with an EFI will lead to problems, that is also discussed/explained at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since you will be installing your windows system on a separate drive from Ubuntu, you need to decide where you want the bootloader for Ubuntu, on the primary drive or on the second drive on which you install Ubuntu.

If you are planning to use the 3TB drive only for data to be share between windows/Ubuntu, you can format it ntfs as there is software available to read/write to an ntfs filesystem with Ubuntu.

I [discovered]("https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10") is possible to convert a Win10 installation from Legacy to UEFI mode using MBR2GPT, but being another complex operation want to ask if sticking with Legacy will create me problems with the new platform.

> **oldfred said:**
> BIOS/MBR is from the original PC in the 1980s.  With various fixes to make it work with newer hardware over the years.
UEFI/gpt was developed originally by Intel in early 2000s as major  update to booting systems. First adopted by Apple when Mac was changed  to Intel chips. Then it was EFI. Now Intel released it to independent  group and EFI became UEFI v1. When Microsoft required UEFI for new  Windows 8 systems it was UEFI version 2 with minor version updates since  then.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Appear Legacy (BIOS) / UEFI are irrelevant if I have less than 2TB primary disk, so I'm safe?

---

### Post by oldfred on 2018-12-19
When you purchase your new Corvette, you always have them go back and install an old Vega engine just because it has been around for years. :)

You can dual boot with Windows in BIOS boot mode & Ubuntu in UEFI boot mode, but not using grub. UEFI & BIOS are incompatible and once you start booting in one mode you cannot switch. But some just use UEFI boot menu anyway and that is the only way you can then boot.
Since Ubuntu is on separate drive, I would still use gpt partitioning and include both the ESP - efi system partition (for future use) and a bios_grub partition for grub to install correctly on gpt partition drives for BIOS boot.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry: 
[*]Not swap partition for 18.04 or later, it uses a swap file like this entry in fstab: 

Then only use Something Else install option to choose which partition is / & which is /home or other system partitions. If you are using data partition(s) you set those up after install. 
[/LIST]

---

### Post by davide445 on 2018-12-20
That's interesting and detailed but my problem is I normally use GUI for all my activities and didn't know where to start for all these configurations.
What about if in the Ubuntu installer there is something can guide me on these tasks.

---

### Post by CatKiller on 2018-12-20
The partition manager in the installer is displayed entirely graphically (it's better that way, as well as being more comfortable for a new user). The "something else" option lets you set up the partitions however you want.

Use Windows to edit Windows partitions, though. It is finicky and fragile.

---

### Post by davide445 on 2018-12-20
Just to recap a procedure
- Migrate Win10 from old to new PC to setup all the components, maintaining current Legacy boot mode
- Use only Nvidia GPU from the beginning
- After all is working start setup of Ubuntu on the secondary disk, using the guided procedure to create the various partitions (I hope will be "idiot proof" since I have no idea about what the various partitions means)
- If the system didn't boot on Linux evaluate possible incompatibilites
- Maintain current HDD in NTFS since can be read also from Linux

Just to know if you agree. About selecting the OS from whom booting, there is some specific tool to achieve that in a dual disk configuration.

---

### Post by oldfred on 2018-12-20
If you disconnect either physically or with UEFI settings, a default install of Ubuntu in UEFI boot mode will make drive MBR and only add one partition / (root).

If you want more than one large / partition, you either use gparted to create partitions in advance, or use Something Else to manually create partitions. I think gparted is slightly easier to use.

Your UEFI will have boot menu, grub will have boot menu if Windows fast start up or hibernation is off. So you can use either to select which system to boot. In BIOS/Legacy boot mode you are selecting which drive to boot from as boot code starts from MBR which is very first sector of a hard drive.

---

