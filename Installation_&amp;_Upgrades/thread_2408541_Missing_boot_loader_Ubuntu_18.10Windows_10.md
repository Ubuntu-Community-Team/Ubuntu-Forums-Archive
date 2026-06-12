---
title: "Missing boot loader Ubuntu 18.10/Windows 10"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by dralcohen2 on 2018-12-19
As there are a lot of similar threads, I'm a bit embarrassed to post this, but I can't seem to find a solution that works.

Brand new system. 2 SSD drives. I installed Win10 on 1. Then I disconnected it and installed Ubuntu 18.10 on the other. I was hoping to set up a dual boot.

The system boots straight into Ubuntu. Here is the boot info: [http://paste.ubuntu.com/p/Q6sBscvmBC/](http://paste.ubuntu.com/p/Q6sBscvmBC/).

If possible, I'd really rather not have to reinstall either OS (which seems to be recommended in a lot of threads). 

If it helps, I can boot into Ubuntu or Windows by selecting the appropriate drive in BIOS. os-prober is not finding Windows, even when the partition is mounted. update-grub doesn't fix it.

I'm pretty new at this, I must confess to only partially understanding many of the previous responses, so more details and guidance is good.

Thanks for your help and patience!

---

### Post by yancek on 2018-12-19
You have a mix of Legacy/CSM install of windows and a UEFI/GPT install of Ubuntu, they don't mix well as you have found.  I know that a Legacy install of Linux will not boot a windows EFI install but am surprised that an EFI  Ubuntu/Grub doesn't recognize the Legacy windows.  Take a look at the link below on problems with mixing boot modes.  There is an explanation of how to convert from UEFI to Legacy/GPT on the Ubuntu page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dralcohen2 on 2018-12-19
Thank you.

If I understand correctly, Ubuntu is UEFI/GPT and Windows is Legacy/CSM (I have no idea how that happened). I changed the Bios to legacy only (right now it's either) and it booted Windows. So the first step is to get them installed the same way? Rather than changing Ubuntu to Legacy, could I change Windows to UEFI? I found a few posts that claim to be able to do that. Would something like this work?

[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

or maybe

[https://www.disk-partition.com/gpt-mbr/change-legacy-to-uefi-4348i.html](https://www.disk-partition.com/gpt-mbr/change-legacy-to-uefi-4348i.html)

Assuming the answer is yes and it works (ha!) how do I then set up grub?

---

### Post by oldfred on 2018-12-20
Both Windows & Ubuntu install in the same boot mode UEFI or BIOS as you boot install media from UEFI boot menu.

Since 2 drives you can dual boot in your your configuration, just not from grub.
UEFI & BIOS are not compatible and once you start booting in one mode, you cannot switch. Or grub can only boot other installs in same boot mode.

But you can always use UEFI boot menu. Most systems will work without changing other settings from UEFI to Legacy/BIOS. A few older ones may need you to change UEFI boot mode settings.

Not sure how well a Windows conversion works. I would make sure I have good backups.
And I would disconnect Ubuntu drive when working on Windows. I know with old BIOS, Windows wold install boot partition to default boot drive in BIOS. If that boot  drive was an Ubuntu drive, Windows would not see the ext4 partition and just overwrite part of it, destroying it.
You may not have to physically disconnect drive, but just change setting in UEFI to turn off a drive.
But if you disconnect drive,  you may have to recreate UEFI boot entry with efibootmgr or by reinstalling grub (which uses efibootmgr to add entry).

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by dralcohen2 on 2018-12-20
Thank you.

The built-in Windows MBR to GPT function didn't work (it couldn't create an EFI partition). I tried a couple of apps that claim they can change MBR to GPT without data loss, but the free versions don't have that functionality and I was feeling too cheap to shell out the $50 to try.

So...I re-installed Windows as UEFI. In case this helps anyone, I used Rufus to make a EFI USB drive, disabled secure boot, changed the boot setting to UEFI only, physically disconnected all other drives, wiped the drive and changed it to GPT, and then installed Windows. After installation, I changed the BIOS settings back (legacy + UEFI and secure boot). I then reconnected all drives, booted into Ubuntu (using BIOS to select the drive), and ran os-prober. It found Windows! I then ran update-grub (which listed Windows this time), changed the boot order of the drives to make the Ubuntu partition first, and rebooted and...it worked! Oh lovely purple screen.

So, I now have to spend a few hours setting up Windows again, but at least I have a working system.

Thank you for your help and I hope this helps someone in the future.

---

