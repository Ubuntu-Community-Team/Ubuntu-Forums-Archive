---
title: "Ubuntu 23.04 boot USB doesn't recognize internal external HDD/USB"
date: 2023-05-12
forum: Installation &amp; Upgrades
---

### Post by rajkhand on 2023-05-12
I have created the 23.04 USB by belenaEtcher. It boots but doesn't mount any internal NTFS or external HDD/USB in Try Ubuntu mode while the 22.04 does that.

---

### Post by sudodus on 2023-05-12
Run the following command line in a terminal window , copy&paste the command and the output into a reply here and mark it as code

```

lsblk -e7 -o name,size,fstype,label,mountpoint,model

```

[hr][/hr]
Please post the command line and its output between code tags like this
 
[noparse]```

command line
output

```[/noparse]
 
to get output like this
 
```

command line
output

```

---

### Post by yancek on 2023-05-12
Which windows version are you using?  That would be expected behavior if you are using a recent windows version where hibernation is set as default.  Linux will not mount and therefore you will not see/access ntfs hibernated partitions.  So, is it only ntfs/windows partitions that are not seen?

---

### Post by rajkhand on 2023-05-13
```

ubuntu@ubuntu:~$ lsblk -e7 -o name,size,fstype,label,mountpoint,model
NAME          SIZE FSTYPE  LABEL              MOUNTPOINT MODEL
sda         298.1G                                       Hitachi HTS545032B9SA02
&#9500;&#9472;sda1        200M vfat    EFI                           
&#9492;&#9472;sda2      297.9G apfs                                  
sdb         465.8G                                       CT500MX500SSD1
&#9492;&#9472;sdb2      465.4G hfsplus HackSSD                       
sdc          14.9G iso9660 Ubuntu 23.04 amd64            Cruzer Blade
&#9500;&#9472;sdc1        4.6G iso9660 Ubuntu 23.04 amd64 /cdrom     
&#9500;&#9472;sdc2        4.9M vfat    ESP                           
&#9500;&#9472;sdc3        300K                                       
&#9492;&#9472;sdc4       10.3G ext4    writable           /var/crash 
sdd             0B                                       STORAGE DEVICE
nvme0n1     232.9G                                       Samsung SSD 970 EVO 250
&#9500;&#9472;nvme0n1p1   200M vfat    EFI                           
&#9492;&#9472;nvme0n1p2 232.7G apfs                                  
nvme1n1     465.8G                                       Seagate BarraCuda Q5 ZP
&#9500;&#9472;nvme1n1p1   512M vfat                                  
&#9500;&#9472;nvme1n1p2    64G ext4                                  
&#9492;&#9472;nvme1n1p3 401.3G ntfs    Data

```
No Windows MacOS Ventura on separate Drive and existing Ubuntu 22.04 on another disk which I want to upgrade

I tried manually mounting the drive Data (nvme1n1p3 401.3G ntfs    Data)  which succeeded but when I plugged in my external 2TB HDD it gave system error
 somehow not able to paste screenshot. I am doing this on 23,04 live usb

---

### Post by rajkhand on 2023-05-13
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292235&stc=1[/IMG]

---

### Post by ActionParsnip on 2023-05-13
Have you ran a full chkdsk on the NTFS partition from Windows? This will make sure the data is complete and consistent. You should then shutdown the system (not suspend or hibernate). Windows can still keep its clutches in file systems.
Hth
Also, do you use the safe remove feature in the operating system before you physically unplug the storage? This is important too

---

### Post by yancek on 2023-05-13
>  I tried manually mounting the drive Data (nvme1n1p3 401.3G ntfs    Data)   which succeeded but when I plugged in my external 2TB HDD it gave  system error

Is the 2TB drive the one shown as sdd in your lsblk output above?  It shows Size as 0B.  Is this a new drive?  Is there  a filesystem on the drive with 1 or more partitions?  Is there data on this drive?  Is this a drive with a windows install?  I see you indicate "No windows Mac OS Ventura on a separate drive" but I'm not sure what that means?  If you do not have a windows install, why do you have a windows filesystem partition?

---

