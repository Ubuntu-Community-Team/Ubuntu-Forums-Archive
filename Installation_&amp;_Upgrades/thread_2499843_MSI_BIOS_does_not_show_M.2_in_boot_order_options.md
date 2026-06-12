---
title: "MSI BIOS does not show M.2 in boot order options"
date: 2024-08-13
forum: Installation &amp; Upgrades
---

### Post by ubuncha2 on 2024-08-13
I have an A320 Series MSI motherboard and I am flashed to the latest BIOS version.  I bought a M.2 NVME SSD drive for use with OS installations.  I created a Ubuntu 24 USB install drive and installed it on the M.2 drive.  However, I am unable to access that installation now, because I cannot find the M.2 drive in my MSI BIOS.  This would be the first order of business.  

Also, I read somewhere that if you formatted your drive with FAT32. the files can be accessed by Windows and Ubuntu.  However, when I installed Ubuntu, I did not see FAT32 among the list of file system options.  Why is that?  And can that be changed or avoided?  

I’m a brand new Ubuntu user.  Thanks.

---

### Post by oldfred on 2024-08-13
How did you install? UEFI or BIOS?
Should really be UEFI with gpt partitioning for any newer system which supports M.2 type drives.

Ubuntu must use Linux formats like ext4 for / (root) and any other optional partitions you may create like /home.
But you can add additional data partitions. FAT32 not recommended for large data partitions as it does not support files over 4GB nor has journal.
If you need to share with Windows better to use NTFS. But you need Windows to run chkdsk or make other repairs to NTFS as Linux cannot fix Windows issues.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

