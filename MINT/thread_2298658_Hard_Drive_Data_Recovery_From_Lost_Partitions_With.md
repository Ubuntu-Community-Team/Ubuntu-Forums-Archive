---
title: "Hard Drive Data Recovery From Lost Partitions With Testdisk"
date: 2015-10-12
forum: MINT
---

### Post by devon8 on 2015-10-12
So when i first installed linux i wanted to set it up as a dual boot, long story short linux messed up my partitions and i cancelled it when i realized what it was doing.

I removed the hard drive and used a spare i had to get my computer running again, ( i now have two seperate hard drives for windows and linux) 

so im still a bit of a linux noob but I'm now trying to recover files from the hard drive with the messed up partitions using Testdisk, when i run it i get the following
     
 > Warning: number of sectors per track mismatches 2 (NTFS) != 63 (HD)  NTFS                 33314  40 31 33314 138 30       6174
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 2 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 63 (HD)
  FAT12                33331 187 33 33331 233 14       2880 [EFISECTOR]
  ext4                 33536  98 19 33606 127 41    1126400
check_FAT: Unusual, only one FAT
check_FAT: Bad media descriptor (0x 0!=0xf8)
  ext4                 35443 135 35 35574  18 42    2097152
  NTFS                 35565  46 43 35756 103 36    3072000
  NTFS                 35756 103 36 35947 160 29    3072000
  ext4                 36124 210 39 36194 239 61    1126400
  NTFS                 39365  37  9 97947  82 46  941122703


Then after all of this i get a message saying that three partitions could not be recovered, and that my drive size seem to be too small (500gb/465gib), it does detect it as a 500gb which is correct but it seems to show less than that,
Any help would be greatly appreciated, please excuse anything i said that was noobish.

---

### Post by oldfred on 2015-10-12
Was or is drive MBR(msdos) or gpt(GUID)?
Or were you installing in UEFI or BIOS boot mode?
Or were you selecting LVM or LVM with full drive encryption which then only uses partitions as containers for the logical partitions?

Does this show anything?
sudo parted -l

---

### Post by devon8 on 2015-10-13
Okay, so please excuse me if i don't answer your question well, it was a normal windows HDD that had windows 7 on it originally then updated to windows 10. 
  I booted linux mint desktop version from a live usb, and clicked the install button on the desktop
  During the install when is asks installation type, i chose "something else" and then created a new partition table and made a "boot","swap", and "home" partition, i don't believe that i chose weather to set it up as MBR or gpt, 
  Then I clicked install and let it do its thing until I realized that it was screwing up windows, I then cancelled it, i don't need to make it bootable again i just want my files, if i try to boot from it i still get a windows 10 error screen which tells me that it wasn't completely formatted.

Another interesting thing i found and I don't know if it helps or not, but when i plug the hard dive in as a external drive, Linux recognizes the drive and shows the hard drive as three different devices, im assuming the devices are the three partitions i made (boot, home and swap) and it shows some files inside each of them. But when i plug it in to a windows computer, it makes the usb connection sound but nothing shows up. 

 
sudo parted -l returns this

> Model: WD My Book ES (scsi)Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            boot, diag
 2      1574MB  1823MB  250MB   primary   ext2
 3      1825MB  174GB   172GB   extended
 5      1825MB  21.8GB  20.0GB  logical   ext4
 6      21.8GB  172GB   150GB   logical   ext4
 7      172GB   174GB   1999MB  logical   linux-swap(v1)
 4      484GB   500GB   15.8GB  primary   ntfs            hidden




---

### Post by oldfred on 2015-10-13
If NTFS partitions are otherwise ok, they need chkdsk after a resize.
It is normal for Windows not to see the Linux partitions, and if NTFS partitions need chkdsk it may not show those until you do that.
Because you have an extended partition, you must have MBR(msdos). Windows 7 was usually BIOS boot with MBR, but a few were UEFI. Windows 10 overwriting Windows 7 in BIOS stays BIOS. And Windows in BIOS mode can only boot from MBR drives.

If drive is d: or e: run with that not c: as in example. Chkdsk is only in Windows.
 Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

