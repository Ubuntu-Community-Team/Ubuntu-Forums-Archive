---
title: "[UEFI] Dual-booting Ubuntu 12.10 and Windows 8 - Razer Blade 2"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by ajdlinux on 2013-02-17
Hi all

Friend with a Razer Blade 2 (preinstalled with Windows 8) wanted me to install Ubuntu. We installed Ubuntu 12.04 from a Live USB in UEFI mode.

Upon rebooting we found that Ubuntu boots absolutely fine, however the Windows 8 options gave a "drivemap not found" error. As per the advice on the wiki we rebooted into the live USB and ran Boot Repair (log at [http://paste.ubuntu.com/1670620](http://paste.ubuntu.com/1670620)).

The new Boot Repair options didn't work either, so I tried adding some GRUB boot options of my own (based on [http://falstaff.agner.ch/2012/12/18/ubuntu-12-10-and-windows-8-with-secure-boot-mode/](http://falstaff.agner.ch/2012/12/18/ubuntu-12-10-and-windows-8-with-secure-boot-mode/), although without trying to get secure boot working). At this point I realised Secure Boot was still on and might be causing problems so I switched it off, but it didn't change anything.

I noticed that Boot Repair seemed to have overwritten the Windows boot manager files (bootmgfw.efi) with GRUB and stored the original Windows boot manager as a backup file, so I swapped them back. After doing this, the Windows boot manager would load and either reboot immediately or hang on a "Preparing Automatic Repair" screen.

Current BootInfo log is here: [http://paste.ubuntu.com/1671118](http://paste.ubuntu.com/1671118)

Any help would be much appreciated as this friend really wants Windows working for his games... Thank you!

---

### Post by ajdlinux on 2013-02-17
I should add that the system has a 64GB "cache" SSD in addition to the main 500GB HDD, which is where the installer decided to put Ubuntu. Would I be correct in suspecting that this may have something to do with it? Perhaps GRUB and the Windows Boot Manager having different drive orderings?

---

### Post by oldfred on 2013-02-17
Was this an Intel SRT? If so you may still have some RAID settings to remove.

It looks like Windows is in the sda hard drive as UEFI boot with gpt partitions.

But Ubuntu is on SSD with BIOS boot and MBR partitions.

You will not easily dual boot in that configuration. The only way to boot is to go into UEFI/BIOS and change from/to UEFI and which drive each time you want to change which system you boot.

Both systems need to be UEFI to easily dual boot. And how you boot install media is how it will install. You will need to reinstall on SSD and change to gpt partitioning and boot install flash drive in UEFI mode.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions. (If installing on same drive).
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some systems have poor UEFI designs and only boot Windows. So Boot Repair will rename Windows boot file to backup and rename shim or grub to Windows name to boot grub. Then from grub you can boot backup. But that only works is grub/Ubuntu is in UEFI mode.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    You also want an efi partition on the SSD, but may have to edit boot stanza with correct UUID.
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

    grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            > Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions. sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.

Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by ajdlinux on 2013-02-17
> **oldfred said:**
> Was this an Intel SRT? If so you may still have some RAID settings to remove.

It looks like Windows is in the sda hard drive as UEFI boot with gpt partitions.

But Ubuntu is on SSD with BIOS boot and MBR partitions.

You will not easily dual boot in that configuration. The only way to boot is to go into UEFI/BIOS and change from/to UEFI and which drive each time you want to change which system you boot.

Both systems need to be UEFI to easily dual boot. And how you boot install media is how it will install. You will need to reinstall on SSD and change to gpt partitioning and boot install flash drive in UEFI mode.

The machine is set to boot only in UEFI mode. I'm a bit curious as to why the SSD isn't GPT though.

---

### Post by oldfred on 2013-02-17
I do not know how Intel SRT works, but it uses RAID and seems that it is using the SSD just as a cache to speed things up.

---

