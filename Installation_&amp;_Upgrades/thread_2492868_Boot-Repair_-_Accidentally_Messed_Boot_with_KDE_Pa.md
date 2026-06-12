---
title: "Boot-Repair - Accidentally Messed Boot with KDE Partition Manager by Resizing Space."
date: 2023-11-25
forum: Installation &amp; Upgrades
---

### Post by robertpettersen on 2023-11-25
Just seeing if anyone can provide some help. I'm trying to use grub-boot-repair, although I'm not sure if the problem is in the partitions since I was resizing my hard-drive space with KDE Partition Manager when I wasn't patient and didn't wait for the process and did this to my build. Guess I need another lesson of patience. 

Here is the pastebin. Let me know if you are able to help.
[https://paste.ubuntu.com/p/498kmxSW8C/](https://paste.ubuntu.com/p/498kmxSW8C/)

Thanks.

---

### Post by Rubi1200 on 2023-11-25
Not sure what you were trying to do and I really hope you have good backups of whatever was on your drives/partitions.

There is no bootloader installed and no operating system according to the script results.

If you can tell us what you originally wanted to do, perhaps we can help.

---

### Post by yancek on 2023-11-26
In the boot repair output, lines 8-16 show the efi partiiton with grub efi boot files.  As pointed out in post 2 above, line 46 shows no OS detected.  On line 68, you show an entry for Ubuntu in the BIOS. Line 124 shows sda2 as a Linux filesystem.  Line 150 also shows sda2 as a linux filesystem under blkid output with UUID:  d0fa56ae-7d53-074d-a341-b5b837ff53f8.  If you look at  line 168, it shows the UUID for sda2, / partition as:   26a7bef3-5ff8-42a4-a465-5c69bf2fa0ad root hd0,gpt2.

Line 168 is from the grub.cfg file on the EFI partition point to the Ubuntu filesystem on sda2 (hd0,gpt2) and it has a different UUID so that won't work.  If this were the only problem, you could put the UUID from line 150 in boot repair into the grub.cfg file on the EFI partition but, with all the other problems, I doubt this will do anything so you probably formatted the partition 'accidentally'.  Formatting will crate a new UUID.  Do you have good backups?

---

