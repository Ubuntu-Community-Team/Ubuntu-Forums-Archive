---
title: "How to mount an external drive on 20.04 ?"
date: 2020-10-24
forum: Installation &amp; Upgrades
---

### Post by sussexlad on 2020-10-24
Hi.
I'd like to format several SSDs but when plugging any of them into a usb port, they appear in lsusb but not lsblk so I don't know how to mount  them, if that's what's required?
What should they then ideally be formatted with, to suit a fresh Ubunto 20.04 install?
 I have installed it onto a spare laptop but the disc allocation seems bizarre, with both Extended Partition 2, sda2 occupying the same space as Filesystem Partition 5, sda5 !! Is that right because when I attempted to image the disk (using Image for Linux) it took forever, rather than the previous 5/6 minutes?
TIA

---

### Post by TheFu on 2020-10-24
Did you chose LVM or ZFS during the install?
or encryption?

Under the 40 year old DOS partitioning, a few hacks where created to allow more partitions than the limited 4 primary allowed. 

GPT removes those limitations, but certain install choices force the old method to be used. 

Anyways, please post the command AND output.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo fdisk -l
```

---

### Post by Dennis N on 2020-10-24
> the disc allocation seems bizarre
This is the default partition scheme in Ubuntu 20.04 when you install in BIOS mode and choose erase disk and install. It works, but is not the usual way it would be done by most users. Partition #2 is an extended partition, which is essentially a container for one or more logical partitions. Partition #5 is where your install will be done.

```
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4

```

Formatting the USB drives is best done with the Linux partition editor **gparted**. It should detect your drives. You don't mount them when creating the partition table and partitions.

---

### Post by oldfred on 2020-10-24
UEFI or BIOS systems for SSDs?
If only Ubuntu use gpt either way. But for UEFI you need ESP and for BIOS you need bios_grub partitions.
But you have to use MBR(msdos) if old system and you have to install Windows in old BIOS boot mode.
Microsoft has required UEFI/gpt  since 2012, so most hardware is now UEFI.

My partitioning on SSD, but some data on HDD also.

```

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]nvme0n1                                 465.8G        Samsung SSD 970 EVO Plus 500GB [/COLOR]
&#9500;&#9472;nvme0n1p1 vfat   ESP_NVME  /boot/efi    512M  11.9M  
&#9500;&#9472;nvme0n1p2 ext4   focal_0               29.3G         
&#9500;&#9472;nvme0n1p3 ext4   focal_k   /           29.3G   8.2G  
&#9500;&#9472;nvme0n1p4 ext4                         29.3G         
&#9492;&#9472;nvme0n1p5 ext4   nvme_data /mnt/data  195.3G 127.5G 

[/FONT]
```

On smaller drives gparted still defaults to MBR(msdos), you first need to change to gpt. Changing from MBR to gpt will erase all data, so if you have data, but sure to have good backups.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
or
sudo parted /dev/sda mklabel gpt

---

### Post by TheFu on 2020-10-24
If you selected LVM for 20.04, something like this will happen: 

```
$ sudo fdisk -l
Disk /dev/vda: 30 GiB, 32212254720 bytes, 62914560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: **dos**
Disk identifier: 0xa55500b1

Device     Boot   Start      End  Sectors  Size Id Type
/dev/vda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/vda2       1052670 62912511 61859842 29.5G  5 **Extended**
/dev/vda5       1052672 62912511 61859840 29.5G 8e Linux LVM
```

[LIST]
[*]vda1 = Primary partition - only 4 primary partitions are allows, including 1 Extended Primary Partition.
[*]vda2 = Primary extended partition
[*]vda5 = Logical partition - logical partitions must fully fit inside the single, "Extended Partition", but there can be over 100 Logical partitions.
[/LIST]

Inside vda5, LVM has control. Unless you prove you are using LVM, I'd rather not go any farther into that hole.

More data, if you like, but not really mandatory if you don't want deep details:
[LIST]
[*]MBR [https://en.wikipedia.org/wiki/MS-DOS_partition_table#Overview](https://en.wikipedia.org/wiki/MS-DOS_partition_table#Overview)
[*]GPT [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
[/LIST]
WinXP didn't support GPT, at least not initially.  Microsoft mandated GPT be used for all UEFI booting probably for simplicity, but Linux isn't that picky. It can boot legacy BIOS or UEFI from either MBR or GPT partitioned disks.  This is one decision where I really can't fault Microsoft, at least for my needs. I don't duel or quad-boot, so there isn't any need to support older OSes on the same boot. If I need an older OS, I'll run it inside a virtual machine.

GPT is better in many, many, ways, so supporting older methods is mainly a compatibility choice by the Linux guys. For example, over 100 Primary partitions can be created with GPT without the   Some Linux distros still create MBR partition tables today on new HDD/SSD installs.

---

### Post by sussexlad on 2020-10-24
> **TheFu said:**
> Did you chose LVM or ZFS during the install?
or encryption?

Under the 40 year old DOS partitioning, a few hacks where created to allow more partitions than the limited 4 primary allowed. 

GPT removes those limitations, but certain install choices force the old method to be used. 

Anyways, please post the command AND output.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo fdisk -l
```

