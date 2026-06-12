---
title: "More than 4 Primary partitions cant be done?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by asn_knight on 2010-01-28
Well, I am having a 250 GB hard disk in my Acer Laptop.
C: - a  65 Gb partition with Win7.
D: - a 150 GB partition with general data. 
and 2 partitions by default - a 13 GB and a 3.5 GB one( I guess backup and recovery by Acer or sumthn)
I shrank the D: partition to 135 GB and had made the 15 GB unallocated space to install Ubuntu.
Everytime I checked I got the free space shows as 'unusable' in the Ubuntu partitioner.
I tried shrinking again with EPM, Win Disk Management and also Ubuntu partitioner. Each time the free space which showed up said Unusable. 
A friend of mine advised me to defragment and use 'GParted' through the live cd. I did so
and when click on the unallocated space to format it said 

"IT IS NOT POSSIBLE TO CREATE MORE THAN 4 PRIMARY PARTITIONS.
 If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

Well I didnt know all of my partitions were primary! And I dont even want D: to be primary. It just is there to hold some data. 
So How do I comtinue?

Thanks.

---

### Post by asn_knight on 2010-01-28
Can I just make my D: drive secondary without formatting.
Or is there any way with which i can still install Ubuntu into my HD.
Thanks

--asn_knight--

---

### Post by chewearn on 2010-01-28
Yes, due to legacy reason, MSDOS partition scheme allows for only 4 primary partitions.

I suggest you temporarily transfer the data from D: to another location.  Then, delete D: and create a new extended partition in it's place.

---

### Post by Leppie on 2010-01-28
> **asn_knight said:**
> Can I just make my D: drive secondary without formatting.
Or is there any way with which i can still install Ubuntu into my HD.
Thanks

--asn_knight--
primary or logical partition doesn't have much to do with windows drive letters (though primary partitions usually are listed first, hence assigned lower drive letters which in any case can be changed).
the only way to install ubuntu is to create an extended partition which can hold many logical partitions. however, the extended partition is a primary parition itself, so you would still have to delete 1 of your primary partitions.

---

### Post by darkod on 2010-01-28
One of your options is using win7 Backup & Recovery tool and make a backup of your win7 system. I haven't used it, but the way I understand it you can have two approaches:
1. Create the full backup image on DVDs, in this case it can take a number of DVDs depending on your system partition used space.
2. Create a startup bootable cd/dvd (not sure which is it) with the same Backup & Restore tool, and create the actual image as file on external hdd. During restore you would only boot with the startup disc created and then use the image file from the ext hdd to restore the system partition.

This would give you the following benefits: you can restore win7 as it is now, with your software included, even if you don't have win7 install dvd (and you probably don't have it if your computer came preinstalled, only some recovery partition). The other benefit is that you can delete the recovery partition, and that way you could install ubuntu without any further partition management.

You see, I consider those recovery partitions useless anyway, since in most cases it will not only reinstall win7 on your C:, but it will DELETE your whole disk, create the partitions sizes the same as from factory, and put back image of win7 as it was, without all your software. That would also delete all your data from ntfs partitions, not just ubuntu.
Why would you ever need a restore like that?

As long as your win7 is working fine right now, no viruses, no instability, make the backup image and you can restore it with all your software already on it. Much better isn't it?

If you have a manual for the computer you can check whether the recovery partition would delete the whole disk, there will be a warning like that if using the procedure. If that is the case, why keep it?
Just MHO.

---

### Post by darkod on 2010-01-28
This is what I was talking about, look at the attachment. On the left side you see the choices:
Create system image
Create repair disc

You can see the create repair disc message open, it says you can boot with it and make repairs, or restore image backup. With Create system image you could make image file on ext hdd instead of using up lots of DVDs, and with the Create Repair Disc you just create startup disc and job done.
Not sure if the startup disc fits on CD, it should and it doesn't say whether you need CD or DVD. Try with CD first, no need to waste DVD. :)

Once you have this, you don't need any recovery partition and I guess you could delete both the 16GB and 3.5GB you mentioned. Look around in them, if you can, and try to figure out what they are exactly. Or if your manual says it.

---

