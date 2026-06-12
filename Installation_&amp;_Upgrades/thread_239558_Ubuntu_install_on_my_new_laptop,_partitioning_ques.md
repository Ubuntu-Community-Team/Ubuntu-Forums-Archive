---
title: "Ubuntu install on my new laptop, partitioning questions"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by DavyO on 2006-08-19
Hi folks,

I have recently got myself a new laptop, a HP Pavilion dv8000 series and now i would like to make it dualboot Windows xp home and Ubuntu. I have 2 80GB hardrives in my laptop with the following setup:

HD 1 : OS (C: ) (Windows XP) 67.65 GB NTFS and HP_RECOVERY (E: ) 5,87 GB FAT 32 and some 1GB NTFS partition at the end.

HD 2 : DATA (D: ) 74,53 GB NTFS

I cant remove the HP_RECOVERY partition i reckon. 

Could someone advice me on whats the best way to partitioning my drives?

I could do :

1 : Rezise windows partition and make partitions for my new Ubuntu install on the 1st HD. Format my HD 2 to FAT32 so both windows and linux can read/write it and use this for my data

2 : Resize windows partition and create a new partition for my data and make it FAT 32 so both windows and linux can read/write it and use this for my data. Installing Ubuntu on HD 2

3 : Leave the first drive untouched. Use the 2nd drive for the Ubuntu install and a data partition using FAT 32

..... Many other options, suggestions?

Any help is appreciated :D ?

---

### Post by DavyO on 2006-08-19
Nobody had any advice on whats best to do?

---

### Post by Big_J on 2006-08-19
I would make three partitions on the second hard drive for ubuntu, one large root, one larger home and one as needed swap partition. 
Leave the windows partition alone, and make that extra gig on the first drive a fat32 for shared files. If you have access to the E: drive through windows, you can use that to share files as well...

Once you start using ubuntu and start to get comfortable with it, believe me you will dump windows!

---

### Post by DavyO on 2006-08-19
> **Big_J said:**
> I would make three partitions on the second hard drive for ubuntu, one large root, one larger home and one as needed swap partition. 
Leave the windows partition alone, and make that extra gig on the first drive a fat32 for shared files. If you have access to the E: drive through windows, you can use that to share files as well...

Once you start using ubuntu and start to get comfortable with it, believe me you will dump windows!

Thanks for your suggestions Big_J :D

Actualy i really like Ubuntu already :D , i had it installed on my old laptop which has died :(  Now i miss my Ubuntu system, but since i ve plenty of HD space i reckon i keep windows for now. 

I just found out that 1GB partition is for HP Quickplay Direct (so i can play DVD`s without booting into windows). And the E: partition is the restore partition and its almost full so i cant use that for sharing files.

Whats a /home partition good for??? I was think about creating a 1024mb swap partition and the rest the root or / partition?

Is it a good idea to create a extra FAT32 partition on the 2nd HD for data exchange between windows/linux or are there better ways?

---

