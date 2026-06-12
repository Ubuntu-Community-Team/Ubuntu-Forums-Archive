---
title: "[Boot-Repair] Using boot-repair to fix erased EFI partition"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by carlh on 2019-06-17
I accidentally hosed my EFI partition on a dual boot Lubuntu/Windows disk. I tried to recover by clearing and reformatting the EFI partition as FAT32 with gparted,
then used the boot-repair bootable USB to run the recovery. Initially it says "GPT detected. Please create a BIOS-Boot partition...", but used the advanced options to select
the separate boot/efi partition in Grub Location. It seemed to run OK,  but then when booting it flashed "failed to open /EFI/ubuntu/grubx64.efi" or something like that.

Can anyone give me advice on restoring the EFI partition? It seems that wiping this partition also wiped access to the Windows recovery partition. My linux and windows
partitions all seem OK, but googling how to boot one of these from a grub cli from a bootable USB didn't lead to a straightforward way to access the hard disk images.

I uploaded my boot-repair info to [http://paste.ubuntu.com/p/g5YbGs6b6w/](http://paste.ubuntu.com/p/g5YbGs6b6w/)

Thanks for any advice!

---

### Post by oldfred on 2019-06-17
UEFI uses GUID to know the ESP - efi system partition. So when you recreated it, it got a new GUID & you have to recreate UEFI boot entries. For Ubuntu you can do a full reinstall of grub which uses efibootmgr to add UEFI entry. But you can just run efibootmgr to add entry.

For Windows you will have to run Windows repairs as you are missing both the UEFI entry & the /EFI/Microsoft folder with Windows boot files in the ESP.

       sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 2

I also like to have the fallback entry that uses /EFI/Boot/bootx64.efi, but Windows may overwrite bootx64.efi with its version on its repairs:
      
  sudo efibootmgr -c -g -w -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/sda -p 2 

 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by carlh on 2019-06-18
Thanks so much! I tried the above commands using the boot-repair OS, and had no luck-- same symptoms. The commands seemed to work, though it said there already was an "ubuntu" entry.

 So I tried running boot-repair with the advanced options to purge grub and reinstall (since you said full reinstall should fix it). It seemed to do all the installs OK from the copy and paste shell commands. After all that, it still failed with the same message.

I took a photo of the boot error that flashed, it said "Failed to open \EFI\BOOT\grubx64.efi". I'm not sure where that came from-- I couldn't figure out how to use efibootmgr to view details including the -l paths-- maybe it was from an old "ubuntu" in bootnum 000. I noticed there was grubx64.efi in the ubuntu folder, so I copied it and the config into the Boot folder, then booting worked! I'm not sure what the correct efibootmgr command would have been, but at least I am back with a working system.

Somehow the grub update seemed to have hosed my /etc/resolv.conf, so broke DNS. I think it renamed the prior one, so I was able to get back by renaming my /etc/resolv.conf.old

---

### Post by oldfred on 2019-06-18
I have seen that error or similar before, but it does not make sense.
I have a full install and do not have /EFI/Boot/grubx64.efi. That file is just in /EFI/ubuntu.

You may want to check UEFI boot entries.
sudo efibootmgr -v

You can houseclean any old or obsolete entries with efibootmgr. 
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B 

This was your original 0000 entry, but the reinstall of grub probably replaced it or renumbered it.

Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

---

