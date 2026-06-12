---
title: "Upgrade Not Available with this Tool ?!?"
date: 2024-03-05
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2024-03-05
Attempting to Upgrade Xubuntu from 20.04 to 22.04 via Software Updates. After seeing some downloading, window disappeared. 
Clicked on Software Updates again ... Not all can be updated, cont? Yes. Another window popped up - "Upgrade from Focal to Jammy not supported with this tool".
In addition, as I recall, I removed SNAP (see [https://ubuntuforums.org/showthread.php?t=2465234]("https://ubuntuforums.org/showthread.php?t=2465234") ).
Will this have something to do with the Upgrade, as I am assuming the Upgrade will Install SNAP for v22.04. 

Perhaps I need to download the ISO, burn to DVD, and attempt an Upgrade from that! I hesitate because I have several OS's installed on several partitions including all my Trading software running on Windows (as much as I hate MS, my trading software only works on MS). Have backups, but only the Home Dir on Xubuntu as that partition was 136 GB. 

Any suggestions or ideas?
Thanks!

---

### Post by Bashing-om on 2024-03-05
Rick St. George - 

How about we see what results when attempting the upgrade from terminal; better error reporting ?

1st is "release-upgrades" set properly ?
what shows:
```

grep -i ^prompt /etc/update-manager/release-upgrades

```

It it comes back "Prompt=lts" then we can proceed in terminal:
```

sudo apt update
sudo apt upgrade

```

All good so far ?

Then do the release-upgrade :D
```

sudo do-release-upgrade

```

[INDENT]the terminal is your friend
[/INDENT]

---

### Post by Rick St. George on 2024-03-08
Sorry for late reply ... net access went down. Now it will not boot, so Terminal not available. HP Laptop Elitebook 6930p Intel.

So I downloaded the 22.04 ISO, burned to DVD. Now I want to Upgrade using the DVD on SDA2 (ext4 showing 22.04 as partial/corrupt install) and SDA1 is Windows.

I am at; Something Else / Installation Type: I can select a partition SDA2 (highlighted), but under it is "Device for Boot Loader installation (SDA6 = 866 MB EFI). Is this correct?

---

### Post by Rick St. George on 2024-03-08
Update: went ahead with this Option and after ReBoot ... I arrive at a Grub Rescue prompt. 
Now I'm really stumped !!!
Any suggestions would be appreciated. Thanks!

---

### Post by Rubi1200 on 2024-03-09
Best thing would be to run the boot info script (see my signature).

Do not repair, but choose the option to create a summary report. It will generate a pastebin link which you can then post here.

Thanks.

---

### Post by Rick St. George on 2024-03-10
> **Rubi1200 said:**
> Best thing would be to run the boot info script (see my signature).
Do not repair, but choose the option to create a summary report. It will generate a pastebin link which you can then post here.


Ran from Boot Repair Disk, BIS shows nothing after pastbin.ubuntu.com

FYI 64 Bit and 1TB SSD drive.

---

### Post by Rubi1200 on 2024-03-10
If you are on a live disk can you show us this?

```
sudo fdisk -l
```

and also

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Please wrap with code tags when replying. It makes it much easier to read and analyze.

---

### Post by Rick St. George on 2024-03-10
> **Rubi1200 said:**
> If you are on a live disk can you show us this?



FYI: I get this just before grub rescue;

symbol 'grub disk native sectors' not found

Output for Rubi1200;

<code>
xubuntu@xubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 2.72 GiB, 2925768704 bytes, 5714392 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 262.5 MiB, 275251200 bytes, 537600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 74.21 MiB, 77819904 bytes, 151992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 496.98 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 40.43 MiB, 42393600 bytes, 82800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WD Blue SA510 2.
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc4fee8bc

Device     Boot      Start        End           Sectors       Size    Id Type
/dev/sda1             2048      461375487  461373440   220G  7 HPFS/NTFS/exFAT
/dev/sda2        461375488  922748534  461373047   220G  83 Linux
/dev/sda3        922753022 1953523711 1030770690 491.5G  5 Extended
/dev/sda5        922753024  981348351   58595328    27.9G 83 Linux
/dev/sda6        981350400 1049709774   68359375   32.6G ef EFI (FAT-12/16/32)
/dev/sda7       1049712640 1118072831   68360192  32.6G 83 Linux
/dev/sda8       1118074880 1938698239  820623360 391.3G 83 Linux
/dev/sda9  *    1938700288 1953523711   14823424   7.1G ef EFI (FAT-12/16/32)


xubuntu@xubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE  MOUNTPOINT
sda    931.5G disk         
&#9500;&#9472;sda1   220G part ntfs    
&#9500;&#9472;sda2   220G part ext4    
&#9500;&#9472;sda3     1K part         
&#9500;&#9472;sda5  27.9G part ext4    
&#9500;&#9472;sda6  32.6G part ext4    
&#9500;&#9472;sda7  32.6G part ext4    
&#9500;&#9472;sda8 391.3G part ext4    
&#9492;&#9472;sda9   7.1G part vfat    
sdb      984M disk         
&#9492;&#9472;sdb1   983M part vfat    /media/xubuntu/1GB Stick
sr0        3G rom  iso9660 /cdrom

</code>

Does this Help? Had to paste into Libre, transfer to main computer, copy & past in here.
Also, think I messed up by installing Bootloader into SDA9, instead of SDA, as I thought it needed a small partition to install Boot and Grub files.

---

### Post by yancek on 2024-03-10
>  Disklabel type: dos

The output above shows you are using the decades old Legacy system with boot code in the MBR.  You also have 2 EFI partitions on that single drive which is a mistake.  You can do an install on a Legacy drive in EFI but it is not the standard and not recommended.  With a Legacy install, if you want the system you are installing you should have the bootloader installation pointing to the drive so it goes in the MBR (/dev/sda) and the remaining Grub files are on the / filesystem partition, whatever that is in your case (sda2)?

Your lsblk output shows ext4 filesystem type for sda6 while the fdisk output shows it as (FAT-12/16/32.  That cannot be right.  Did you make changes between running each command?  Try running them both consecutively for the results.

---

### Post by Rick St. George on 2024-03-10
I did a Re-Install without choosing to install bootloader to an EFI partition, but to the device instead (/dev/sda). 
Then Grub was installed correctly, and Laptop Booted no problem. Although the original question goes unanswered, don't care as long as I'm up and running.

Sorry to have you guys chase down another rabbit hole!
Thanks a Million for helping everyone out!

---

