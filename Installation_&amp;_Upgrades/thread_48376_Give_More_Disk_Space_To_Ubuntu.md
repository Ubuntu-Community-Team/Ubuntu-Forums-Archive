---
title: "Give More Disk Space To Ubuntu"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by DimitrisChr on 2005-07-12
This is my first post in the forums (i am a new user so bare with me).
I have a 30GB HD with the following partition configuration:

1. 20.5GB NTFS Primary Partition (Windows XP Primary OS)
2. 3.5GB Fat32 Primary Partition (Used to store files / Backup)
3. 512MB Swap Partition
4. 5GB ReiserFS Primary Partition (Ubuntu Linux)

I have tried Ubuntu and its grown to be the best distro i've tried so far.  I have always used the 5GB partition to test different linux distros and i always deleted it after a while since i always had some kind of problems with linux.
I installed Ubuntu and for the first time i have everything working great and its been almost 2 months since i dual booted in Windows.

What i want to do (if its possible) is to shrink my first NTFS partition that holds windows and give the extra space to ubuntu (so that i can install more applications, games and download more stuff in general).

I have Partition Magic 8 in windows but when i shrink the ntfs partition it only lets me redistribute the free space back to the ntfs partition and the fat32 partition that comes after it.

I also have gparted in Ubuntu but all the partitions seem locked and i can't do anything. I read somewhere that i can't do anything unless i unmount the partition first. How can i resize the reiserfs partition when i am in linux? (Can i unmount it while i am using it???) The ntfs partition shouldn't be a problem since i can unmount it and do what i want with it. The problem is the linux partition.

So anyone has any ideas how to give more disk space to linux without destroying my winxp nor my linux installation???

Thanks in advance for any help you give me!!!

---

### Post by az on 2005-07-12
You need to unmount the disk before partitioning it.  You need to run a live cd since you only have one drive.

You can use the installer cd to edit your partition table.

I think you will need to free up a space greater than the partition you already have.  Can you shrink your NTFS partition by more than 5 Gigs?

If you can, then temporarily delete your swap, move your storage partition back to the beginning of the free space and then make your swap and move your linux partition to the beginning of the free space.   Once you have done that, you can grow your linux partition to fit all of the space.

Does that make sense?

Also, check to see that the partition names are not changed.  Change the fstab and grub (menu.list) entries, if applicable.

---

### Post by DimitrisChr on 2005-07-12
Ok azz thanks for your help. I think i got it and i am going to give it a try. I can shrink my ntfs partition at least 5GB (i am only using 7GB).  The only live cd i have is Knoppix  3.4 (kind of old i think).  Can i use the ubuntu installation cd?
I didn't quite understand the part where i may have to edit grub file. Is there any chance that i will make my pc not bootable (in winxp or in linux)???
I would like to now if there is before i try anything and then its too late  ](*,)   :razz: 
Thanks again!!!

---

### Post by not_yet on 2005-07-12
perhaps this will help [http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/) :)

---

