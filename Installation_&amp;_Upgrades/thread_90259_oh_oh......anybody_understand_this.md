---
title: "oh oh......anybody understand this ?"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by HarryMangurian on 2005-11-14
Successfully dual booting Win XP and Ubuntu.
Everything seems ok.

**Just fired up Partition Magic and it thinks my main drive is hosed** (see below).
Any clue or experience appreciated.

[IMG]http://upload.pbase.com/image/52262171.jpg[/IMG]

---

### Post by salva on 2005-11-14
You can still boot to your linux system?
If so, what filesystem are you using on you drive?
If you can boot without problems, its probably a case of Partition Magic not recognising the changes Linux/Ubuntu did to your partition table.

---

### Post by adrianhensler on 2005-11-14
Let's see what googling error #114 finds:

"114 - Logical partition does not start one head away from EPBR

    If the EPBR is found at sector N, and there are 63 sectors per track, then Partition Magic expects the logical partition to start at sector N+63. "

Hm; that doesn't help me much....
Partition Magic 7; that doens't support WinXp if I recall? I also see some google results suggesting that you might want to verify with cfdisk that your partitions don't overlap.

I'd also suggest moving to Partition Magic 8; much better support of linux partitions.

Are you having any other issues? You can obviously boot into Windows.... (nothing gets by me)...

Adrian

---

### Post by HarryMangurian on 2005-11-15
no other issues that can be related have been found.

I guess I am in business, except I had been planning to enlarge the Linux partition by taking some space from an NTFS partition.
I will look with a different partition program when I find a cheap copy.

ps. Norton speed disk and XP Disk Management can see the Windows partitions on the drive.   That's a bit comforting.

---

### Post by VicVega on 2005-11-15
I have the same thing happening with my setup. I have Partition Magic 8 and initially setup my partitions with it, including formatting my Linux partition. I installed Breezy and everything was good. I dual boot with XP Pro. Checking PM 8 from XP everything was fine. After a week or so, I n00bied my Breezy bigtime. I attempted a fresh install and it would not accept my partition setup this time. No matter what I tried it wouldn't take. So I had the installer delete the existing Linux partition and reassign the free space for the new install. It worked. Been running fine for a couple of weeks now. However when I boot up XP and check PM 8 now it shows my XP NTFS partition as BAD. Both XP and Breezy run fine as far as I can tell. I have GParted on Brezzy and it all partitions appear as they should. 

Could it be a PM 8 quirk?

Thanks,
Vic

---

### Post by VicVega on 2005-11-16
I am not sure but after checking some more I discovered a couple of things. If I boot XP with my external drive turned off, PM 8 will not even start. I get an error: 

```
Init Failed: Error 117
Partitions drive letter cannot be identified.
```

After I fire the external drive up, PM 8 will start fine, but shows Disk 1 as BAD. My screen looks very similar to yours. What is listed as my disk 1 used to be recognized as my C drive. However, now it shows no drive letter in PM 8. When I check in "My Computer" all my drives are listed with the correct (windows) letter value.

After I did the reinstall of Breezy I mounted my NTFS partition as read only. I suspect that somewhere in that process of mounting from Breezy, the drive letter (C:) got lost as far as Partition Magic is concerned. This is just a suspicion of mine based on my observations and not on any hard evidence or computer knowledge.

HTH

Vic

---

### Post by yesplease on 2005-11-17
@vicvega:

The short answer is that you should not use Partition Magic unless there is really no other option. Mounting Breezy wont change your windows drive letters.

Lets sum up what you did. You installed Windows which is capable of keeping track of your partitions and writes a partition table to the mbr. Then you install PMagic to take over this job. Then you use the Breezy installer and change things, you delete a partition and add it again.. Breezy installs grub and takes over handling boot from your partitions and it overwrites the mbr. PMagic does not know this. I would say that PMagic needs a function to rescan this altered situation, but apparently is hasnt (it is possible because gparted can do it). 

Perhaps PMagic has improved and has a rescue function somewhere. When  somebody uses PMagic and has no problems all is fine, however, if you can avoid using PMagic you  are better off in my opinion.

---

### Post by az on 2005-11-17
Windows partitioning tools are unreliable (suck).


(Pardon my candor.)

---

### Post by Paul Casey on 2005-11-17
my partition magic 8 gives similar results.  On the drive that pm describes as Bad is the 3 boot - Ubuntu, Fedora, Win.
At first in Win I used PM to resize and create an extra partition on that disk.  All was normal.  Then installing Ubuntu I used the partition tool to create another partition in addition to where Ubuntu gets installed.  Then installing Fedora used that last partition.  Computer works fine with all boots.  But PM now sees the disk as bad.
[IMG]http://www.axelweston.com/baddisk.gif[/IMG]

