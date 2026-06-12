---
title: "Partitioning issues"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by wldstrm on 2007-04-23
I am attempting to make a 10 gig ext3 partition for xubuntu and a 1 gig swap.  I have two partitions on my harddrive already.  I have one for XP and one for personal files.  I had no problems resizing my old partitions, but when i attempt to make the new ones i receive the following error when making the ext partition:

/dev/sd6 is mounted; will not make a filesystem here!

I dont even have an sd6 listed so i dont know what my problem is.  I have searched the forums and have not found anything to help me.  I am new to Linux in general and really like what little i have used the live cd so far.  Someone please help a newbie :(

EDIT: I have tried to make sure that I unmount everything possible before hand.

---

### Post by dannyboy79 on 2007-04-23
what are you using to do this? also, you must have a typo because there is no such device as /dev/sd6, maybe /dev/sda6. if I were you I would just delete those partitions you created adn leave it unallocated. then use the installer to create what you want. i always use the alternate cd install because it has more options for where to install grub etc etc.

---

### Post by wldstrm on 2007-04-23
oh im sorry that is a typo, i meant dev/sda6 and i am using Gparted on the Xubuntu live cd.  I have tried to leave it unallocated, and it still give me same error during the install.  I could try the Alt cd but i would like to fix this without having to DL a whole new file since they are so big.

---

### Post by wldstrm on 2007-04-23
bump
I just noticed that my drives current partitions are listed, in order: 
/dev/sda1 - Windows install nfts
/dev/sda2 - extended
/dev/sda5 - personal files nfts
i dont knew where sda 3 and 4 are

---

### Post by dannyboy79 on 2007-04-23
this is what I would do if I were. back everything up using tar or similar to another hard drive. or even use a windows tool to backup your windows stuff. then start over. after backing everything up, I would wipe the drive by writing zero's to it to make sure nothing is hanging around. otherwise, 3 & 4 must be the ones you erased to try to leave an unallocated space for the install. i have tried to use partimage to backup a brand spanking new win2000 pro install to a fat32 partition. it worked, then I restored it after preparing the new drive using gparted. it worked BUT when I started her up, I got disk failure error so I would not trust partimage writing to ntfs just yet. you can however backup the windows install at a "files" level, so mount the windows install in a live cd, then use tar to backup everything onto a seperate drive that is mounted also. backup the other partitions using tar as well. then simply restore it using live cd after you completely delete partition table, all partitions and recreate them using gparted. you won't be able to boot the windows install though because the mbr didn't get backed up so make sure you do that also!!! that is done with this command

 dd if=/dev/hdx of=/path/to/image count=1 bs=512 

and then to restore it from within a live cd

 dd if=/path/to/image of=/dev/hdx

this is most likely your best cleanest route. otherwise you may have iussues in the future due to partitions being out of order, maybe. ghost for linux works also to backup the files.

can't help ya otherwise?..

---

### Post by zazen666 on 2007-04-23
> **wldstrm said:**
> bump
I just noticed that my drives current partitions are listed, in order: 
/dev/sda1 - Windows install nfts
/dev/sda2 - extended
/dev/sda5 - personal files nfts
i dont knew where sda 3 and 4 are


Usually, It seems that computers random pick numbers to assing to the hard drive, if you do not choose the numbers yourself. The above means you have 3 pations. 1,2 and 5. You dont have a 3 or 4.

I had some succes with the Gpatitio Live CD (not in ubuntu). I booted it up and re partioned my HD, then threw the ubuntu live cd in and everything was numbered and named the way I wanted.
Good luck

---

### Post by wldstrm on 2007-04-24
Wow zazen666 that worked great, piece of cake once i used an actual gparted live cd and not the one in xubuntu.

---

