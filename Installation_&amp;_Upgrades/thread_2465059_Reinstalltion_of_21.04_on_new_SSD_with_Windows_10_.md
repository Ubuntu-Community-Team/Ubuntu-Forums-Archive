---
title: "Reinstalltion of 21.04 on new SSD with Windows 10 64"
date: 2021-07-20
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2021-07-20
I cloned my SSD onto a larger one (1 TB), The cloning software that came with the Crucial SSD successfully closed the Win 10 partition including the MBR and GRUB.  It did not clone the Ubuntu partition.  MBR and GRUB are on C: with 679 GB free space. D: is marked EFI AND HAS boot and ubuntu as subdirectories.   The ubuntu subdirectory has BOOT64.csv, grub.cfg, grub64.efi, mmx64.efi, and shimx64.efi.  Free space is 500 MB.  Drive G is EXT3 and has 112 GB free space.  I would like to put 21.04 on G.  QUESTION: will the 21.04 installer put the 21.04 system files and programs on G: without any special instructions?  Will the installer keep the existing MBR and GRUB?

Are there any other pitfalls in doing such reinstallation?

Thank you,

John

---

### Post by oldfred on 2021-07-20
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Do not understand MBR with .efi. Use of MBR is for old BIOS boot. And gpt partitioning is used with UEFI boot. But gpt has a protective MBR, just to have one entry saying drive is gpt, so old partition tools do not attempt to modify a gpt drive and cause damage.
The .efi bootable files are for UEFI boot in an ESP = efi system partition. And you should only have one ESP per device.

---

### Post by yancek on 2021-07-21
>   MBR and GRUB are on C 

The MBR is actually separate from any drive on the first sector of a bootable drive.

If you are seeing what you refer to as the 'D' drive (partition actually) then you state it has both windows and Ubuntu EFI boot files so they are both installed UEFI. 

>  Drive G is EXT3 

That is very unusual as historically, windows has not assigned 'drive' letters to Linux partitions.  Posting the boot repair output suggested above will give more specific information.  You might review the link below which is the official Ubuntu documentation on dual booting with windows 10.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

