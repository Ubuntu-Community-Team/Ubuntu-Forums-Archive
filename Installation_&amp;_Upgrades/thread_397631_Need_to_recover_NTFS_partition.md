---
title: "Need to recover NTFS partition"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by MxGB on 2007-03-30
Hello,

I have been running Ubuntu Edgy and WinXP in a dual-boot setup on my laptop for some time, but I've recently been having trouble with my swap partition, which has led to me royally screwing up my Windows partition.

Recently my Ubuntu has been 'losing' its swap partition during the course of going into hibernation. Just before it would normally beep and switch off the machine after hibernating it will return to the desktop and upon inspection I would find it had switched off the swap partition and damaged it somehow - gparted would show it as type 'Unknown'. I can easily run mkswap and swapon to restore the affected part'n, but it is lost again when I try to hibernate my machine. None of this happens on a reboot. This is my first unsolved mystery, and although not my pressing issue I would appreciate any hints.

The aforementioned problem has led me to a bigger problem of my own making. I recently attempted to restore my swap partition as described, but I told mkswap to use my NTFS partition belonging to Windows, in the form of 'sudo mkswap /dev/hda4'
. Immediately I realise my mistake, but then commit the henous act of rebooting and thus it seems committing the above instruction in stone. I havent touched the previously-NTFS partition since in the fear of disturbing the dust, but I need to at least try to reverse what I've done.

I would really appreciate any assistance anyone could offer. Many thanks in advance.

---

### Post by MxGB on 2007-04-01
Just an update. I have managed to sort-of recover the partition using testdisk (as obtained from universe). Strangely it is now mountable and the correct files are visible (and thankfully retrievable) despite Gparted still showing it as a linux-swap partition. I am also unable to boot from it either. As a last resort I have backed up the files on the partition and am prepared to destroy it and re-create it, although this will necessitate re-installation of Windows.

---

### Post by pradeepadapa on 2007-04-01
post ur 

sudo fdisk -l 

output,so that we can see hw much swap u hav nd try t get the solution

---

### Post by MxGB on 2007-04-02
As requested, fdisk says:```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3010    24177793+  83  Linux
/dev/hda2            3011        3142     1060290   82  Linux swap / Solaris
/dev/hda3            3143        5760    21029085   83  Linux
/dev/hda4            5761        7296    12337920    7  HPFS/NTFS
```
However, parted now sees hda4 as a fat32 partition.```
Disk /dev/hda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  24.8GB  24.8GB  primary  ext3              
 2      24.8GB  25.8GB  1086MB  primary                    
 3      25.8GB  47.4GB  21.5GB  primary  ext3              
 4      47.4GB  60.0GB  12.6GB  primary  fat32
```
I have a new hard drive on the way anyway and all I want to do is recover what's on the 4th partition before I reinstall both OSes.

---

### Post by pradeepadapa on 2007-04-02
ur swap is on the 2nd partition, as it appears from ur linux root(/) partition i.e.,hda1 or hda3 is not mounted to run the linux system, its not recognisable to the GRUB, this is precisely ur problem,

i dont know the solution t r problem bt i hav sorted r problem, the problem is nt in ur swap partition, itsi n ur root(/) partition not mounting.......

maybe others may help u

---

### Post by MxGB on 2007-04-21
Thanks for your reply. I've since managed to recover the NTFS partition, using a combination of testdisk and fdisk. After changing the MBR to say the partition was NTFS (not linux-swap) I managed to get the system mounting it using ntfs-3g even though (g)parted still saw it as a swap (maybe it generates its own partition table instead of using the MBR). After I got it mounted I just took a copy of everything to DVD and reformatted, which seemed the sensible option all things considered.

---

