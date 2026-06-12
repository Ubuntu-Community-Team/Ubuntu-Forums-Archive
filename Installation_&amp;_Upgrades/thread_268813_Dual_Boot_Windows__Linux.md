---
title: "Dual Boot Windows / Linux"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by spaulson on 2006-09-30
Hello,

Ultimatly what I would like to do is Dual Boot the computer with XP and Ubuntu.  But a bit about my setup first

I currently have Ubuntu installed and would like to add XP.  

The computer has two hard drives.  Ubuntu is installed on the first hard drive and there is no un-used partitionalb space on this drive.

I want to put windows on the Second hard drive where I do have some unused partitinoable space.

When I try to install windows, it tells me it must write some startup files to the first drive, but the drive does not contain a Windows XP compatible partition.  It them goes on to say I should delete the partition that is on it (The ubuntu partition) which of course I do not want to do.

Can anyone sugest a course of action

thanx

---

### Post by Kateikyoushi on 2006-09-30
I say disconnect the first HDD with ubuntu, install windows on the second.
Connect the first drive again and boot from ubuntu add a windows boot option to your grub.

---

### Post by Herman on 2006-09-30
I agree with Kateikyoushi.
I installed Windows 98SE on my second hard disk. It also kept threatening to wipe out all my installations on my first hard disk.  I decided to unplug my first hard disk completely and de-jumper the second hard disk to make it master temporarily, until I got Windows 98 installed. 

Once I got it installed, I plugged my regular hard disk in again, and re-jumpered my second disk as slave again.

Then I configured Grub in my first hard disk to boot Windows 98 by adding an entry in menu.lst for it with map commands, so that Windows 98 still thinks it is number1. (He,he :D ).
```
title        Microsoft Windows 98SE
root       (hd1,0)
map      (hd0) (hd1)
map      (hd1) (hd0)
savedefault
makeactive
chainloader +1
```That worked for me. I hope it will help you, Windows XP should be a little easier than Windows 98, because it is more modern.

If it can't make it's own partitions first, I recommend [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to make your FAT32 partition for Windows XP. FAT32 filesystem in XP is better for dual booting with than NTFS if you can get away with it. My XP Home Edtition can have either FAT32 or NTFS, but some Windows XPs might only be able to be NTFS. It's a shame, as NTFS causes a lot of problems, but that's the way Windows is. For the time being, it still isn't recommended use Linux for writing to an NTFS fielsystem. I find that a terrible handicap, so I keep away from NTFS.
GParted can also make NTFS filesystem if you need it.

Regards, Herman :D

---

### Post by lepre on 2006-10-01
i have the same problem, but i don't have 2 hds.

i have an ext2 boot partition, which windows installer can't read. so it won't install.
i tought about changing the partition to fat32 but will the same files work there?

other suggestions?

---

### Post by vinodmenon on 2006-10-02
I don't have two hard disks on my laptop. However I did Install Windows XP first then installed Partition Magic. After this i had plenty of empty disk space not used by Windows. I then decided to resize my partition to accomadate Ubuntu. After that i inserted the Live CD and proceeded to install it on the new partition i had made after resizing Windows. The Installation was a breeze, no problems faced.

GRUB enables me to choose which OS i want to start with, default being Ubuntu and the other Windows. Now I have a dual boot system. Works perfectly the first time!

---

### Post by lepre on 2006-10-02
> **vinodmenon said:**
> I don't have two hard disks on my laptop. However I did Install Windows XP first then installed Partition Magic. After this i had plenty of empty disk space not used by Windows. I then decided to resize my partition to accomadate Ubuntu. After that i inserted the Live CD and proceeded to install it on the new partition i had made after resizing Windows. The Installation was a breeze, no problems faced.

GRUB enables me to choose which OS i want to start with, default being Ubuntu and the other Windows. Now I have a dual boot system. Works perfectly the first time!

the problem is that win xp can't install (don't want) if it can't write the mbr on the disk.

---

