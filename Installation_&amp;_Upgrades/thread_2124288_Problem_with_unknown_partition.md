---
title: "Problem with unknown partition"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by long2511mdd on 2013-03-10
I downloaded Gparted Partition and saw that there was an unknown Partition
When I found out more, I knew that it is the Swap partition, and I have 2 Swap Partition:

fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e304e05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3            2048   385931263   192964608    7  HPFS/NTFS/exFAT
/dev/sda4       467855358   625141759    78643201    5  Extended
/dev/sda5       617144320   625141759     3998720   82  Linux swap / Solaris
/dev/sda6       467855360   613230591    72687616   83  Linux
/dev/sda7       613232640   617136127     1951744   82  Linux swap / Solaris


I do not know if I can delete one of these to have more free space.
Could you guys give me some advices?

---

### Post by oldfred on 2013-03-10
It looks like sda5 is about twice the size of sda7.

List UUIDs
       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

    
Then in fstab see which is used. Both may be used if both existed during install. Change UUID to the one you want to keep.
       Then you'll have to edit fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

    
to confirm there are no typos, run this. If it gives no error message it has remounted everything in fstab ok.
 sudo mount -a

---

### Post by long2511mdd on 2013-03-14
There is just one swap partition during installation and it is on /dev/sd7. The other swap is still unknown and there is no information about the partition. This is what I recieved:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=c3ae50a1-103c-4892-b306-8d390b991b96 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=50ca4fbb-0663-4d0d-93f3-8fe2460dc43c none            swap    sw              0       0

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=644 0 0

I do not know about change UUID, what is that?

---

### Post by darkod on 2013-03-14
From fstab it seems you are not using sda5. It might be corrupted or something from earlier (or if you tried manipulating it from windows). It should be safe to delete it but you can't use it for much except to expand sda7 because sda5 physically is after sda7, so you can't expand sda6 to use it for example.

If you decide to delete it, do it from ubuntu not windows.

---

