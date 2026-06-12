---
title: "NTFS data on 3 TB drive is not visible in Ubuntu 14.04"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by dyno7351 on 2015-04-14
I have a dual boot computer non-UEFI BIOS running Windows Vista and Ubuntu 14.04 LTS. The computer has two hard drives; 1 tb WD (shows as /dev/sdb) that contains both Vista and Ubuntu. The data on /dev/sdb in the ntfs file system is fully accessible in Ubuntu. The other is a 3 TB Hitachi drive formatted as NTFS that contains mainly DVD movies in ISO form. When I boot into Ubuntu the 3TB drive is visible as a 3 TB drive as /dev/sda. The problem is that none of the data on the drive is visible in Ubuntu and therefore cannot be mounted.

In Vista the drive works as expected; all 3 TB are visible. Thinking that it might be partition size problem, I shrunk the drive down to a 2.2 TB and a 500 GB drive. This did nothing as Ubuntu still sees the drive as a single 3 TB drive. Ubuntu seems to be unable to view the partition information. **This is the problem**. The drive shows up in Disk Management as Disk 0, Basic, and healthy with two primary partitions.

I could format the drive in Ubuntu, but this would mean I would loose the ~1.5 Tb of files stored on the drive. I'm hoping to avoid this!

My question is thus: is there a way to make the file system on the 3 TB drive visible (non-destructively) to Ubuntu

---

### Post by oldfred on 2015-04-14
Did vendor apply proprietary formatting, or did you format drive with Windows with something other than gpt partitioning? Some vendors created odd ball MBR(msdos) partitioning to make drive compatible with XP.
Vista or later will use gpt just fine for data, but only boot from gpt with UEFI.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Post this:
sudo parted -l

---

### Post by dyno7351 on 2015-04-15
The drive was purchased new from Newegg and formatted by me under Vista Ultimate 32bit as a 3Tb drive.  The motherboard does not have a UEFI bios.

---

### Post by oldfred on 2015-04-15
Vista's old partitioning tools may not have been updated.

Would have been much better to have used something much newer like gparted or gparted on Ubuntu live installer.

Post this:
sudo parted -l

---

### Post by dyno7351 on 2015-04-15
Unfortunately I didn't. Hence the need to find a way to non-destructively get access to the drive and its data.

---

### Post by oldfred on 2015-04-15
Have you run the parted command? We need to see details, otherwise we cannot help.

Also you can run this as it is designed for gpt partitioned drives. It may not be in live installer.
sudo apt-get install gdisk

sudo gdisk -l /dev/sda

---

### Post by dyno7351 on 2015-04-16
Here's a screen cap of the output of gparted (basically the same as commandline parted).

---

### Post by oldfred on 2015-04-16
Gdisk seems to see it ok, but parted does not.

I might use gdisk to rewrite gpt partition data, It may just update whatever error parted is seeing.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
       sudo gdisk /dev/sda
Command (? for help): 

I might use p, which should be same as you posted above to confirm it sees partitions, v for verify and then w to write partition table. If anything does not look right you can use q to quit without any changes, but if fixing errors it should be making some change.

---

### Post by dyno7351 on 2015-04-18
I moved all of the data I wanted to keep to a different drive and then created a new GPT partition formatted as ntfs from within  Gparted (gui version). Once done the full drive is visible and mountable in linux.

I then rebooted into Vista to check the status of the drive. In Disk Management is shows up as an unformatted blank disk 0. 

OK, so lets created a GPT disk and format with ntfs from Vista. A 3 Tb drive is created and is usable in Vista. 

Back to booting with Ubuntu/mint and once again the drive is not mounted and shows in gparted as unallocated.

My take away here is that the GPT formatting in Ubuntu is not the same as in Windows Vista. I don't know, maybe I'm missing some special command line options in gparted?

I guess I could format the drive as MBR in vista (or in Ubuntu) - forcing me to split into two drives and then seeing if Ubuntu can see the drives.

---

### Post by oldfred on 2015-04-18
You cannot partition a 3TB drive with MBR to have more than 2.2TB as that is as far as MBR goes.

Gparted may have formatted it in NTFS differently but you want to keep it partitioned with gpt.
Did you try partitioning with gparted or gdisk.
But then format with Vista?

There are at least two different NTFS formats, one for XP and one for Vista & later.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)        Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by dyno7351 on 2015-04-18
I am aware of the limitations of MBR and may try this method as a last resort. Just to repeat: the two OS's are Vista 32 bit and Ubuntu 14.04 64 bit.
In Ubuntu I used gparted, GPT and ntfs. As I am not trying to boot from this drive, do I need to worry about the bootsector?
In Vista I used Drive Management to add the drive as a GPT drive allocating all of the drive to one ntfs partition.
After trying in both OS's the disk appeared as a full 3TB drive within each OS, just not available to the other OS. Ubuntu is installed on my 1 Tb partition along with Vista 32bit. Ubuntu can access/mount all of the ntfs partitions used by windows.

---

### Post by oldfred on 2015-04-18
Not many Vista users left, dual booting. So have not seen anyone else with issue.
It may just be the 32 bit Vista? And perhaps just that it is 32 bit?

Others with Windows 7 or later and large drives have posted that it works.

---

