---
title: "Awkward Partition task"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Kirky_D on 2006-11-17
Hi there. 
Now that i have got vmware fully working on my edgy setup, i am getting rid of xp altogether.

The problem i have is that my partition table is a bit funky.

[[IMG]http://img293.imageshack.us/img293/9250/partitionmf2.th.png[/IMG]](http://img293.imageshack.us/my.php?image=partitionmf2.png)

I have tried resizing and moving ext3 partitions before and always ended up with a bad superblock (i think thats what its called) 

I have been looking into the gparted live cd, but the general consensus seems to be that its not very good at resizing and moving.

Can anybody help me?

---

### Post by wpshooter on 2006-11-17
If you have the time and aptitute my suggestion would be to wipe the hard drive and re-install Edgy on the computer from scratch.

Good luck.

---

### Post by Kirky_D on 2006-11-17
> **wpshooter said:**
> If you have the time and aptitute my suggestion would be to wipe the hard drive and re-install Edgy on the computer from scratch.

Good luck.

Thats kind of not an option. lol. I have too much data to be saved, and only a 55 GB external hard drive, and DVD's to back up on, which would take me ages, aswell as wasting a lot of DVD's

anybody else?

---

### Post by K0LO on 2006-11-17
Kirky_D:

I can't say that I've ever had problems moving ext3 partitions around, but the last time that I did it I used Acronis Disk Director, not Partition Magic. So if you're nervous (and I don't blame you for not wanting to take risks with your data), then I would do the following:

1. Get a drive imaging program. I use Acronis True Image. You could try Partimage here [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

2. Back up the partitions that you want to save to your external USB drive. It looks like you have 67 GB of data in the two ext3 partitions. TrueImage compresses  to about 0.7 of the original size as it creates an image so you will need about 47 GB of storage space. I'm not sure how much compression partimage uses; check the documentation. You'll want your USB drive to be formatted with NTFS if you're going to use TrueImage to save a huge file of this size -- FAT32 has a 4 GB maximum file size limit. For partimage you can probably use ext3.

3. Use Partition Magic in a stand-alone mode to delete all of the existing partitions and then create new, formatted partitions in the desired order and of the desired size. You could probably just create three for root, home and swap, and they all could be primary partitions.

4. Use TrueImage or partimage to restore your backed-up root and home partitions.

5. You may need to change the /etc/fstab file to reflect the new drive references if the partition references are different. You may also need to edit the /boot/grub/menu.lst file. Do both of these by booting into a LiveCD version of Linux.

Hopefully this will put everything back in working order. I did it this way six months ago when I wanted to move a bunch of partitions around on my hard drive. It worked perfectly.

---

### Post by Kirky_D on 2006-11-18
Thanks for the info, I will look into it!

Sounds like a good idea though!

---

### Post by Kirky_D on 2006-11-20
Ok, so i looked into partimage, tried it, and it didn't recognise any of my partitions. lol

It said that the filesystem was not recognised.

Are there any other suggestions?

---

