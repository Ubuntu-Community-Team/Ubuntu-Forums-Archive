---
title: "PLZ Help with Triple Boot Setup: OSX YOSEMITE + WINDOWS 8.1 Pro + Ubuntu 14.04LTS"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by aarag013 on 2015-03-26
I need help making my triple boot system work... I've been at it for a couple weeks and still cant't completely crack it?!

My Current Setup
300 GB WD3000HLFS-0 Raptor -** OSX Yosemite Hackintosh** / FAT32 OSX Backup drive _(GPT)_
1.0 TB WD1000DHTZ Raptor - Data drive /** Ubuntu 14.04LTS** _(MS-DOS)_
128 GB OCZ Vertex 4 - **Windows 8.1 Pro 64bit** _(MS-DOS)_

Partitioning Schemes:
300 GB HDD
 GPT / GUID Partition Table
dev/sdb1 - FAT32 EFI 200 MB (flag = boot) 
dev/sdb2 - HFS+J OSX Yosemite 139 GB
dev/sdb3 - HFS+J Recover HD 620 MB  
dev/sdb4 - FAT32 OSX Storage 139 GB (flag = msftdata)

1.0 TB HDD
dev/sda3 200 Mb FAT32 198 MB 
unallocated 1.0 MB
dev/sda1    extended 146 GB
   dev/sda5 EXT4 Ubunut 14.04 LTS 64 GB /root
   dev/sda6 linux-swap 16.21 GB /swap
   dev/sda7 EXT4 Kali Linux 10 GB 
   dev/sda8 EXT4 home folder 60 GB /home
dev/sda2    NTFS Storage 843 GB 

128 GB SSD (MS-DOS)
dev/sdc Windows 8.1Pro 
Works fine

Where I'm at...

I have OSX Yosemite working, Windows 8.1 Pro working, and have been able to boot into Ubuntu from the Chimera bootloader from Multibeast 7, plenty of times...

The issue is that I would love to resolve is how to get the bootloader to recognize that the OS/drive for Ubuntu is a Linux drive and not FAT32... 

The only way I am able to boot into Ubuntu successfully from the Chimera Boot Loader is when it's either labeled as FAT32, or when I was able to somehow get the drive to show up as Linux Icon and Read Ubuntu, I broke it by trying to remove the GRUB2 screen. 

If someone can enlighten me with a plan of action and partitioning scheme for my 1TB drive so my desired set up will work, I'll be one happy man. 

I've been on every Tutorial/Guide/Forum searchable on the mighty google search engine, I was not able to find anyone doing exactly what I want from separate hard drives. I've found a couple of guides where Ubuntu was on the same drive as OSX, in my case it is not because I want the OS's separate and wanted to stay away from a hybrid drive MBR/GPT partitioning scheme. If gptsync is the only solution just let me know or if you need more specifics/info. 

Thanks a lot, 

Jr.

---

### Post by yancek on 2015-03-26
> 
The issue is that I would love to resolve is how to get the bootloader  to recognize that the OS/drive for Ubuntu is a Linux drive and not  FAT32... 

Why?    Which system is your bootloader (Chimera) on, the Mac?  I see you have an EFI partition on the drive with the Mac.  What is sda3 on the 1TB drive with Linux?  Is that a boot partition?  Do you have all systems installed using UEFI/GPT?  You might try downloading and running the boot repair script and selecting the option to Create a Boot Info Summary.  You can post the output here and some members familiar with UEFI/GPT might be able to help.

---

