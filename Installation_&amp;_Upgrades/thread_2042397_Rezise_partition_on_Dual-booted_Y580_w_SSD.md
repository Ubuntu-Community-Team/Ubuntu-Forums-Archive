---
title: "Rezise partition on Dual-booted Y580 w/ SSD"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by popnbrown on 2012-08-14
So I got a new laptop a Ideapad Y580, and swapped the HDD with a Samsung 830 256GB SSD.

Made a GPT:
Size   Format   Name
4MB      -       bios_grub
100MB   FAT32   EFI
25GB    EXT4    Ubuntu
85GB    NTFS    Data
130GB   NTFS    Windows

I installed Windows 7 Pro 64bit, all worked fine, had a bit of driver issue, but got it sorted. I then attempted to install Ubuntu 12.0 64bit, but the live CD wouldn't work. Gave me "Error: prefix not set" followed by a selection menu (Try Ubuntu, Install Ubuntu, Check Disk), and clicking any of them resulted in some error like "Could not find / root filesystem".

So I went and installed Ubuntu 32-bit. All works fine, I just have to go into BIOS to switch into Ubuntu. GPT now looks like:
Size    Format  Used     Name
4MB      -       4MB     bios_grub
100MB   FAT32    22MB    EFI
25GB    EXT3     0       Ubuntu
85GB    NTFS     0       Data
128MB    Other   128MB   Reserved PArtition
128GB   NTFS     59GB    Data Partition (windows)



I now don't need the Data partition, so I want to remove it and give the space to the Windows parition and some to the linux. However, no parition software is letting me do that. 

My main question is:
 - Where in my set-up did I go wrong? 
I would ideally like grub to be there, and would like to not have to format the drive and start over, but will if I have to.

Any suggestions, comments, would help.

Thank you
Sravan

---

