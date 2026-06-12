---
title: "Dual boot of Xubuntu and Mint?"
date: 2018-01-09
forum: MINT
---

### Post by xipho2 on 2018-01-09
Hi, 
X. is installed as sda1-4. "Unallocated Space" 120 GB. Now I want to install Mint. I watched a few vids, but I am not sure, how to install the second OS.
Thanx a lot for your advice.

---

### Post by ajgreeny on 2018-01-09
We need to know more about your hardware to be able to help.

Does it use MBR/BIOS or UEFI?
How old is it; what make and model?
What current partitions do you have for Xubuntu, and which version is it?

Please show us the output of ```
sudo fdisk -l
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by oldfred on 2018-01-09
Moved to MINT sub-forum.
BIOS/MBR or UEFI/gpt?

If MBR, you may have used all 4 primary partitions.
But default installs often put swap into an extended partition which you would have to extend.

Post these:
sudo parted -l
       sudo blkid -c /dev/null -o list

Nijia'ed by ajgreeny :)

---

### Post by xipho2 on 2018-01-09
Lenovo T400, ~10 years
MBR/BIOS
Xubuntu 16.04.3 LTS




 **```
** Model: ATA SamsungSSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size(logical/physical): 512B/512B
Partition Table:msdos
Disk Flags: 


Number  Start   End    Size    Type     File system     Flags
 1      1049kB 1000MB  999MB   primary  ext2            boot
 2      1000MB 31,0GB  30,0GB  primary  ext4
 3      31,0GB 37,0GB  6000MB  primary  linux-swap(v1)
 4      37,0GB 117GB   80,0GB  primary  ext4