### Post by efflandt on 2010-01-28
Be careful.  From what I understand in Win7, from the menus on the left, "Create System Image" only backs up the operating system (no data).  Use DVDs for that.

Recovery Disk is not specific about what kind of disk, but I thought it needed a DVD (since it referred to the DVD drive).  But when I did need it, the DVD would only boot to the Win7 background and then halt with a generic numerical error.  So that is probably supposed to be a CD (which worked when I made one later).  Fortunately it came with a system disk that was able to restore bootmgr.

If you want to back up your Win7 data, you have to set up a Backup.  Best for that would be an external NTFS formatted USB hard drive (it will not backup to FAT32).  Other choices are DVDs or simply copy files to a different drive.

---

### Post by asn_knight on 2010-01-30
After hearing from you all... 
I was left deciding between the option of installing Ubuntu within Windows
Or Formatting the Recover Partition.
Well...was it worth the risk?
Then I decided.
Atleast I'll end up using Ubuntu but never in the rarest sense go to a factory restore
in future. I made the backup discs like @Darkod said and also made a repair disc.
Yeah, his suggestion made perfect sense! :D
I deleted the 13.5 GB recovery partititon and suddenly the long awaited option
'Install in the longest free space' appeared. 
And now, Ubuntu is up and running. Thumbs up!
@Darkod : Thank You. and yeah Repair Disc came just to around 142 mb though i chose a DVD. But doesnt matter. CD and DVD almost cost the same here. :D

Again, I have some problem-the same i encountered last time when i had installed Ubuntu within Windows when 9.10 had jus released. y graphic card ATI Mobility Radeon HD 3650 wasnt detected, the battery backup decreased drastically compared to windows and also crap is that the 'Extra' visual effects couldnt be setup as it said 'Desktop Effects couldnot be enabled'. Well, what more Ubuntu has in store for me!!!

---

### Post by garvinrick4 on 2010-01-30
With Windows 7 do not forget to make your system OS disks. Takes 3 DVD's and you get one
shot at it. That will be your disks you get no more. Your recovery disk in 7 is made from same
App and it takes 1 DVD. That you can make as many as you want. I am in Ubuntu most all the
time so next time I go over to update Windows 7 I will post where the app is but it resides where all the other apps folders are.

---

### Post by asn_knight on 2010-01-31
@garvinrick4 : I already made a full image of my C: in my ext HD comes to around 32 GB.
 Do I still need to make the discs of the OS?
And Thank you all. Ubuntu works though it has some probs. Well, Why is Ubuntuforums there then? :D
I need more help. Pls look into this once. 
[http://ubuntuforums.org/showthread.php?t=1394743](http://ubuntuforums.org/showthread.php?t=1394743)

@Darkod : I know u have been linked through my reply again. :) but cant help! Im a Ubuntu-newbie and all im getting are these probs at hand.

Thanks again and enjoy,
--asn_knight--

---

### Post by asn_knight on 2011-02-03
> **asn_knight said:**
> Can I just make my D: drive secondary without formatting.
Or is there any way with which i can still install Ubuntu into my HD.


After encountering the same problem many a time trying to install in some friend's PC i got a easier solution to this.

[Partition Wizard]("http://www.partitionwizard.com/") tool actually has a simple option to mark a primary partition to Logical without formatting!!! 
Saves me the hassle for all the above. The non-Windows drive can be made Logical and it may be shrinked by some 10-15GB or so as to make an ext4 partition for Ubuntu!

Thanks all.

---

### Post by codeomnitrix on 2013-01-27
Hi,

I am facing quite similar problem but the issue is I can't go for the logical or extended partition as I am having the following partitions on my machine:

```
1. EFI System Partition (500MB)  <br/>
2. OEM Partition (400MB) <br/>
3. Recovery Partition (500MB) <br/>
4. Recovery Partition (7.87GB) <br/>
5. Windows8 Partition (105GB) <br/>
6. Other 1 (255GB) <br/>
7. Other 2 (100GB)
```

Please suggest how to install ubuntu 12.04 LTS on the machine as it says  the machine should have only four primary partitions and rest all it  identifies as raw partitions

---

### Post by uRock on 2013-01-27
This thread has been dormant for almost two years. Please start a new thread.

Thread Closed

---

