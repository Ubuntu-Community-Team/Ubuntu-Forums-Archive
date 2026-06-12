---
title: "[SOLVED] Creating Logical Partitions Within an Extended Partition"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by NewWorld on 2008-08-22
Hey there! I got my laptop (Dell Inspiron 1525) 3 days ago, pre-installed with Hardy. It has these partitions:

[IMG]http://i189.photobucket.com/albums/z57/digital_apocalypse/Screenshot--dev-sda-GParted_edit.png[/IMG]

The first 2 partitions were put there by Dell for recovery services, etc. Combined with ext3 that makes 3 primary partitions, so I can't make anymore. What I'm trying to do is create an NTFS partition to put WinXP on. So I used GParted to resize ext3 and make space for a new logical partition - it took me 7 hours to resize it! I right-click the newly-created unallocated space and select "New" to make a partition - it tells me that I can't create any more partitions because I have reached the maximum number of primary partitions, but I want to make a logical partition! It also told me that I should make logical partitions within the extended partition.

Even though I searched all over the web for a good 2 hours, I'm  stumped! :confused: How do I create a new logical partition to put WinXP on?

BTW, I used a Recover Disk which restored the computer, and thus the HDD, to it's factory settings so ext3 is no longer resized. I'm not afraid to resize it again though!

Any help would be greatly appreciated! Thank you :-D

---

### Post by Pumalite on 2008-08-22
If you put XP in a logical partition; good luck booting it. Windows demands a primary partition; preferably sda1.

---

### Post by NewWorld on 2008-08-22
> **Pumalite said:**
> If you pur XP in a logical partition; good luck booting it. Windows demands a primary partition; preferably sda1.

I heard people used XP on a logical partition just fine :S, isn't there a way to make both XP and Ubuntu work without getting rid of those Dell Primary partitions.

---

### Post by Pumalite on 2008-08-22
I've heard of only two people being able to boot Windows from a logical partition and I'm not one of them.

---

### Post by sandysandy on 2008-08-22
u can reformat sda3 to NTFS and put Xp there. also shrink sda3.

then move sda4 to left (expand)

in the free space next to sda5 create ext3 partition for linux.

for creating new partitions u can use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

u can download hardy from net or order from shipit.


regards

---

### Post by Gannon8 on 2008-08-22
From GParted from a LiveCD after backing up do this:
1. Delete the extended and swap partitions. You will not loose anything, as swap is not meant to store files in, and the extended partition is really a container.
2. Resize your ext3 partition so that you have enough space for your windows and swap partition.
3. Make a new extended partition from the unallocated space.
4. Make a NTFS Partition and a swap partition in the extended partition.
5. Mount your ext3 partition, open /mountpoint/etc/fstab, and change the line that says something similar to:
```
# /dev/sdaX
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX none            swap    sw              0       0
```
To:
```
# /dev/sdaX
/dev/sda* none            swap    sw              0       0
```
where * is your swap partition. Or you could use a UUID but I am not sure how to do that.

Then install Windows and try and boot it. Good luck :)

---

### Post by jminker on 2008-08-22
Hello NewWorld!

It looks to me as if you already have your logical partition on sda4. It's just that you are only using it for your swap. See how it says "extended" and then shows sda5 (linux-swap) under it? What you need to do is to shrink sda3 down and then expand sda4 into the free space you created. Then you can create as many partitions in sda4 as you give it space for.

Jim

---

### Post by NewWorld on 2008-08-22
Thank you for the fast replies! :-D

@Pumalite: Thanks for the input I wonder how I'll manage to make it a primary partition.

@Sandy: I don't think you've read the whole of my post, I've already used GParted and I know where to get Ubuntu :/

**@Gannon+jminker: Your posts have been extremely helpful, both seem like adequate solutions but the new partition in the extended partition can only be logical, while I need XP to be installed on a primary partition. If there is no other way to make a primary partition for XP, I WILL delete one of the FAT Primary Partitions.**

---

### Post by sandysandy on 2008-08-22
> **NewWorld said:**
> Thank you for the fast replies! :-D

@Pumalite: Thanks for the input I wonder how I'll manage to make it a primary partition.

@Sandy: I don't think you've read the whole of my post, I've already used GParted and I know where to get Ubuntu :/

**@Gannon+jminker: Your posts have been extremely helpful, both seem like adequate solutions but the new partition in the extended partition can only be logical, while I need XP to be installed on a primary partition. [COLOR="Red"]If there is no other way to make a primary partition for XP, I WILL delete one of the FAT Primary Partitions.[/COLOR]**

>  it tells me that I can't create any more partitions because I have reached the maximum number of primary partitions, [COLOR="Red"]but I want to make a logical partition![/COLOR] It also told me that I should make logical partitions within the extended partition.

if u go thu what i have suggested u will be able to make more logical partitions within the extended partition. in those new logical partitions u can put ubuntu (ext3) and SWAP. this is with reference to ur post >  but I want to make a logical partition!

as u have rightly said in above post u cannot put windows on logical partitions, so u will have to put windows on the existing hardy partition (sda3) and reinstall hardy on the logical partition. 

deleting FAT partitions which u say are for recovery may not be a good idea.

the link i have provided is for the gparted tutorial 

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

kindly go thru it as it is a very nice tutorial.



regards

---

### Post by Pumalite on 2008-08-22
Make disks out of the Recovery Partitions, save your data and use Gparted Live CD to repartition your drive:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it.
Your first partition (at the beginning of the drive) should be formatted ntfs. There install Windows. You can put the rest (logicals) inside of an extended partition.

---

### Post by Pumalite on 2008-08-22
Don't confuse the Gparted incorporated in the Ubuntu Live CD with Gparted Live CD.
[http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)

---

### Post by NewWorld on 2008-08-24
Awesome! Everything works for me now :D

I followed your advice Pumalite, and your instructions sandy. Thank you for the excellent contributions! :)

For anyone else in a similar situation here is how I got it fixed:

_Installing WinXP_

Because the Inspiron 1525 comes with a SATA HDD you won't be able to install Windows XP without the SATA drivers, as they are not packed in the CD. Get the SATA drivers [_**here**_]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R166200&SystemID=INS_PNT_PM_1525&servicetag=&os=WLH&osl=en&deviceid=11530&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=41&fileid=224400"). And follow [_**this guide**_]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml") on how to build a streamlined Windows XP installation CD with the SATA drivers included, without having to buy an external floppy drive.

_Partitioning for XP_

Pumalite was right when he said Windows XP should be on the first partition (i.e. sda1). I tried putting the NTFS partition in sda3 AFTER the recovery partitions, but all that did was give me the error: "NTLDR is missing". So I moved the NTFS partition all the way to the front (left-hand-side) of the disk.

_Installing XP_

From the Windows installation CD, after choosing the partition you want to install XP on you should choose to Quick Format the newly created NTFS partition. It didn't work without me formatting :P

_Notes_

After both OSes are installed you may notice that from Ubuntu GParted says it cannot read the NTFS filesystem. I solved this by following [_**this**_]("http://ubuntuforums.org/showthread.php?t=785263") very useful and simple thread.

^ it may not be much, but if I had this info I would save a good few hours running around the internet :)


Thank you to all who tried to help!:KS

---

### Post by Pumalite on 2008-08-24
Glad you got it working. Use the thread tools and mark it Solved please.

---

### Post by NewWorld on 2008-08-24
^ And congrats on your 15,000th post :O Wow you sure are dedicated! =D

---

### Post by Pumalite on 2008-08-24
Got my beans in DeRemate.com

---