### Post by rajkhand on 2023-05-13
The 2TB Toshiba drive is working perfectly in my ubuntu22.04 and MacOS. It is a NTFS formatted drive. As mentioned earlier when I plug in the drive the system error window pops up and the drive is not mounted or recognized in Ubuntu 23.04 Install USB. The NTFS patitions and external drives are because in Work and in my family others are using Windows. Also it is easier to have a common data drive between Ubuntu and MacOS. The Following output is from my Ubuntu 22.04
```

lsblk -e7 -o name,size,fstype,label,mountpoint,model
NAME          SIZE FSTYPE  LABEL                    MOUNTPOINT     MODEL
sda         298.1G                                                 Hitachi HTS54
&#9500;&#9472;sda1        200M vfat    EFI                                     
&#9492;&#9472;sda2      297.9G apfs                                            
sdb         465.8G                                                 CT500MX500SSD
&#9492;&#9472;sdb2      465.4G hfsplus HackSSD                  /mnt/HackSSD   
sdc           7.5G iso9660 Ubuntu 22.04.1 LTS amd64                Transcend 8GB
&#9500;&#9472;sdc1        3.6G iso9660 Ubuntu 22.04.1 LTS amd64 /media/raj/Ubu 
&#9500;&#9472;sdc2        4.1M vfat    ESP                                     
&#9500;&#9472;sdc3        300K                                                 
&#9492;&#9472;sdc4        3.9G ext4    writable                 /media/raj/wri 
sdd             0B                                                 STORAGE DEVIC
sde           1.8T                                                 External USB 
&#9492;&#9472;sde1        1.8T ntfs    DevToshiba               /media/raj/Dev 
nvme1n1     232.9G                                                 Samsung SSD 9
&#9500;&#9472;nvme1n1p1   200M vfat    EFI                                     
&#9492;&#9472;nvme1n1p2 232.7G apfs                                            
nvme0n1     465.8G                                                 Seagate Barra
&#9500;&#9472;nvme0n1p1   512M vfat                             /boot/efi      
&#9500;&#9472;nvme0n1p2    64G ext4                             /              
&#9492;&#9472;nvme0n1p3 401.3G ntfs    Data                     /mnt/Data    

```

---

### Post by tea for one on 2023-05-13
> **rajkhand said:**
> I have created the 23.04 USB by belenaEtcher. It boots but doesn't mount any internal NTFS or external HDD/USB in Try Ubuntu mode while the 22.04 does that.
Yes, I confirm that Files (nautilus) does not automagically mount internal nor external drives in a live session of Ubuntu 23.04.
I had to open Disks (gnome-disk-utility) to mount the drives and then they were visible in Files.

I don't know if this is deliberate behaviour.

Edit: Usb sticks mount automatically as usual when Ubuntu 23.04 is installed to a disk.
Internal disks are visible (but not mounted) in "Other Locations"

---

### Post by rajkhand on 2023-05-14
The 2TB Toshiba drive is working perfectly in my ubuntu22.04 and MacOS. It is a NTFS formatted drive. As mentioned earlier when I plug in the drive the system error window pops up and the drive is not mounted or recognized in Ubuntu 23.04 Install USB. The Following output is from my Ubuntu 22.04

Why the system error when I plug the 2TB NTFS HDD?
```

lsblk -e7 -o name,size,fstype,label,mountpoint,model
NAME          SIZE FSTYPE  LABEL                    MOUNTPOINT     MODEL
sda         298.1G                                                 Hitachi HTS54
&#9500;&#9472;sda1        200M vfat    EFI                                     
&#9492;&#9472;sda2      297.9G apfs                                            
sdb         465.8G                                                 CT500MX500SSD
&#9492;&#9472;sdb2      465.4G hfsplus HackSSD                  /mnt/HackSSD   
sdc           7.5G iso9660 Ubuntu 22.04.1 LTS amd64                Transcend 8GB
&#9500;&#9472;sdc1        3.6G iso9660 Ubuntu 22.04.1 LTS amd64 /media/raj/Ubu 
&#9500;&#9472;sdc2        4.1M vfat    ESP                                     
&#9500;&#9472;sdc3        300K                                                 
&#9492;&#9472;sdc4        3.9G ext4    writable                 /media/raj/wri 
sdd             0B                                                 STORAGE DEVIC
sde           1.8T                                                 External USB 
&#9492;&#9472;sde1        1.8T ntfs    DevToshiba               /media/raj/Dev 
nvme1n1     232.9G                                                 Samsung SSD 9
&#9500;&#9472;nvme1n1p1   200M vfat    EFI                                     
&#9492;&#9472;nvme1n1p2 232.7G apfs                                            
nvme0n1     465.8G                                                 Seagate Barra
&#9500;&#9472;nvme0n1p1   512M vfat                             /boot/efi      
&#9500;&#9472;nvme0n1p2    64G ext4                             /              
&#9492;&#9472;nvme0n1p3 401.3G ntfs    Data                     /mnt/Data    

```

---

### Post by ajgreeny on 2023-05-14
So the 2T external disk is seen (sde) but just not mounted by the looks of it.

What method did you use to remove it from the computer, any computer, not just this 23.04 Ubuntu live system?
You have already been asked if you used the "Safely remove hardware" but I have seen no reply to that question.

---

### Post by yancek on 2023-05-14
>  The NTFS patitions and external drives are because in Work and in my family others are using Windows.

How does that work?  Do other family members use this drive to store data while using their windows machines with it attached?  Is it done on a home network?  This is just a guess but if others with a windows OS are attaching and using the drive to copy or back up data, it could still be the hibernation problem.

---

### Post by sudodus on 2023-05-14
```

NAME          SIZE FSTYPE  LABEL                    MOUNTPOINT     MODEL
...
sde           1.8T                                                 External USB 
&#9492;&#9472;sde1        1.8T ntfs    DevToshiba               **/media/raj/Dev **

```

The partition on this drive **is** mounted. If you make the terminal window wider, you will be able to see the whole mountpoint (the output is truncated now).

---

