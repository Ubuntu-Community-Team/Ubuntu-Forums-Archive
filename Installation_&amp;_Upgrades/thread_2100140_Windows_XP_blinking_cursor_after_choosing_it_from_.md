---
title: "Windows XP blinking cursor after choosing it from GRUB"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by ivotkl on 2012-12-31
Ok, so I'm having [this](http://ubuntuforums.org/showthread.php?t=1812764) problem. I have also seen something called [Boot Repair](http://ubuntuforums.org/showthread.php?t=1769482&highlight=xp+blinking+cursor)

Any help? I've tried Boot Repair

Result:

```
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1483560/](http://paste.ubuntu.com/1483560/)

If  you still experience boot problems, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (640GB) disk!

The boot files of [The OS now in use - Ubuntu 10.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

Happy new year!

Useful outputs:
cat /etc/grub.d/40_custom: [http://pastebin.com/jHSEXjr1](http://pastebin.com/jHSEXjr1)
grub.cfg: [http://pastebin.com/xV2XkdjX](http://pastebin.com/xV2XkdjX)
ls -all /boot: [http://pastebin.com/GDLRbsB0](http://pastebin.com/GDLRbsB0)
ls -al /boot/grub: [http://pastebin.com/UybrB2r0](http://pastebin.com/UybrB2r0)
df -h: [http://pastebin.com/B2RF2HaJ](http://pastebin.com/B2RF2HaJ)
sudo blkid -l: [http://pastebin.com/xe7W5t2Z](http://pastebin.com/xe7W5t2Z)

---

### Post by oldfred on 2012-12-31
Windows only boots from primary partitions. You now have your XP in sda5 a logical partition. Did you have another install of Windows. Windows puts all its boot files into the primary partition with the boot flag or as Windows calls it the active partition.

Your install in sda5 also says it starts at sector 63 but is now starting 208908. Windows partition boot sector PBR has to have the same info as the partition table and you should not move Windows partitions.

       Windows Boot files, you are only showing boot.ini:
WinXP
/boot.ini /ntldr /NTDETECT.COM


You may have backups of your other boot files:
       
 If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

    
And you may be able to use this to convert partition back to primary. You may have to delete swap and then recreate it in a new extended partition. You will also have to update fstab with the new UUID.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    
You also should move the Windows partition back to start at sector 63, but will have to run Windows repairs to update it.

That is a lot of repairs. You can also just back up all your data and reinstall.

---

### Post by ivotkl on 2013-01-01
Okay, so I've decided to start from scratch as installation was completed like 3 hours before posting first thread.
Thank you for the options. I might keep them in mind just in case.
 
**Problem found: There was sort of a recovery partition of around 100 MB on the first sector, which I deleted but could not merge with the free space available on following cilinders.-**
 
**Solution: Format, as it was a fresh install. =P**
**I formatted entire disk and started from scratch. Now It is working fine. Special thanks to elfy and another guy whose name I cannot recall His user begins with j and has like 12 years of Ubuntu experience.**

---

