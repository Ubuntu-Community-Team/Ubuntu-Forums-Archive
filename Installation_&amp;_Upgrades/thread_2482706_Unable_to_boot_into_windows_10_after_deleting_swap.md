---
title: "Unable to boot into windows 10 after deleting swapfile"
date: 2023-01-08
forum: Installation &amp; Upgrades
---

### Post by ananas-comosus on 2023-01-08
I had ubuntu desktop running nicely on a microsd card in a usb card reader. I wanted to try zram as a replacement for swap so I followed this procedure to disable and remove the swapfile:Run the following command to deactivate the swap file: swapoff -v /swapfile . Use a text editor to remove the /etc/fstab entry. Instead of deleting the line I commented it out thinking this was safer. Run the following command to remove the swapfile: rm -f /swapfile. After this procedure I quickly realised that the flash drive file system was unwriteable. I rebooted hoping the situation would resolve itself but I could not boot from the flash drive, and got the message "missing operating system". Thankfully I had an ubuntu 22.10 live usb that I booted into. My windows 10 ssd was visible and readable but the flash drive had no partition visible in gparted. 

After trying a few solutions I came to trying to fix the flash drive filesystem with e2fsck -b $BACKUPSB /dev/sdb replacing $BACKUPSB with different superblock backup locations but that didn't work so I used the live usb to reinstall ubuntu 22.10 on the flash drive. The flash drive booted okay with the new system installed but when I shutdown and removed the flash drive so I could boot into windows I got the same message about missing operating system. I am figuring that the message was always about the missing windows because the flash drive was unreadable and was bypassed by the bios.

I made sure to not install grub on the windows disk. I am not sure how an operation on the flash drive affected the ssd. When the system was working ok the bootloader on the flashdrive would offer to dual boot windows or ubuntu but if the drive was not inserted windows would load as normal, which is exactly how I want it. As it is now I have a working ubuntu 22.10 on the flash drive, the windows 10 partition is readable and healthy in 'Disks; I just can boot to it and the grub on the flash drive does not recognize it. I am trying not to panic and do this the right way so I got boot-repair and the report is at [https://paste.ubuntu.com/p/WR79sPmtCY/](https://paste.ubuntu.com/p/WR79sPmtCY/) . Any help to get things right again will be appreciated.

---

### Post by oldfred on 2023-01-09
Not sure why you have Windows in old BIOS/MBR configuration.
Microsoft has required vendors to install in UEFI/gpt mode since 2012. So you must have installed yourself or upgraded from an old Windows 7 BIOS/MBR install.

And sdb is UEFI/gpt.

UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch. Or grub booted in UEFI mode cannot boot another system in BIOS mode. You only can boot from UEFI boot menu, or in your case unplug external drive. UEFI/BIOS may need settings to default boot in correct mode.

Did you reinstall to flash drive or totally reinstall grub converting from grub-pc(BIOS) to grub-efi-amd64(UEFI).

Best to also have Windows in UEFI mode, but that will totally erase drive in conversion from MBR to gpt.
You can install grub-pc to external drive, either manually or with Boot-Repair.
Or always boot from UEFI boot menu.

---

### Post by ananas-comosus on 2023-01-14
Thanks for your input . This is a laptop bought new around 2015. I upgraded the hard-drive to an SSD a while back and probably did the MBR install at that time. I don't know if I misunderstand your comments regarding UEFI & BIOS being incompatible. The system is now working as I want it and the only changes I did were to use a windows 10 installation usb recovery environment to mark the windows 10 partition as active with diskpart and configure grub on the flash drive to probe for other OS. Again, I am not sure if I had "reinstall to flash drive or totally reinstall grub converting from grub-pc(BIOS) to grub-efi-amd64(UEFI)". I had formatted the drive using Disks then just allowed the Ubuntu installer to do its thing, please note this was after the windows partition had already been messed up so I am still not sure why the windows partition would have become inactive by me messing with the swapfile on the original flash installation. 

If I understand you correctly my system should not be working as the grub on the flash drive is installed in UEFI mode and my windows 10 drive is MBR? If that is the case, have I recreated a situation that  will inevitably crash again? Or am I misunderstanding your comments? I don't want to mark this as solved when the solution I found is not sustainable.

---

### Post by oldfred on 2023-01-14
Older UEFI systems can boot in UEFI mode or BIOS mode.
But modes are not compatible. And most UEFI require you to set in UEFI/BIOS the default mode for installed systems. Many will auto switch if one mode does not work, but some just complain about no boot files for mode you specified. That happend when you have installed in one mode, but system is set to boot in other mode.

Windows also only installs in UEFI mode to gpt partitioned drives and only in BIOS boot mode to MBR drives. 
Ubuntu can boot in either mode from either type of partitioning, but better to always use gpt. With gpt in BIOS mode, you have to have a bios_grub partition or in UEFI mode you have to have an ESP - efi system partition. 

For both Windows & Ubuntu, how you boot install media UEFI or BIOS is then how it installs & how UEFI should be set as default boot mode.
But booting external drive is normally a choice from UEFI boot menu. For installer you have two boot modes, one clearly UEFI as UEFI: xxx and one that is BIOS as xxx where xxx is name or label of flash drive.
Full install to external drive required boot loader on external drive. With BIOS that should just be grub in MBR. Each drive has only one MBR, so only one system can be default boot for each drive. With UEFI, all installs have boot files in ESP.

---

### Post by tea for one on 2023-01-15
> **ananas-comosus said:**
> If I understand you correctly my system should not be working as the grub on the flash drive is installed in UEFI mode and my windows 10 drive is MBR? If that is the case, have I recreated a situation that  will inevitably crash again? Or am I misunderstanding your comments? I don't want to mark this as solved when the solution I found is not sustainable.

Dual boot with Windows in Legacy (mbr) mode and Ubuntu in UEFI should be avoided.
As your system is working OK at the moment, I think that luck is temporarily on your side.

To be more robust in the future, please give serious consideration to installing Windows 10 in UEFI mode with GPT.

Finally, I assume you have backups of both Windows and Ubuntu personal files.
The ice, on which you are skating, will start to develop hairline cracks and ...................

---