---

### Post by yesplease on 2005-11-17
@Paul Casey: you can continue to work with that setup. PMagic just doesnt understand the changes that it did not make itself. 

However, I had a similar setup and when I uninstalled linux, PM still did not understand the partition and in order to use it I had to format the whole disk. That happend a few years ago, so perhaps PM has improved in the mean time. I would avoid using PM, because it is not needed and may cause problems.

---

### Post by VicVega on 2005-11-17
Thanks for the advice. I used PM 8 because I have been indoctrinated in the "Windows Way". I figured I would use PM since I paid for it and that it would make installation of Breezy easier. I was wrong.

I'm trying to mend my ways and change my way of thinking. 

Who says you can't teach an "old dog" new tricks?

Thanks 
Vic

---

### Post by Wizzard on 2005-11-17
Partition Magic 8.0 is absolutely absolete, it does not support ext3. I had the same problem in PQM8, then I installed another newer utility and no problem.

---

### Post by osioke on 2006-01-07
I have this same situation (Ubuntu + XP Pro dual boot, and PM 8.0 giving init failed error 117 message).  I have read this thread and maybe I missed the solution someone mentioned.  Or is there no resolution to this problem with PM 8.0?  If I remove PM, what's the alternative for managing my partitions from within XP pro?

Thanks for your support.

-Osioke

---

### Post by newuser111 on 2006-01-08
partition magic does claim to support ext3 and linux swap, but i wouldn't trust its formatting

best thing to do if you want to use partition magic is to resize the ntfs partition and let ubuntu create its partitions out of the free space, that shouldn't cause any problems

---

### Post by osioke on 2006-01-08
I am not trying to perform any action on my Linux partition.  I already have Ubuntu installed and can dual-boot between XP and Ubuntu successfully.

I am, however, unable to luanch Partition Magic 8.0 from within XP.  That is the problem I am experiencing.  Any help?

Thanks. -Osioke

---

### Post by dsp76 on 2006-01-13
Hi,
I have now the same problem - but it only started, after Partition Magic 8.0 (started the first time after dualboot installation) recognized some differences between CBS and LBA values and suggested to correct the values (telling me that the LBA is the right one).
Now after this fix, PM complains about an error 117 and exits. 

So far I didn't see any resulting errors in the operation - but I fear there could happen some when the disk gets full?

regards 
Dirk

---

### Post by dsp76 on 2006-01-13
Just run Testdisk and found out that the CHS seems really to be set wrong. From the web I found out that my Hitatchi Travelstar 7k60 should have values 7296 255 63 for CHS, but 7752 240 63 is actually set.
The program then shows the partitions in the wrong order, and when analyzing the drive only find the FAT32 and NTFS partitions...

Now having set the correct CHS values in the program, it lists the partitions correctly, but mentiones wrong values of the FAT32 and NTFS partitions (telling me that that partitions are not set to 255 for heads. When then analyzing the partitions, it just finds all EXECEPT the FAT32 and NTFS....

I have no clue how to set it correctly.

regards
Dirk

---

### Post by kayzu on 2007-07-24
I know this is an old thread, but I am currently experiencing the exact same problem like the others that have posted here.

After installing Windows XP and after that, Ubuntu on the same HDD (a Samsung Spinpoint T166 HD501LJ), Testdisk and Norton PartitionMagic both say that the CHS and LBA values don't match.

I have formatted the HDD several times, did low-level formats and cleaned the MBR with a tool from the vendor (Samsung) and did a complete disk check with the same tool and after calling Samsung and asking them about this issue, I have now come to the conclusion that the disk is definately not corrupted or damaged.

Thus, there seems to be something wrong with the way the Ubuntu Installer (gparted?) handles the LBA and CHS values and corrupts them.
I have no solution for this and afer days of searching still haven't found one, I even posted a thread about the same issue ([http://ubuntuforums.org/showthread.php?t=506655](http://ubuntuforums.org/showthread.php?t=506655)) but didn't get any reply.

I really hope someone can tell us what's up with those CHS and LBA values and help us with installing Ubuntu without messing up the CHS/LBA values.
thanks, kayzu.

---

### Post by SmallFish on 2008-02-24
Use gparted in ubuntu, you shall see a bogus partition with acclamation mark (sorry I do not remembered the name). Delete that partition. Essentially, that partition does not exist and causing PM to throw error "Init failed: Error 117".  

Now this should fix PM in XP.

Good luck.

smallfish

---