~$ sudoblkid -c/dev/null -o list
device     fs_typelabel    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs        /snap/core/3604 
/dev/loop1 squashfs        /snap/core/3748 
/dev/sda1  ext2            /boot          bd3146dc-7e3e-4f35-9697-f89135c1e76b
/dev/sda2  ext4            /              9053101e-536e-473a-8abd-e702ad248531
/dev/sda3  swap            [SWAP]         bffe9dad-a643-446f-95f7-55453931d4fc
/dev/sda4  ext4            /home          9ed459da-0cec-42ac-bcae-a0cfd6e758b5
xux@x-Acer:~$ sudofdisk -l
Disk /dev/loop0:83,8 MiB, 87896064 bytes, 171672 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 512 bytes
I/O size(minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1:83,8 MiB, 87863296 bytes, 171608 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 512 bytes
I/O size(minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 232,9GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 512 bytes
I/O size(minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier:0x77e2ec7d


Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048   1953791   1951744  953M 83 Linux
/dev/sda2       1953792  60547071  58593280   28G 83 Linux
/dev/sda3      60547072  72265727  11718656  5,6G 82 Linux swap / Solaris
/dev/sda4      72265728 228515839 156250112 74,5G 83 Linux




**
```**

---

### Post by Dennis N on 2018-01-09
You have a problem, because your disk is partitioned ms-dos, which allows only 4 primary partitions and you have used them all up. 

There is no easy answer. Consider either abandoning the whole idea of dual booting with Mint, or if you are willing to start over, partition the disk with GPT partition table, which allows by default 128 partitions. Then install Xubuntu and Mint. Since your machine is BIOS, you will also need a bios_grub partition to install in BIOS mode on a GPT disk. 

Also realize that you don't need a separate home partition, and unless you are encrypting, you don't need a separate boot partition.

---

### Post by oldfred on 2018-01-09
You could delete swap, but then when done have to manually update fstab with new UUID from a new swap. Comment out current swap in fstab so you do not have issues booting. Then you can uncomment it and change to new UUID.
Moving /home into swap space will take a long time if it has a lot of data. Do not interrupt or you lose all data. And you then must have good backups before you start, just in case.

Then you can create a new extended partition, for a new ext4 for Mint's / (root) and a new swap partition.
You cannot share /boot nor /home.
If you may want data in both installs better to have /home inside / and separate /mnt/data partition that you can mount in all installs.

But there are advantages to gpt. 
You would have to reinstall grub in current install.

Do not know if Mint has a way to not install its grub into MBR, but you can go back into Ubuntu and reinstall its grub to MBR.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface

[/URL] Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 

[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

### Post by xipho2 on 2018-01-13
Ouch, seems to be something for experts? What about deleting the OS and installing both? It is true, Gparted complained those 4 primary partitions...

---

### Post by Dennis N on 2018-01-13
There is an easier solution that should work and would not require any reinstall of Ubuntu or moving the existing home partition. 

Basic Outline - working from live media you could:

1. Delete the swap partition with gparted, leaving a small unallocated space which will not be used. This will allow you to create an extended partition in what must be a relatively large unallocated space after sda4.  
2. With gparted, create the new extended partition in the space after sda4.
3. Create 2 new logical partitions (which will be located inside the new extended partition) with gparted: ext4 for install of Linux Mint and a swap partition that both can share. (The number of logical partitions are not restricted.)
4. Install Mint to the new ext4 partition by chosing the "something else" option of the installer. After this install, computer will startup to grub menu on Mint; Ubuntu will boot from Mint's grub menu.
5. For Ubuntu to use this same swap partition, you would need to change UUID of its swap in its /etc/fstab file to the that of the new swap partition.

Looks like a reasonable plan. Think it over.

---

### Post by xipho2 on 2018-01-24
@Dennis N: I am not quite sure, if I understood completely. Therefore a screenshot:
[ATTACH=CONFIG]278310[/ATTACH]
For partitioning I would boot  a Gparted CD, because a running OS would not allow partitioning?

---

### Post by oldfred on 2018-01-24
You do not show much data in /home, is it a new install?
If so then a new install may make sense as you can then change partitions around.

If re-installing do not use /boot keep that inside / (root). 
Some very old systems only like to boot from files that are inside the first 137GB of a hard drive. So I might make 2 / (root) partitions at beginning of drive. And all other partitions as logical. Make extended the entire rest of drive, and place swap at end (or far right in gparted view), so out of way.

You also cannot share /home. I often suggest separate /home as then it is a bit easier to backup and reinstall into a new / . But if using two operating systems and you want to share data, create another ext4 partition for that data. Disadvantage of data partition is you have to manually mount with fstab and set ownership & permissions which with /home is automatically done.

---

### Post by yancek on 2018-01-24
> For partitioning I would boot  a Gparted CD

If you are going to install Mint per the suggestion by Dennis N above by deleting swap and creating an EXtended partition, you should have GParted on the Mint install DVD/flash drive, use that.

---

### Post by xipho2 on 2018-01-27
Yes, it is a new install. I did not understand your post, could you name the partitions from left to right, as it would be displayed in Gparted? What belongs to Xubuntu and what to Mint after partitioning the SSD?  I want to use both OS for learning and comparing them. If I do not get it, I would try one after the other, without installing them both at once. Is it better to install the OS with "Doing something else" or checking the first box? Seperate /home, as you mentioned, but using the installed backup software would yield the same result, after a new install? As far as to my knowledge, I would reinstall the OS, starting the external HDD with the backup, clicking the backup software, done? I ask this, because I have no experience and I do not want to run into unsolvable trouble.  

 PS: I read somewhere, with the backup all configurations, changings and preferences are included, so no need to configure the OS again. If this is true, I try one OS after the other, because the time consuming configuration would not be necessary.

---

### Post by oldfred on 2018-01-27
If you at all understand partitions, you should use Something Else.
I would never rely on any automatic process whether it is installing or saving settings. Always have good backups. Not sure if installing one version over another would save anything or not. And if different versions, settings will not be common anyway.

If you have multiple installs worthwhile to learn to read the output from the report this creates. It is long, but really is just running a sequence of standard Linux commands and putting all the output into a report.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

      [/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 
    
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by xipho2 on 2018-02-18
As dual boot of Linux seems to be something for seasoned users, I gave this idea up. Win and Linux is easy. So I try them consecutively: 
I want todelete Mint and to install Xubuntu. For this I have a backup from theprevious install of Xubuntu. Before X. I tried Mint, as mentioned,but decided to install X. as the final installation. This would bethe same version of X, I installed before. If I understood, what youwrote, the backup would not install the settings, software, etc. andI must do all that time consuming stuff again? But everything insideof /home? What is your opinion concerning the partitioning as mentioned above in the screenshot? I followed suggestions of Joe Collins vids on partitioning.

---

### Post by oldfred on 2018-02-18
Most of the user settings and configuration files for installed apps are in /home. And then I back up the list of installed apps, to make it easy to reinstall them.
I do have a few settings in /etc and include the adding of a few lines as part of my new install script.

I prefer to separate my data from my settings in /home. So I use 25GB for each install including /home. But then have a large /mnt/data partition that I link folders into each install's /home. 

If you have installed several times, dual booting should not be that difficult. But I have an SSD & HDD which makes the install very quick approx. 10 min. I install from one drive to the other.
I just did a full UEFI install to a flash drive and it took about an hour as USB & flash drives are a lot slower.

---

