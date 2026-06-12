---
title: "Going to UEFI, broken something!"
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by ogp on 2017-07-18
Hi, 

I'm trying to go from a Legacy boot to a UEFI boot on a current installation of Linux mint, and also upgrade to a new installation of Ubuntu Gnome.

It seems that my existing installation is running in Legacy mode. 

I've created an EFI partition at the start of my system drive, flagged it with 'boot' and run a live USB of Ubuntu Gnome, which appeared to install correctly. 

I've changed the 'CSM Support' in my BIOS (Gigabyte) to 'Never' and tried to boot, and it won't boot. It doesn't appear to find any bootable drives to boot from. 

It will boot from the bootable Ubuntu Gnome USB stick (which is how I am posting this). 

I'm slightly at the end of the my abilities and knowledge but have tried running Yannubuntu's boot-repair and it claimed to have repaired the boot, but it still doesn't want to boot. 

The boot info script is in pastebin here: 

[https://pastebin.com/vGvZq4HB](https://pastebin.com/vGvZq4HB)

I have 'CSM Support' set to 'Never' in the BIOS. 

What do I need to do to get the machine to boot from the hard drive? 

Thanks, in advance, for any help.


Oli.

---

### Post by oldfred on 2017-07-18
UEFI standard is gpt partitioning. While some have managed to install in UEFI mode to a MBR(msdos) drive it is not the normal way.
If dual booting from Windows, Windows only boots from gpt with UEFI, and Windows only boots from MBR with BIOS. But Ubuntu can use gpt and boot in either UEFI or BIOS boot mode if you have correct supporting partitions.
So for any drive that will be Ubuntu only I suggest using gpt and include both an ESP - efi system partition for UEFI boot and a bios_grub partition for BIOS boot, if you may want to change boot modes. Re-install of grub is then all that is required to switch, not full reinstall of system.

You show sda & sdc as DOS or MBR and sdb as gpt. Best if all drives are gpt once you decide to use UEFI.
And if no Windows you can convert drive, normally without data loss, but still need to have full backups as things can happen.

       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Be sure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966 ]("http://ubuntuforums.org/showthread.php?t=1718966") 

For more general info on UEFI install, see link in my signature below.

Since any drive later may become a boot drive and it can be difficult to add an ESP to the beginning of a drive, I prefer to have both the ESP & bios_grub as first two partitions on every drive, even if currently just a data drive. But I like to at least have a minimal install of Ubuntu on every drive, even if just a data drive, for emergency boot, if needed.

---

### Post by ogp on 2017-07-18
oldfred, 

Thanks very much for your input. I had to read it several times but I think I've understood it. Are you saying that I need to make each of the drives into gpt form, but that when I have them all in gpt form then the machine should boot? 

I don't have windows on the machine and am very unlikely to want to install it again so am happy to move to an entirely UEFI / gpt setup.

I'm just following the link you provided for conversion from MBR to gpt and will see how I get on. However a couple of other questions: 

- How should I have the BIOS set? Should I have 'CSM Support' set to 'never'? My motherboard is a dual-BIOS affair which seems to support both simultaneously which confuses me. 
- Will I be able to get back into (and run) my old Mint installation on sda2? This was created in an MBR configuration. 

Thanks, 


Oli.

---

### Post by oldfred on 2017-07-18
While I do not think every drive has to be MBR as I have seen several installs to MBR drives, with an ESP on a gpt drive. And the Ubuntu installer which boots in either UEFI or BIOS is usually on a MBR partitioned drive with one FAT32 partition.

The main difference with UEFI or BIOS boot is grub2. You should be able to reinstall Mint's grub2 in UEFI mode. Often easier with Boot-Repair as it walks you thru process. If using Ubuntu's grub to boot, it may not care how Mint's grub is configured as it will just load kernel & boot it.

All my systems need UEFI or UEFI only and all CSM settings off.
But have seen one or two systems where users had to have CSM on, but still select UEFI boot for both USB installer and actual install.
My Asus motherboard has CSM, UEFI and (UEFI or CSM, UEFI first). But the UEFI first only booted in CSM/BIOS mode. Sometimes you just have to experiment.

In UEFI mode, grub only installs to the ESP - efi system (FAT32) partition on drive seen as sda. If you do not have a gpt drive with ESP as sda, grub fails to install. Depending on your drives, you could also disconnect MBR drives, so you only have Ubuntu drive as gpt with the ESP so it is seen as sda.
I also have found that you need to have drives plugged into SATA ports in SATA port order, not skipping any ports. I had a sdf flash drive that on reboot became sdb and every other drive went up a letter. I had skipped SATA1 port and flash drive or UEFI/BIOS then put flash drive in that spot.

---

### Post by ogp on 2017-07-19
oldfred, 

Thanks again for your help. The machine is working now; I think I managed to change the filesystem on sda to UEFI and then cheated a little and re-installed Ubuntu-Gnome on sda3 once I had access to it. The process of doing that updated GRUB which also found the existing installation of Mint and gave me access to that as well, which was a pleasant surprise (although unnecessary). I've subsequently put Ubuntu Mate on a third partition on sda and that works very nicely and will probably become my regular 'machine'. 

So, all is well that ends well and I'm happy with it, and grateful for your help. However I now have two very small partitions at the start of sda - the first one is a fat32 partition of 250Mb, flagged boot and esp, mount point boot/efi. The second one is not formatted (unknown filesystem), 100Mb in size and with the flag bios_grub. Are both of these necessary? If so, why? If you know of a good online tutorial then it may be easier to send me the link! 

Thanks again for your help. 


Oli.

---

### Post by oldfred on 2017-07-19
If booting in UEFI mode you have to have the ESP - efi system partition (FAT32 with boot flag). That is where grub has the boot files that the UEFI uses to start booting.

If only using UEFI, you do not need the bios_grub partition. I normally keep a bios_grub on my systems, just in case I want to go back to or test BIOS boot. But it only needs to be 1MB, must be unformatted and since unformatted will show as an error in gparted. Gparted wants to see formatted partitions and does not like partitions it cannot mount.

I also add both ESP & bios_grub to every drive, even if currently only a data drive. But normally also have some install of an Ubuntu flavor on every drive.

If you look at the link in my signature, the very last part is this:
 Acronyms:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

