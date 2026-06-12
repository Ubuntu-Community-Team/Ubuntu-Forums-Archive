---
title: "Ubunto dont see my HDD for installing native. Acer aspire 3 a315-56"
date: 2022-03-20
forum: Installation &amp; Upgrades
---

### Post by dead208 on 2022-03-20
I already:

Update my BIOS

Change optane without RAID for AHCI

Disable secure boot

Disable fast boot

Made space in win particion manager

Try Rufus and etcher

Try almost every option on Rufus

I tried too on a SSD and nothing

I have win 10 pro but i disable the bitlocker

Disable fast boot in windows energy options





Posible problems:



My info tab in my BIOS dont identify my USB but in the boot menu for the priority options it identifies it.





I havent tried:



Change the USB: (I dentify the blocks and that never give me problems. And i dont have another one)



I would really aprecciate the help. I've tried to solve this for about 2 weeks and i really want to do this.

---

### Post by oldfred on 2022-03-20
Acer Aspire A315-53-386P remove RAID from drive
[https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa](https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa)

RAID can leave meta-data on a drive that has to be removed.

---

### Post by dead208 on 2022-03-21
Nope, even GParted don't see my disk. I also remove the dmraid with <apt-get remove dmraid>. I also just re-install windows from USB and that work perfectly.

---

### Post by oldfred on 2022-03-21
Does live installer boot ok?
If SSD have you updated firmware for SSD?

Can you run these. Post in code tags if they work.
sudo parted -l
sudo fdisk -lu
lsblk -f

---

### Post by dead208 on 2022-03-21
```
ubuntu-mate@ubuntu-mate:~/Desktop$ sudo parted -l
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sda: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  31.0GB  31.0GB  fat32        Main Data Partition  msftdata

```


```
ubuntu-mate@ubuntu-mate:~/Desktop$ sudo fdisk -lu
Disk /dev/loop0: 1.86 GiB, 1975693312 bytes, 3858776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.52 MiB, 58204160 bytes, 113680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 43.6 MiB, 45703168 bytes, 89264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 16 KiB, 16384 bytes, 32 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 15.17 MiB, 15900672 bytes, 31056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 28.92 GiB, 31029460992 bytes, 60604416 sectors
Disk model: DataTraveler 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7D253766-040B-460D-8287-F6D0D9D0C229

Device     Start      End  Sectors  Size Type
/dev/sda1   2048 60604382 60602335 28.9G Microsoft basic data
```


```
ubuntu-mate@ubuntu-mate:~/Desktop$ lsblk -f
NAME FSTYPE LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0
     squash                                                  0   100% /rofs
loop1
     squash                                                  0   100% /snap/core
loop2
     squash                                                  0   100% /snap/snap
loop3
     squash                                                  0   100% /snap/soft
loop4
     squash                                                  0   100% /snap/ubun
sda                                                                   
&#9492;&#9472;sda1
     vfat   UBUNTU-MATE
                  CA3B-8DAD                              25.7G    11% /cdrom
```

---

### Post by dead208 on 2022-03-21
My disk is updated I use the Kingston SSD manager and no update available. U think that if I buy a new SSD without Winwoes could work?

---

### Post by oldfred on 2022-03-21
Is there some setting in UEFI for protection on drive?
Some have a setting to lock drive, so not seen. But then I do not understand why Windows would see it.

I assume a 5 is similar to a 3. May have some setting you missed. 
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
Acer Aspire 7 A715-71G NVE not seen Boot parameter: nvme_core.default_ps_max_latency_us=200 
[https://ubuntuforums.org/showthread.php?t=2429323](https://ubuntuforums.org/showthread.php?t=2429323)

May still be optane related?
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)
removal (setuprst.exe and setupoptanememory.exe - both from Dell

---

### Post by tea for one on 2022-03-21
In your UEFI Set-up, can you disable (if they exist)?
TPM (Trusted Platform Technology)
PTT (Platform Trust Technology)

---

### Post by dead208 on 2022-03-22
Ok, now it sees my USB driver but not my HDD. Using the [COLOR=#000000]sudo parted -l [/COLOR][COLOR=#000000]sudo fdisk -lu [/COLOR][COLOR=#000000]lsblk -f
[/COLOR]It only shows the USB.

---

