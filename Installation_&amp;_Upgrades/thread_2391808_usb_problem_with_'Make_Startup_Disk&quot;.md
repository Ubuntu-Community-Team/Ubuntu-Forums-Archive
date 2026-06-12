---
title: "usb problem with 'Make Startup Disk&quot;"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by whimbrel on 2018-05-13
After using 'Make Startup Disk' to write Ubuntu 18.04 to my usb
stick I could no longer write anything else to it. 
gparted  gave the error: The driver descriptor says the physical block size is 2048 bytes, but 
Linux says it is 512 bytes.
I used: dd if=/dev/zero of=/dev/sdb1  bs=2048 count=32    to remove the data
but now the stick is not automatically detected. 
lsusb detects it (Bus 002 Device 023: ID 18a5:0302 Verbatim, Ltd Flash Drive) 

fdisk -l   gives:
Disk /dev/sdc: 3.8 GiB, 4008706048 bytes, 7829504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8d93facb
But it's not mounted:
mount  /dev/sdc  /media/whimbrel/             gives:
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

Thanks

---

### Post by ubfan1 on 2018-05-13
Most startup disk creators these days just burn the ISO directly to the device, overwriting any partition table which exists, leaving the USB looking like a read-onyl DVD.  To reuse the USB,  use your favorite disk tool to  
 1) Put a partition table on the USB (sdb for example) (DOS or gpt, DOS if you just want one partition).
2) Add a (primary) partition, and select a type like linux data or FAT...
Now add a filesystem to the partition you just created (call it sdb1) (i.e. format the partition).
If the disk tool does not even recognize the device with the ISO on it as something it can write on, you need to zero out the first few blocks to wipe all recognizable info (which you tried, but used a non-existent partition instead of the device, sdb).

---

### Post by monkeybrain20122 on 2018-05-13
I don't know about make startup disk since I never use it. I use [multisystem]("http://liveusb.info/dotclear/index.php?pages/install"), with it I can still write into it after making a live usb as long as there is room left.

---

### Post by yancek on 2018-05-13
> I used: dd if=/dev/zero of=/dev/sdb1  bs=2048 count=32

That command will only overwrite the first partition on the usb (sdb1) and won't have any effect on the MBR/partition table and as pointed out above, create a new partition table which is very easy with GParted.

> mount  /dev/sdc  /media/whimbrel/

That won't work either because there is nothing to mount as you have overwritten the partition with the dd command above.  Also, you mount filesystems which are generally on partitions and your command is pointing to the entire drive (sdb when a mount should be sdb1).  Not sure what you want to accomplish trying to mount as there's nothing there.  If you had another partition on the drive, that might work.

---

### Post by kerry_s on 2018-05-13
you zeroed/blanked the drive, use disks app to format it & create a file system.

---

### Post by whimbrel on 2018-05-14
Thanks for the responses.
I used gparted and created a partition table (msdos) then added a primary partition
with a filesystem (ext4). The USB stick is now detected and displayed in Nautilus
but when I copy a file from my home directory (right click Copy) then go to the 
USB and try to paste it, Paste is grayed out, so I still can't use the USB. (Thanks
for any additional help.)

---

### Post by kerry_s on 2018-05-14
you should just leave it msdos/fat, ext4 has permissions, things copied from 1 computer may not be able to use/access in another computer.

---

### Post by yancek on 2018-05-14
> when I copy a file from my home directory (right click Copy) then go to the 
USB and try to paste it, Paste is grayed out

Either change to FAT3 or change the owner:group and/or permissions on the usb drive.  Remember that as a general rule, multi-user systems like Ubuntu don't give you write access outside your /home/user directory so it is up to you to make these changes.

---

### Post by whimbrel on 2018-05-14
Thanks. msdos/fat16 worked and the USB is restored.

Can anyone shed some light on why when I burn the Ubuntu .iso to a 
USB, when it's finished I get the message: warning, system program problem detected. 
Then when I open gparted with the USB inserted I get the message: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Is it safe to install with the USB having this problem?

Thanks

---