This is with the external usb drive plugged in -  this is not the laptop. I shouldn't have involved two things at once !
lsusb  adds the line 

Bus 003 Device 014: ID 11b0:6298 ATECH FLASH TECHNOLOGY SNA-DC/U

```
$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 003 Device 014: ID 11b0:6298 ATECH FLASH TECHNOLOGY SNA-DC/U
Bus 003 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 004: ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
Bus 003 Device 003: ID 04a9:190e Canon, Inc. CanoScan LiDE 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE FSTYPE      MOUNTPOINT
sda                   232.9G disk             
&#9492;&#9472;sda1                232.9G part LVM2_member 
  &#9500;&#9472;ubuntu--vg-root   231.9G lvm  ext4        /
  &#9492;&#9472;ubuntu--vg-swap_1   980M lvm  swap        [SWAP]
sr0                    1024M rom    


``````
$ sudo fdisk -l
[sudo] password for andy: 
Disk /dev/loop0: 9.7 MiB, 9506816 bytes, 18568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 9.7 MiB, 9510912 bytes, 18576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 97.72 MiB, 102445056 bytes, 200088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 97.76 MiB, 102486016 bytes, 200168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 2.17 MiB, 2273280 bytes, 4440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 290.45 MiB, 304545792 bytes, 594816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 217.92 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 860 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x42df724b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 488396799 488394752 232.9G 8e Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 231.95 GiB, 249028411392 bytes, 486383616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 2.17 MiB, 2273280 bytes, 4440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 55.33 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 96.92 MiB, 101605376 bytes, 198448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 290.98 MiB, 305086464 bytes, 595872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 96.92 MiB, 101605376 bytes, 198448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 289.8 MiB, 303853568 bytes, 593464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 50.69 MiB, 53133312 bytes, 103776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 290.59 MiB, 304689152 bytes, 595096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 54.84 MiB, 57479168 bytes, 112264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 255.6 MiB, 267997184 bytes, 523432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 260.73 MiB, 273375232 bytes, 533936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by TheFu on 2020-10-24
This install uses LVM.
I use LVM almost everywhere. 
I don't know what your intention is. Could you please simplify down to 3rd grade sentences for what you need?

a) all the "loop" stuff is useless. Ignore it. That's part of the new snap packages. It is never useful.
b) LVM is great, but adds complexity. It is an install-time choice. If you don't want to learn LVM, backup your files and do a fresh install being careful not to choose LVM.
c) If you are willing to learn LVM, know that there is no GUI for this. Everything to manage the LVs inside to VGs connected to the PVs is 100% CLI/terminal.  PVs are usually tied to a partition. Those layers make to tremendous flexibility.

The first LVM commands to learn are:
```
sudo lvs
sudo vgs
```

LVs can almost always be considered the same as a partition. File systems are placed onto an LV, just like a file system is placed onto a partition.  fstab mounts use the LV device, just like they can use a partition device, except that LV devices do not change at boot. No need to use UUIDs.

To learn more about LVM, there are a number of tutorials. LVM is the same on all linux distros, so any tutorial is fine.

---

### Post by oldfred on 2020-10-24
I used # to add code tags to your terminal output. 
Also better to exclude loops as the are not really devices.
Either just do not include in the copy, paste or:
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

---

### Post by TheFu on 2020-10-24
Hey oldfred, the **lsblk -e 7** blocks loop devices, but I don't know how to get them removed from **fdisk -l**, do you?

If the OP just wants a normal USB data drive, life should be pretty easy.  
Doing an install to USB storage is something I don't do.  The closest tool for that I know is **mkusb**.

---

### Post by oldfred on 2020-10-24
I do not have any loop devices. 
In bootinfoscript, now mostly part of Boot-Repair they added this:
```
## List of all hard drives ##
All_Hard_Drives=$(ls /dev/hd[a-z] /dev/hd[a-z][a-z] /dev/sd[a-z] /dev/sd[a-z][a-z] /dev/xvd[a-z] /dev/vd[a-z] /dev/vd[a-z][a-z] /dev/nvme[0-9]n[0-9] /dev/nvme[0-9]n[0-9][0-9] /dev/nvme[0-9][0-9]n[0-9] /dev/nvme[0-9][0-9]n[0-9][0-9] /dev/mmcblk[0-9] /dev/mmcblk[0-9][0-9] 2>> ${Trash});
```

I tried adding nvme to fdisk & it did not work (missing -l on second entry)
[FONT=monospace][COLOR=#000000]sudo fdisk -l /dev/sd[a-z] -l /dev/nvme[0-9]n[0-9]p[0-9][/COLOR]

But this seemed to work. Probably need mmc & vd drives also.
[/FONT]```
[FONT=monospace][FONT=monospace][FONT=arial][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo parted -l /dev/sd[a-z] /dev/nvme[0-9]n[0-9]p[0-9] [/COLOR]
Model: ATA HGST HTS721010A9 (scsi) 
Disk /dev/sda: 1000GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system     Name                  Flags 
 1      1049kB  536MB   535MB   fat32           EFI System Partition  boot, esp 
 8      537MB   26.8GB  26.2GB  ext4            groovy 
 9      26.8GB  52.5GB  25.8GB  ext4            groovy_k 
 2      52.5GB  85.0GB  32.5GB  ext4            bionic_b 
 5      85.0GB  118GB   32.5GB  ext4            focal_a 
 6      118GB   443GB   325GB   ext4            data 
 4      786GB   945GB   158GB   ext4            backup_b 
 3      945GB   998GB   53.5GB  ext4            ISO_b 
 7      998GB   1000GB  2202MB  linux-swap(v1)                        swap 


Model: Samsung SSD 970 EVO Plus 500GB (nvme) 
Disk /dev/nvme0n1: 500GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp 
 2      538MB   32.0GB  31.5GB  ext4         focal_0 
 3      32.0GB  63.5GB  31.5GB  ext4         focal_k 
 5      63.5GB  273GB   210GB   ext4         nvme_data 
 4      469GB   500GB   31.5GB  ext4
[/FONT]
[/FONT][/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by sussexlad on 2020-10-25
... and there was me hoping there'd be a simple answer !  For anyone who'd read this post, I've made a major edit.
My desktop which I simply updated is using LVM. The laptop which I installed from an iso has the dual Partition arrangement.
How do I do an new install on the laptop and ensure it employs LVM ? I don't recall that being offered as an option.
Thanks

---

### Post by Dennis N on 2020-10-25
> How do I do an new install on the laptop and ensure it employs LVM ?

I create the LVM physical volume, volume group and logical volume befure starting the installer if these don't already exist. That way you have control of the locations and sizes of these things. 

You use the 'Something Else' choice on the 'Installation Type' screen, which opens the partitioning screen. There you select the LV to be used for root of the OS. 

Gparted can create the LVM physical volume (Format the partition as LVM2). The result is also called an 'LVM partition'. The volume group (vg) and logical volumes (lv) are created on the LVM partitions with terminal commands - vgcreate and lvcreate.

Before beginning, you need have a minimal understanding of what you are doing: a good introduction to LVM for beginners that I have used is:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

Once you do an LVM installation, you have 'bought in' to using LVM and need to learn the basic maintenance commands.

---

### Post by TheFu on 2020-10-25
> **sussexlad said:**
> ... and there was me hoping there'd be a simple answer !  For anyone who'd read this post, I've made a major edit.
My desktop which I simply updated is using LVM. The laptop which I installed from an iso has the dual Partition arrangement.
How do I do an new install on the laptop and ensure it employs LVM ? I don't recall that being offered as an option.
Thanks

There is an option to use LVM in the installer for most flavors of Ubuntu Desktop and Server.  I suppose a few installers may not have that included. Usually, when LVM is selected during the install, it is part of the --wipe everything on disk first-- installation choice.

Just to be clear, you already have an install with LVM on the internal disk, but want to do more installs onto external USB storage also using LVM?  These USB devices aren't just to be used for data, but for other OS?

LVM has a few limitations that aren't intuitively obvious.  For example, VG names need to be unique between different VGs connected to the system.  So, if you intend to have 2 Ubuntu-Mate installs on the same machine, the default VG names ... let me check that:
```
$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree
  **vgubuntu-mate**   2   3   0 wz--n- 39.49g 6.39g
```
vgubuntu-mate cannot be used for the 2nd install.  That's because the device mapper process creates device names for LVs based on the VG-LV names. For example:
```
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 17.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g          
```
So, "home", "root", and "swap_1" cannot be used in 2 separate installs on the same machine.
```
$ ll /dev/mapper/
total 0
drwxr-xr-x  2 root root     120 Oct 24 09:26 ./
drwxr-xr-x 20 root root    4140 Oct 25 01:15 ../
crw-------  1 root root 10, 236 Oct 24 09:27 control
lrwxrwxrwx  1 root root       7 Oct 25 07:54 vgubuntu--mate-home -> ../dm-2
lrwxrwxrwx  1 root root       7 Oct 25 07:54 vgubuntu--mate-root -> ../dm-0
lrwxrwxrwx  1 root root       7 Oct 25 07:54 vgubuntu--mate-swap_1 -> ../dm-1
```

Those device names are used in the fstab to mount storage. An /etc/fstab:
```
/dev/vgubuntu-mate/root /       ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/home /home   ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/swap_1 none  swap    sw      0       0

```
See the issue?

So, the different flavors usually create a different VG name to get around this problem.  I think the newer installer attempted to fix that as well by using really ugly names for the devices in the fstab.  I found them too ugly and manually changed those devices back to something human readable:
**/dev/{vg-name}/{lv-name}**.  Personal preference.

If you manually create VGs, it would be good to choose unique names across all your systems, since in the future you may need to connect a HDD/SSD to another system. VG name collision is a hassle.

---

### Post by sussexlad on 2020-10-26
Many thanks for all the helpful advice.  
I now have another problem, in that it looks as if the DVD drive on the laptop has packed up. I have a replacement on the way.
I admit that I did not see or understand the LVM option on install and will choose that option once the drive is sorted.
I'm just left then with the question, how do you make a external SSD mountable on a LVM setup ?

---

### Post by TheFu on 2020-10-26
> **sussexlad said:**
>  
I'm just left then with the question, how do you make a external SSD mountable on a LVM setup ?

External storage can use or not use LVM. It is up to you.  For data-only, not an OS, there are reasons for both of those options. Or you could decide to use ZFS or one of the 20+ other solutions. Storage on Linux has lots and lots of options, depending on the need.

But ... the simple answer is don't use LVM for just data storage unless you need snapshot support.
To do that, do it like any other disk.

[LIST=1]
[*]Create a partition table on the whole disk, use GPT. gparted, fdisk, parted can all do this.
[*]Create at least 1 partition. gparted, fdisk, parted can all do this.
[*]If you use gparted, format the partition with ext4 as the file system.
[*]Give the file system a LABEL. again, gparted makes this easy.
[*]Don't forget to "Apply" your gparted changes.
[/LIST]
That's all the prep work.
Now for the mounting. There are a number of methods:
[LIST]
[*]sudo mount command from a terminal
[*]modify the /etc/fstab
[*]use autofs to mount the storage on-demand and umount it when it isn't used.
[/LIST]
The easy answer is to setup the fstab, but then the storage has to be there at boot and cannot be removed.  I don't do that for USB or networked storage, since those connections can be flaky and disappear.
Because you gave the file system a LABEL during the prep-work above, you can easily mount the storage using that unique LABEL in the fstab. Add a line like this:
```
LABEL={whatever-label-you used}    /media/{whatever-label-you used}   ext4 nofail,noatime,errors=remount-ro     0 2
```

Use **sudoedit /etc/fstab** to safely edit the fstab. Add that line.  The label you choose cannot have any spaces in the name.
When done, run this command to force systemd to re-scan the fstab and the mount -a to mount all storage that is inside the fstab.
```
sudo systemctl daemon-reload
sudo mount -a
```
That should be it.

**gparted** rocks.  There are other tools, but they aren't nearly as capable. You may need to install gparted .... or not. It is worth having installed. I don't trust the gnome-disks app.

If you want to use LVM, do all the prep-steps up to the point of formatting a file system.  Then you'll want to follow an LVM guide.  For an SSD, I'd recommend a few things to get flexibility and to drastically increase the SSD lifetime.
Leave 20% of the total storage un-partitioned. This allows the SSD to have more storage space for wear leveling.
Inside the partition, setup 1 VG, but only allocate the LV storage as needed for 1-3 months growth.  Increasing LV sizes is trivial and easy while the file system is online.  Decreasing an LV is an off-line operation and can require backup+wipe first.  If you use LVM, then you'll likely want to also use LVM snapshots for backups. These are dynamic - create/delete - just during backups, so you'll likely want to limit the total allocated VG storage to 80-90% of the total available so 10-20% is available for those snapshot LVs.
After you create the PV, VG, and any LVs you need, then you use **mkfs** to format the LV as desired with the filesystem you want. If you don't use ext4, then all sorts of LVM+ext4 features are not available.  LVM and EXT4 are designed to be used together.

So see the different commands for vg, lv, and pv stuff, use tab completion:
pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}
Basically, each command work like this:
create, convert, reduce or extend and finally remove.
```
$ pv{tab}{tab}
pvchange   pvcreate   pvmove     pvresize   pvscan     
pvck       pvdisplay  pvremove   pvs   
$ vg{tab}{tab}
vgcfgbackup    vgconvert      vgextend       vgmknodes      vgs
vgcfgrestore   vgcreate       vgimport       vgreduce       vgscan
vgchange       vgdisplay      vgimportclone  vgremove       vgsplit
vgck           vgexport       vgmerge        vgrename       

```
and the same for LVs.

sudo pvs, vgs, lvs are the overview commands for each LVM object type. The vgdisplay, lvdisplay, and pvdisplay commands aren't really needed anymore, unless you really need to see all the details. I haven't in years, but the detail are there if you like to look.

LVs are treated just like partitions. They get file systems (mkfs on LVs is blazing fast compared to normal partitions). They get mounted. They get fsck'd.  

The manpages for each of these commands is really great, but you'll want a clear understanding of how each of the objects fit together.  LVM does add some complexity, but that usually only matters about 5 minutes every 5-10 yrs.  The rest of the time, will be spent being happy you used LVM and knowing that 5-10 seconds with an lvextend command can add storage where you need it, when you need it. No guessing 4 yrs ago which I promise you'll get wrong.  I've been doing storage for 25+ yrs and have yet to guess correctly where I needed storage.

Heck, on a fresh 20.04 install in June, I got the storage guess wrong.  My desktop install had been using 25G total storage for about a decade, but after the 20.04 install where I gave it 30G, I found it was always running out of storage.  LVM to the rescue.
```
$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 6.39g
$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- 39.49g 6.39g
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 17.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g            

$ df -hT
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G   10G  5.9G  63% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.2G  5.0G  56% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi 
```
Can you see what I did?  BTW, the system was active, booted, running, the entire time these changes were made.

---

### Post by sussexlad on 2020-10-26
Hi and thank you for that comprehensive explanation which I've made a note of.   :-)

I have Gparted installed and have used it in the past.
My issue is that when I plug the SSD into a USB port
#lsusb   adds the following line  to the list but the drive is not listed by Gparted and so I'm unable to make any changes to it.
How do I get it to appear ?   I'm sorry if I'm being thick !!

Bus 003 Device 008: ID 11b0:6298 ATECH FLASH TECHNOLOGY SNA-DC/U

---

### Post by TheFu on 2020-10-26
Search for the USB ID and linux to see if it is supported.  It appears to be an extremely old drive, from 2012 timeframe or did I misread that?

Try a different USB port.  Use USB2, not USB3 ports. If it is using a USB-switch/hub, try connecting it directly.
When you connect it, does **dmesg -w** show that physical connection?

Do you have the drive externally powered? If not, hook up external power.

There are all sorts of reasons for USB storage not to work.

Please post both the command AND the output here.  Also, use the advanced editor and the '#' around everything you copy/paste from the terminal. We call that "using code-tags."  Do not edit or realign the output. See how my output above in columns is aligned nice?  That's just code tags -copy/pasted into the editor here.

```
dmesg -w
lsusb -t
```
please.

---

### Post by sussexlad on 2020-10-27
This is the final message following plugging the additional usb drive in.

#dmesg

[11908.752514] usb 3-8: new high-speed USB device number 26 using xhci_hcd
[11908.901437] usb 3-8: New USB device found, idVendor=11b0, idProduct=6298, bcdDevice= 1.14
[11908.901443] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11908.901447] usb 3-8: Product: SNA-DC/U
[11908.901450] usb 3-8: Manufacturer: Kingston
[11908.901453] usb 3-8: SerialNumber: 303030303030303030374239
[11908.903012] usb-storage 3-8:1.0: USB Mass Storage device detected
[11908.903299] scsi host6: usb-storage 3-8:1.0
[11910.056717] usb 3-8: reset high-speed USB device number 26 using xhci_hcd
[11910.348776] usb 3-8: reset high-speed USB device number 26 using xhci_hcd
[11910.640705] usb 3-8: reset high-speed USB device number 26 using xhci_hcd
[11910.932781] usb 3-8: reset high-speed USB device number 26 using xhci_hcd

