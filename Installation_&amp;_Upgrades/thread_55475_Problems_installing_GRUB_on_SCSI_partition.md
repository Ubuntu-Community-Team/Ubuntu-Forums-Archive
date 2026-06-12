---
title: "Problems installing GRUB on SCSI partition"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by mikuskuikku on 2005-08-09
Here's the problem:

I just have 1 SCSI (SATA) disk
Following partitions
 #1 WinXPpro (NTFS)
 #2 WinXPpro test (NTFS)
 #3 PersonalFiles (NTFS)
 #4 ? (/dev/sda4, volume.size: 1024)
 #5 ext3 (/dev/sda5, volume.size: ~23Gb)
 #6 swap (/dev/sda6, , volume.size: ~100Mb)

I installed GRUB on floppy (fd0) after having trouble finding out witch partition i should install GRUB on (DON'T want to install GRUB on MBR!)

Questions:
1) Can i put GRUB into #4 (or should i put it into #5)?
2) How do i install GRUB (from floppy or a new one) to the partition?

Have tryed:
>grub
>root (hd0,3)  *Answer is: "Error 12:Selected disk does not exist"
>root (sd0,3)  *Answer is: "Error 23:Error while parsing nubmer"
>root (sd0,4)  *Answer is: "Error 23:Error while parsing nubmer"

What to do?

<<mikuskuikku>>

---

### Post by Larkki on 2005-08-09
[QUOTE=mikuskuikku]Here's the problem:

I just have 1 SCSI (SATA) disk
Following partitions
 #1 WinXPpro (NTFS)
 #2 WinXPpro test (NTFS)
 #3 PersonalFiles (NTFS)
 #4 ? (/dev/sda4, volume.size: 1024)
 #5 ext3 (/dev/sda5, volume.size: ~23Gb)
 #6 swap (/dev/sda6, , volume.size: ~100Mb)

I installed GRUB on floppy (fd0) after having trouble finding out witch partition i should install GRUB on (DON'T want to install GRUB on MBR!)

Questions:
1) Can i put GRUB into #4 (or should i put it into #5)?
2) How do i install GRUB (from floppy or a new one) to the partition?

Have tryed:
>grub
>root (hd0,3)  *Answer is: "Error 12:Selected disk does not exist"
>root (sd0,3)  *Answer is: "Error 23:Error while parsing nubmer"
>root (sd0,4)  *Answer is: "Error 23:Error while parsing nubmer"

What to do?

<<mikuskuikku>>[/QUOTE]
 I had same kind of problem, I had 2 SATA disks in a Raid and Grub just couldn't be installed on that. It also broke my MBR, so I had to fix that too.
My solution was to install the grub on another HD (PATA).
I tried to look for a solution on how GRUB handles the /sdaX drives, but on some pages there was some kind of conversion like this sda1 = (hd0,14) for GRUB which was very unclear to me, also didn't work on my system.
So I can't really help you there. If it works from floppy and you don't have another HD to spare, then you might just want to be happy. =)

---

### Post by tonym on 2005-08-09
try entering

root (

and then hit the tab key.  This should give list of drives an partitions.  May help resolve issue.

---

### Post by mikuskuikku on 2005-08-11
Nop! It didn't work.
When pressing [TAB] i just get a new line with the same command.

---

### Post by mikuskuikku on 2005-08-11
I got it working!
Here's what I did.

Phoned a friend whos REALLY good at Linux.
Explained the problem for him.

He said:
"Bios can only have 4 primary partitions.
Only a primary partition can be startable."

And in my cas I had Linux on a Extended Partition.
So I reorganized my partitions so that partition 1 and 2 held XP and partition 3 was Linux partition.
Installed Linux on partition 3 (swap partition became partition 6 or something... extended partition).
Rebooted the box.
Got information 'No existing operating system'.
Started Ubuntu LIVE and mounted sda3 and chroot:ed it.
Installed grub on /dev/sda3.
'fdisk /dev/sda3' and chose first partition to boot.
Run command: dd if=/dev/sda3 of=bootsect.lnx bs=512 count=1
Copyed file 'bootsect.lnx' to DOS floppy.
Rebooted system and hoped that MS bootloader would start (and it did).
Logged in to XP and put a new line in the bootloader configuration pointing on the bootsect.lnx that I just had put on c:/.
Finnish... not only me, but allso the problem!
<<mikuskuikku>> \\:D/

---

