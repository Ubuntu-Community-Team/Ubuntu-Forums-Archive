---
title: "Grub not installing."
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by tarat on 2012-05-13
I just put together a new PC, and decided to dual boot windows (don't have a copy yet) and linux. I have a 120GB SSD (sda) and a 1TB HDD (sdb). I thought I'd put Windows on the SSD, Ubuntu on a 50GB partition on the HDD, and leave the rest for shared storage. Before I started today, everything was totally empty, so reformatting my HDD is not a big deal at all.

I started all of this hours ago, so I can't remember exactly what combinations I've tried, but they include automatic (whole disc) installation, creating just an ext4, swap, and empty partition, adding an EFI partition, then trying to install grub afterwards or update to grub2 (with every set of instructions I've tried, there always comes a point where the terminal commands just don't do anything). 
I've tried three different distros in case that was the problem (spent an hour upgrading ubuntu only to have it not boot at all). All of it with a live usb, I tried it twice with the start up disc creator and once with unetbootin. The total number of times that I've tried to install  it today is probably about ten now. 
When I tried installing ubuntu everything was hunky dory until I tried to restart, then I'd get stuck during the system checks, or it would kind of boot, but after a bunch of clicking I'd end up in the shell (which I have no idea how to use). I tried linux mint after that, at the end of installation it tells me that grub failed to install and then crashes.

Anyway, I'm getting so, so, so very sick of this. Is there some sort of idiot proof guide to setting up my partitions so that grub will actually work? Or is it more likely that something else is at the root of the problem? I don't want to put grub on my SSD, because I'm sure that windows will just erase it when I install it.

---

### Post by darkod on 2012-05-13
It depends on your system. For example, you are probably aware that you need the EFI system partition only if you are using EFI to boot. Otherwise, you don't.

So the first question would be are you using EFI boot or BIOS boot?

Then, if you use gpt table on the disk, you need a small bios_grub partition for grub2. If you use msdos table you don't need this.

If you want, you can run the boot info script which will show many details in your system but it depends in what state it is now after all the things you tried. The link for the script is in my signature. You can post the results as explained there so we can have a look.

---

### Post by tarat on 2012-05-13
Well, it says "press delete to enter uefi bios mode" on that first screen that pops up, and my flash drive pops up as uefi within the bios when I set up the boot priority. Other than that I'm afraid I don't know (If it's dependent on the hardware though, I *do* know all about that)

I'm in the middle of giving it another go (couldn't boot, probably should have selected "try ubuntu") but I'll run that script once I'm able to, assuming this install doesn't work either.

---

### Post by oldfred on 2012-05-13
Since you have the UEFI option, you have to decide if you want UEFI. That determines how drive(s) will be formated and partitioned. Ubuntu can use gpt with either BIOS or UEFI but needs different partitions.

Windows will only install in UEFI mode if drive is partitioned with gpt. If in BIOS mode, Windows must be installed with MBR.

You can have SSD in MBR and 1TB drive in gpt. Windows will read gpt drives NTFS formated shared partition.

I often suggest just creating the partitions you need for both UEFI or BIOS and as gpt if only booting Linux on that drive. 

Everyone who has successfully installed Ubuntu in UEFI mode has partitioned in advance. Not sure if you can boot Windows in BIOS & Ubuntu in UEFI. That may work from UEFI/BIOS menu but not the chainload from grub.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

It is my understanding that if you boot either Windows or Ubuntu Installers in UEFI mode they install in UEFI, if booted in BIOS they install to BIOS. 

Change label in efi menu.
Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter.

---

### Post by tarat on 2012-05-13
Well, now I got it to boot (bios override, selected non-uefi live USB, continued standard set up) but I have the same problem I did my first go at it- no matter what I try to install, it tells me that package dependencies cannot be resolved. I wonder if this is less of a pain in the *** to fix than the UEFI boot.

---

### Post by tarat on 2012-05-13
Just went and updated. Now everything works. :D
Time for a drink.

If anyone else finds this with a search, I have an ASUS Sabertooth Z77 motherboard, so this should work with that and any others with the same BIOS. Go to advanced mode in the BIOS, go to the boot submenu, scroll all the way down to boot override. My USB came up as UEFI Kingston and plain old Kingston without UEFI in front of it, I clicked plain Kingston. Install comes up as usual, went into custom setup (I think it called it "something else" though). Made sure that the bootloader installed on the disc that I wanted it to, created just one 50GB ext4 partition. So I guess I just went with the BIOS over the UEFI option because it was so much easier.

---

### Post by YannBuntu on 2012-05-14
@tarat: thanks for your feedback. For our information, please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ? (it won't change your boot)

---

