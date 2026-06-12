---
title: "Root partition record &quot;free&quot; after Windows installation"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Series8217 on 2008-09-09
I installed Windows XP yesterday so I could run some Windows-only apps that would not run in Wine.

Before installing Windows, I deleted my old, no longer used, Windows 2000 partition (/dev/sda1). I wrote down all of the information in gparted so I knew which partitions were safe for me to delete. 
In Windows Setup, the partition editor would not allow me to create a new partition because I already had 6 partitions on the drive... 2 main partitions and an extended partition + 3 partitions. I deleted my linux swap partition. This allowed me to create a new NTFS partition so I could install Windows.

After setting up Windows, I used Windows and restored the swap partition; I didn't format it or anything, I just added the record with windows disk management. Bad move; should've done it in Linux. Today, I booted to an Ubuntu LiveCD in order to restore grub. After opening gparted to look at my drive names I found that my root partition is now unallocated. Windows apparently overwrote the 6th partition record (which used to be my root partition) when I added the swap partition record, as now the swap partition is in the 6th position. 

How can I restore the partition record so that I can access this partition again without risking data loss? The data must still be there; I did not format the partition or anything like that. I need to edit the 6th record on /dev/sda so that it references my old root partition space (the byte range of which I do know since its bordered by the 4th and 5th partitions. How do I do this? I assume I need to use fdisk?

-Steven

---

### Post by Series8217 on 2008-09-09
I have sfdisk mostly figured out.
One thing I can't figure out how to do is only add one partition without editing the rest of the partition table.

I tried the following:
sudo sfdisk -uS -N6 -n -O /media/disk/sda-sectors.sav /dev/sda << EOF
   215030025,48821598,L,-
   EOF

The -n option prevents sfdisk from actually writing to the disk. -O <file> is the backup file.

Anyway, sfdisk says partition 6 does not exist so it can't do anything. If I remove the -N6 option, it's just trying to write the first partition as starting at 215030025... rather than picking up that I want to write sda6, which is part of the extended partition.

I would rather not have to write out the whole partition table to sfdisk.. too risky if I make a mistake. Is there any other software that allows me to change the start and end points of a record in the partition table?

---

### Post by Series8217 on 2008-09-10
BUMP!

There's got to be some way to do this. I'm not opposed to manually editing the partition table, I'm just not sure what all I need to do... 
Can I just create a new ext3 partition record and then edit the start and end numbers?

---

