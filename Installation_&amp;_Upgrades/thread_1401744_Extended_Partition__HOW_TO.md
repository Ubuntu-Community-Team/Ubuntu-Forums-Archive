---
title: "Extended Partition ? HOW TO ?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by Alxl on 2010-02-08
[SIZE=2]
[/SIZE]
 [SIZE=2]I would like to install  Ubuntu Netbook  Remix on my Asus 1005HA with XP and have dual boot.[/SIZE]
 [SIZE=2]But I already have 4 partitions.[/SIZE]
 [SIZE=2]How do I create an extended partition ?[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]See pics for detail:  [/SIZE]
 [SIZE=2]http://auctionpresto.com/user/0000000016/sized0000000668part1.JPG[/SIZE]
 [SIZE=2]http://auctionpresto.com/user/0000000016/0000000667Part2.JPG[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Thank you very much[/SIZE]

---

### Post by blur xc on 2010-02-08
fire up teh live usb stick, and go into gparted.  there you can set up all your partitions.  I'd create three for Linux (and have on a few dual boots I've recetly set up)- One ext4 for Ubuntu (I make it around 20gig, but 10 gig might be enough- I just noticed my netbooks only use 3 or so gigs for the / partition, my desktop takes closer to 9 gigs, ymmv).  Then, one for swap space, the size - well, you can google that one.  In my short experience w/ Linux, it doens't need very much swap space; 1 gig or 2 should suffice.  Then leave the rest for your /home partition (ext3).  My dual boot netbooks and laptops w/ windows recovery partitions have like 7 total partitions...

BM

---

### Post by Alxl on 2010-02-08
Sorry about the pics not clickable.

It's like this:

  	 	 	 	 	 	  sda1 nfts 77GB  
 sda2 ntfs 40GB  
 sda3 fat32 524MB   
 sda4 49 mb unknown  
 37MG unusable  
 and free:34.8GB

---

### Post by Alxl on 2010-02-08
> **blur xc said:**
> fire up teh live usb stick, and go into gparted.  there you can set up all your partitions.  I'd create three for Linux (and have on a few dual boots I've recetly set up)- One ext4 for Ubuntu (I make it around 20gig, but 10 gig might be enough- I just noticed my netbooks only use 3 or so gigs for the / partition, my desktop takes closer to 9 gigs, ymmv).  Then, one for swap space, the size - well, you can google that one.  In my short experience w/ Linux, it doens't need very much swap space; 1 gig or 2 should suffice.  Then leave the rest for your /home partition (ext3).  My dual boot netbooks and laptops w/ windows recovery partitions have like 7 total partitions...

BM
Thanks [blur xc]("http://ubuntuforums.org/member.php?u=848014") for your reply.
I am not too experienced and not that comfortable with partitions. The installer has GParted but I don't really know how to set up a new extended partition. I could delete one of the 4 partitions but don't know what is there.
Hope you can tell me about making a new extended partition

---

### Post by Alxl on 2010-02-08
BM
As I re-read your post in which you say that you have some 7 partitions, it is very likely that you only have 3 logical partitions and 1 extended partition  since no computer allows one to have more than 4 logical partitions.

That is my problem and I hope that somebody can help me re-arrange the partitions -  I would need step-by-step instructions if at all possible.

Thanks

---

### Post by blur xc on 2010-02-08
> **Alxl said:**
> BM
As I re-read your post in which you say that you have some 7 partitions, it is very likely that you only have 3 logical partitions and 1 extended partition  since no computer allows one to have more than 4 logical partitions.

That is my problem and I hope that somebody can help me re-arrange the partitions -  I would need step-by-step instructions if at all possible.

Thanks

Yeah- you need to know what is on each of those partitions.  Chances are windows exists on one of them, one is blank space, and antoher is the recovery partition.  Axe the one that is blank space (data storage) and shrink the windows partion, imo to be end up around 50% full (or empty, depending on your point of view).  Then take the remaining unallocated space, click it (or double click it) and change it to be an extended partition, then click in it again and create your linux patitions.

BM

edit- It was a trial and error process for me when I figrued it out the first time...  The error beign wiping the hdd completely on the first one I did- not a huge deal, but a dual boot would have been better.  That machine right now is just a clean 9.10 nbr install.

---

### Post by blur xc on 2010-02-08
Ok- looking at your pics I think I understand what's going on...but verify this before doing anything horribly damaging!  sda1 is your windows boot partition, with the OS on it.  sda2 is an empty storage partition.  It's confusing, because some space looks taken up, but it's not much, and I think that's space reserved for the journaling file system.  It's not actually any data.  Then you have a big chunk of unallocated space (sloppy on the ones who built your computer).  The remaining patitions, I think, are part of the windows recovery junk.  So, what I'd do, is shrink sda1 way down, to like 20 or 30 gigs, axe sda2, and make all the remaining unallocated space an extended partition, and then create the three new partitions in that extended partion.

Then during the install, there's an option to manually select what partitions you want mounted where.  Make your first mount to /, the 2nd mount to /home, and leave the last for swap space...  It's easy when you see it.

BM

---

### Post by Alxl on 2010-02-08
ok more info - checked it in Windows :


 72   gb  partition is  windows
 47  mb is              efi partitions
 37  gb is 99 %free but   cannot  figure out what it contains
 

 Should I delete this last 37.26 gb partition  - 65.6 mb are used   but but don't know for what .

---

### Post by blur xc on 2010-02-08
> **Alxl said:**
> ok more info - checked it in Windows :


 72   gb  partition is  windows
 47  mb is              efi partitions
 37  gb is 99 %free but   cannot  figure out what it contains
 

 Should I delete this last 37.26 gb partition  - 65.6 mb are used   but but don't know for what .


Boot into windows a look to see if anything is on it.  I *think* that's 65mb is just part of the ntfs journaling file system.  But yeah, that's what I'd do (and have done).  Shrink down the first one, kill that 2nd one, and use the rest for Linux.

BM

---

### Post by Alxl on 2010-02-08
Never found out what the 65MB were about. I deleted that partition in Windows and got a large unallocated partition, made it an "extended partition" while still in Windows and than used a  USB to install Ubuntu - it is doing this right now!

Thank you very much!

---

