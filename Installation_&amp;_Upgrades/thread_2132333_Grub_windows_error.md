---
title: "Grub windows error"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by sinsterizme on 2013-04-04
Hello, I just installed Ubuntu 12.04 and I can't get back into windows (no such device / file not found when trying to load windows boot loader from grub)

I have an SSD(sdb) and 2 TB HDD(sda). I had windows installed on the SSD containing 

- sdb1: 100MB (for EFI) flag: boot
- sdb2: 120GB (NTFS)

Upon installing Ubuntu, I set a 16GB '/' partition in my HDD as ext4 and a 4GB swap partition in my HDD as well.
I pointed the bootloader to sdb1. 

Now, I can boot into ubuntu fine but I can't get into windows from grub or BIOS. (selecting windows boot manager at bios just starts grub)
I ran boot-repair recommended setting to no avail.

I can find my windows efi files in /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi. I edited the grub windows bootloader entry that had an incorrect (seemingly arbitrary) root UUID to match the one that linux had and put the above filepath but it still gave me the error: no such file.

Any help is greatly appreciated :)

---

### Post by oldfred on 2013-04-04
It sounds like Windows is UEFI, but perhaps you did not install Ubuntu in UEFI. UEFI has to boot from gpt partitioned drives. Are both drives gpt?

Best to see all details. Run BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by sinsterizme on 2013-04-04
Thanks for your reply! I have done this: [http://paste.ubuntu.com/5677442/](http://paste.ubuntu.com/5677442/)

I believe only one of them is gpt.

---

### Post by oldfred on 2013-04-04
The only way you can dual boot is to go into UEFI/BIOS and change to BIOS/Legacy/CSM to boot Ubuntu and change to UEFI to boot Windows.
UEFI and BIOS write info to drive for system to boot. BIOS uses interrupts and UEFI uses drivers, so they write the system info differently and you then cannot dual boot from grub's menu.

You may be able to convert hard drive to gpt, but have to create an efi partition at the beginning of the drive. I do not like moving partitions, but you can do that. NTFS partitions require a chkdsk after any changes.

I have not tried to convert my last MBR drive. But all my new drives are gpt even though I still have BIOS.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

   GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

If 2TB drive is converted to gpt, you can then use Boot-Repair to convert your Ubuntu install from BIOS to UEFI without reinstalling.

---

### Post by sinsterizme on 2013-04-04
Thanks, but I don't understand why it isn't working now. My ubuntu install is UEFI and I'm pretty sure GRUB is loaded in sb1 (on the GPT drive). I can't gather why I can't dual boot from this... Just trying to understand all of this before I do anything drastic :) I need to be able to boot into win7 ASAP so if you know something I could change to get this working (Ubuntu doesn't need to work) I'd appreciate it.

---

### Post by oldfred on 2013-04-04
From UEFI in UEFI mode, you should be able to boot Windows. 

But I am not sure with grub2 efi boot loader on the gpt drive and Ubuntu in MBR partitions on the hard drive, that Ubuntu will work. Some have said it may, but the UEFI spec says you have to have gpt partitioning.

---

### Post by sinsterizme on 2013-04-04
I can't boot into windows at all though. Even when I select windows boot loader from UEFI it boots into grub. Ideally I just want windows booting I can tinker later :S

---

### Post by oldfred on 2013-04-04
Did Boot-Repair rename files. Do you have secure boot on. Some are able to boot with it off.

You can un rename:
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

Or you can copy the Windows boot efi file back.
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by sinsterizme on 2013-04-04
Hi, thanks for continually helping me. The advice you gave in the first paragraph did not work - I still boot into GRUB no matter what. I'd like to try your other suggestion: > Or you can copy the Windows boot efi file back. Where do I copy the bootmgfw.efi file to?

edit: I noticed that my Linux install has two /boot drives. One in / (which is in sda) and the other in sdb1. Maybe it's defaulting to legacy boot from the '/' mount point and hence windows can't start since its UEFI. Also grub is only installed on '/' not on the efi boot disk, would that be the problem?

edit2: Yeah I was correct - I disabled the MBR hard-drive in BIOS and rebooted into both ubuntu boot loader and windows boot loader and both times grub repair popped up and told me "could not find device [UUID]" where it was the UUID of my MBR... So how do I switch my EFI partition to point to the windows boot files? :|

---

### Post by oldfred on 2013-04-04
You need to look at your boot info report.

Some of the key info from your previous, which may have changed?

      ```
 
/EFI/Boot/bootx64.efi 
/EFI/ubuntu/grubx64.efi 
/EFI/Microsoft/Boot/bootmgfw.efi 

     sdb1: ____________________________

       File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

   Device                UUID
/dev/sdb1        1845-F08A                              vfat   


```

---

### Post by sinsterizme on 2013-04-05
Nothing changed... There must be something I can do ;(

---

### Post by oldfred on 2013-04-05
Did you copy this to the efi partition?

   Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Copy to this file?
/EFI/Microsoft/Boot/bootmgfw.efi

Mount point in LInux may be different:

 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by sinsterizme on 2013-04-05
Hey so I did what you suggested then ran windows startup repair off a usb (was a pain to make it UEFI) and now I can boot on windows when my second hard drive is disabled in bios. With the MBR enabled, I get the "windows is loading files" screen then the "start windows repair" or "start windows normally" screen but it is stuck in that loop. Should I simply delete the linux partitions on the MBR?

---

### Post by oldfred on 2013-04-05
UEFI and BIOS are not compatible, but a system can boot either one. Each writes boot info needed by operating system differently so one sytem cannot be UEFI and the other BIOS as they have to read the same info.

If you want to dual boot, you have to go into UEFI and change to UEFI to boot Windows and change to BIOS/CSM/Legacy to boot Ubuntu the way you have installed. Only if both systems are UEFI or both BIOS will it be easy to dual boot from grub2's menu.

---

### Post by sinsterizme on 2013-04-05
Okay, anyway I just removed the two partitions from the MBR and windows booted up fine. I'm now going to try installing dualboot on the SSD. Thanks for your help!

---

