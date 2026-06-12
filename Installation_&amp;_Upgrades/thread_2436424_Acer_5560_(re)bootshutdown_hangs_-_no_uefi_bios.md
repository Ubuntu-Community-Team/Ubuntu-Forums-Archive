---
title: "Acer 5560 (re)boot/shutdown hangs - no uefi bios?"
date: 2020-02-06
forum: Installation &amp; Upgrades
---

### Post by rolandow on 2020-02-06
Hi,

Yesterday I spent hours on trying to get Linux to my Acer Aspire 5560. Both Ubuntu and Linux Mint had the exact same problems.

Installation from USB stick went flawlessly. But then when I need to reboot, problems begin.

Shutting down or rebooting the machine usually hangs it. I have to shut it down with holding my power button. Then on boot, sometimes it boots, sometimes it won't.

I tried adding acpi=noirq to /etc/default/grub .. 

Also when rebooting, all of the sudden by USB controller doesn't initialise anymore. In the boot process, I see it's trying to do so, it resets a bus a few times, and eventually it continues with booting. Mouse and keyboard won't work. Apparently the USB drivers could not be loaded properly.

I never had any issues with Windows, so I was thinking this could be a UEFI issue. But when I enter my BIOS setup, I see no UEFI or safe boot options whatsoever.

So yesterday I got to the point where I thought; ok, Windows it is then. But today I thought let's see if the Ubuntu community can help me, because I'd really rather have Linux on that machine.

By the way, I also read something about GPT? I don't need to dual boot with Windows or anything like that. So maybe I should follow some procedure to remove partitions and set the boot type to GPT somehow? Instead of MBR?

Thanks in advance!

---

### Post by oldfred on 2020-02-06
What version of Windows did you have.
Microsoft required UEFI/gpt for Windows 8 when released in 2012.
Most Windows 7 systems were BIOS/MBR, but a few were UEFI/gpt.

Most systems also need UEFI/BIOS update to latest available and if SSD, SSD firmware update.

Post this from live installer:
sudo parted -l

---

### Post by rolandow on 2020-02-07
The previous system was Window 7, it also has a Windows 7 product key sticker on the back. So I doubt if it's a UEFI system. I can't find anything related to this in the bios. Not sure if UEFI is always shown to the user. Maybe some systems have UEFI without the option to disable it?

I am trying again now with the EFI flag on my boot partition. See if that helps. So my partition tables are already destroyed. I now created a boot partition on fat32 with flags boot and efi. The rest of it is ext4 mounted to /.

I will search for bios updates as well. But I'm afraid I have to install windows to install the bios updates. I'll get back here if I found a solution.

This is my partition table now:

Model: ATA KSS240 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  538MB  537MB  primary  fat32        boot, esp
 2      538MB   240GB  240GB  primary  ext4

---

### Post by yancek on 2020-02-07
If you don't have any information in the BIOS firmware of the computer indicating that it is UEFI capable, why would you create an EFI partition and try to install EFI?  Some reference to EFI should show in the BIOS although I doubt you would see much if anything from a windows system.  You have the old style msdos partitioning on the drive so just do a Legacy install of Ubuntu.

---