#lsusb -t

/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/15p, 480M
    |__ Port 8: Dev 29, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 9: Dev 2, If 1, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 9: Dev 2, If 2, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 9: Dev 2, If 0, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 9: Dev 2, If 3, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 10: Dev 18, If 0, Class=Vendor Specific Class, Driver=, 480M
    |__ Port 11: Dev 4, If 1, Class=Vendor Specific Class, Driver=btusb, 12M
    |__ Port 11: Dev 4, If 2, Class=Vendor Specific Class, Driver=btusb, 12M
    |__ Port 11: Dev 4, If 0, Class=Vendor Specific Class, Driver=btusb, 12M
    |__ Port 11: Dev 4, If 3, Class=Application Specific Interface, Driver=, 12M
    |__ Port 12: Dev 5, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 12: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M


This line has been added when the additional USB drive was plugged in

 |__ Port 8: Dev 29, If 0, Class=Mass Storage, Driver=usb-storage, 480M

However it is not recognised by gparted, so I'm unable to do anything with it.
I have other usb drives that I use for backup which are recognised.

Thanks

---

### Post by TheFu on 2020-10-27
Sorry, I wasn't clear.
[LIST=1]
[*]```
dmesg -w
```
[*]plug in the storage device
[*]what are the new lines added?
[/LIST]

