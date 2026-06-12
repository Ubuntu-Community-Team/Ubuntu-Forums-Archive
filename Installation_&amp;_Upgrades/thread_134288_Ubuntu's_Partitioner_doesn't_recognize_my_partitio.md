---
title: "Ubuntu's Partitioner doesn't recognize my partitions"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by mhenrique on 2006-02-21
Hi, I was trying to install breezy but it didn't seem to recognize my partition table. If I hit F2 and try with cfdisk, it recognizes it just fine. Any ideas?

Regards

---

### Post by mhenrique on 2006-02-21
Just found out that SUSE's partitioner doesn't recognize them either. What is the software that ubuntu uses for this?

---

### Post by Herman on 2006-02-21
> Hi, I was trying to install breezy but it didn't seem to recognize my partition table.This problem seems to be getting reported more and more often lately. I wonder what is going on? I thought it was just the partitioner failing on the side of safety in one or two isolated cases.
> Just found out that SUSE's partitioner doesn't recognize them either. What is the software that ubuntu uses for this?I think it is based on this one: [http://www.gnu.org/software/parted/]("http://www.gnu.org/software/parted/")
What partitioner does Suse use?
I wonder which other types of partitioner can or cannot read your partition table? I would think that all the 'Parted based partitioners would have the same trouble. (GParted, QTParted).
Better informed minds than mine will already be working on this probably, but I have a terrible curiosity about it. I don't know enough to solve your problem, but it might be interesting to see what more we can find out. Actually, I have been poking around all day reading about partition tables. A couple of others with similar problems got me curious about it. I am learning a little bit but it seems like I have a long way to go. Maybe in 100 years I'll know enough to be able to actually help.
What other partitioners can you try?

The other person who reported a similar problem had a relatively new hard drive that had been partitioned by Western Digital's own partitioner if means anything.

---

### Post by mhenrique on 2006-02-22
Oh man, thanks for that info, now I believe I isolated the problem to parted, because using cfdisk or fdisk I can read it, record new partitions and everything.

Not sure which one SuSE uses, but Mandrake's 9.1 one, diskdrake I believe, can read my partitions too.

My HD is a Seagate btw, and strangely, I installed warty last year, without any problems.

Is there a way to install Ubuntu without debian-installer?

Regards

---

### Post by Herman on 2006-02-22
Well I don't think it's an inability of the Ubuntu installer really, or the 'parted based partitioners. They function very well for most hard-drives.
If you have checked the integrity of your downloaded .iso ([run an md5sum check]("http://ubuntuforums.org/showpost.php?p=554578&postcount=2")), and also of your CD after it is burned, and those check out okay, then it seems like something mysterious affecting a few people's hard drives. (An easy way to test the install CD is to just try it in another computer). Have you got access to another computer with Linux to integrity check your install CD?

I would certianly be sure all my data is kept well backed up, that's for sure. I think the 'parted partitioner's refusal to look at the partition table should be regarded as something of a warning, (however, it may only be something trivial causing it). Remember, the Ubuntu installer's refusal may be a safety measure, protecting you, where the other partitioners may not have that safety.

 Maybe partitioning with a different partitioner might correct your partition table, (but I doubt it), you could try that, but maybe if there is something a little but strange about it, further partitioning could aggravate any problem that may be lurking. You might lose everything that isn't backed up. If there is some miniscule fault there, it can remain there for a long time without being noticed, only to surface unexpectedly at some future time when you are partitioning, and you could have a big job getting your data back. It might not be any real 'fault' or problem at all, but a [compatibility]("http://www.ata-atapi.com/hiwtab.htm") issue between the 'Parted based partitioners and some other partitioner that may have been used at some time in the past.
Once you have written some changes to the partition table with a different partitioner you could try again maybe and see if your Ubuntu installer will recognise it then. However, it may require deleting every partitition that's there and starting over from a fully formatted hard disk, and thus a new partition table. That might be the safest thing to do. It might be over-reacting though.
There are other ways,... you could install to another disk and then copy the whole install from one disk to the other, if needs be, but, what would be the point, as then you might as well just use the other disk instead.
Good luck with it, I hope you can get Ubuntu in okay, a computer without Ubuntu is hardly any use. :-D (Herman)

---

### Post by mhenrique on 2006-02-22
Finally I found something that I can use ^^

I found this little error everytime I used parted, gparted etc.

Error: Can't have overlapping partitions.


fdisk/cfdisk seem to support such things as overlapping partitions, since they can read/edit them pretty well, so I'd like to know if I can use cfdisk during the installation instead of parted.

Regards man ;P

---

### Post by Herman on 2006-02-22
Well you'll defininetely need to fix that asap! That is not good! 


We can fix this very easily.

1) Boot with the Breezy Install CD

2) Allow it to proceed through the first stage (detecting hardware) until it stops at [!!] Partition Disks.

3) Press [Ctrl]+[Alt]+[F2]

4) Press [Enter] to activate console

5) Command:     #_parted /dev/hda

6) Command:    (parted)_ print          (or just p for short)
               this will print out your current hard disk details.

7) Take note (on a piece of paper or in another computer) of the details of you partitions, especially where the beginning number  and the endings, so we can use this information to make up a command to resize one of your partitions to fix your problem. Post back this info please, when you are ready.

8. Command:    (parted)_q                (for quit)

9)exit [enter] reboot now                 (to get back to normal mode).

When we see your figures then we can tell you the command to use, or your can do it yourself by [refering to the manual]("http://www.gnu.org/software/parted/manual/") if you like.
:-D (Herman)

---

### Post by Herman on 2006-02-22
I just have to go (work) for a while, I'll be back.
 It's simple, all you need to do is read the output from the 'p' for print comand, and see which partitions start number and end numbers overlap. Then, use the command: resize  , followed by the partition number (minor number) and the partition's start number, then type in a smaller number for the finishing number and press enter. eg:
> minor        start      end          type           filesystem   flags
1             0.031    9342.495    primary       fat32         boot,lba
2         9335.587  15869.985    logical         fat32 In this make believe example, (above), the end numbers of partition minor number 1, overlap the beginning (start) number for partition 2. To fix this, type resize, followed by 1 followed by the start number and a new end number which you make up, that is a little less than the start number for the next partition.
```
resize 1 0.031 9330.000
``` It's very easy really.
Then type 'p' (or 'print') again to make sure it worked.

After that you'll be good to go with your install. :-D

There are lots of others here to help you if you are not sure, if I don't get back in time. :-D (Herman)

---

### Post by mhenrique on 2006-02-23
```
(parted) p
Erro: Can't have overlapping partitions.
```

even if it worked, I still have some ntfs partitions so resize doesn't really work for me... I wonder if I could use cfdisk during the installation, is there this possibility?

---

### Post by Herman on 2006-02-23
Oh... well, yes, I think the next best thing to do is just use whatever partitioner you like that can deal with your partitions in their present state and try to resize each partition a little bit smaller at the end so that there is a small   gap between each one for safety. 
There are some very important items on the first sectors of each partition that you don't want to risk any chance of being overwritten accidentally and corrupted. EMBRs and inode tables and fat tables for example, without which, you will need special recovery software to recover your data. Therefore, it is wise to leave a small safety gap between partitions (no matter how smart the partition software claims to be). If you do that, then 'Parted should be happy.

You can pre-partition your disk if you want, lots of people do, but it's actually making it more complicated and more steps than the ones they are trying to avoid in the first place. Then 'Parted will still have to recognise your partitions in the end anyway, but you can do it that way if you wish. 

I think making a small gap between each already existing partition will cure your problem. :-D (Herman).

---