Also, whenever posting terminal output, it is helpful to use 'code tags' - that's in the advanced editor here - #. We are just used to seeing things that line up a specific way.

A number of other suggestions were made. Please go through each of those and let us know what you did, what the result was.  We cannot read your mind. Every unanswered question leaves doubts.  If it were me, I'd have already used another system, copied all the files onto a newer SDHC or USB3 flash device and moved on. It isn't like USB2 devices are worth $3 anymore.

---

### Post by sussexlad on 2020-10-28
Ok to tidy this thread up there were two problems.... which is confusing to say the least !

1 ) The stand-alone 2.5" housing I was using was faulty, despite appearing to power up OK.
2) The PSU supplying my ALL IN 1 HDD dock was putting out 6v instead of 12v.

Gparted now sees all my SSDs and I can format them etc.

Thanks for all the advice, which prompted me to keep looking.   [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by helen314 on 2020-10-29
> **sussexlad said:**
> Ok to tidy this thread up there were two problems.... which is confusing to say the least !

1 ) The stand-alone 2.5" housing I was using was faulty, despite appearing to power up OK.
2) The PSU supplying my ALL IN 1 HDD dock was putting out 6v instead of 12v.

Gparted now sees all my SSDs and I can format them etc.

Thanks for all the advice, which prompted me to keep looking.   [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

To make you feel better - I optioned my UEFI firmware  to "disable legacy USB " .
My mouse runs off USB port. 
I could not figure out why  my mouse quit! 


I am not sure how this thread got from "eternal drive"  to all that stuff about USB.
I have xTB  USB connected hard drive - so is it USB or "external?

I'll admit I did not scan all discussion contributions, maybe somebody mentioned this. 
I would give "Disks"  a try.
It is little goofy, but does "mount" anything irregardless of technology. 










Perhaps a better terminology should be used.

---

