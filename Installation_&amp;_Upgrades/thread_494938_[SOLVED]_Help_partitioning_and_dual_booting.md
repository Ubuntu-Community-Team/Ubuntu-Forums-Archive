---
title: "[SOLVED] Help partitioning and dual booting"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by kholdstare311 on 2007-07-07
I've read up alot on partitioning and dual booting with XP and Ubuntu recently, and decided it might not kill me to give it a shot with my laptop (already checked out that it's Linux compatible). The only issue is that I'm not quite sure exactly how large the partitions should be, and I've also got concerns about the files and documents already on the computer.

With the partition issues, I know I should have an XP partition, the linux partition, a swap partition, and I know I can have a larger partition (FAT?) to use for all of my personal documents and to be read/writeable to both the Windows and Linux OS's.

1. I've got a small hard drive (showing about 68g taken up right now, and about 15 free, or something of the sort) and I don't know the required minimum sized for each partition, could anyone help me out there? I'd like as much room in the documents partition as possible, of course.

2. Would the FAT partition that shares documents between Windows and Ubuntu function as my seperate /Home partition?

3. Can I partition my hard drive now, and keep all of the documents and files that are on it safe? Will I have an option of exactly which files to shift over to  the /Home partition and what things will stay packed in the Windows partition?

Also, one more thing that will make me sound extremely stupid, but would the Program Files and such that are on the computer now, and that get installed later on, be put in the Windows partition with the OS, or should they go into the documents partition as well?

Thanks!

---

### Post by Pumalite on 2007-07-07
Dual booting with XP: defrag several times, erase temp files, then partition. With that size drive and that much taken up, I'd suggest you use the rest of the drive for Ubuntu; then mount XP through console or /etc/fstab on boot with the use of fuse and ntfs-3g. I'd suggest you backup all your data prior to installation. Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
A possible squeme: 6GB for'/', 500MB for /swap, the rest for /home.

---

### Post by louieb on 2007-07-07
Hi kholdstare311, 68 gig used 15 gig free. That about 80%  used. Your already close to the recommended limit. NTFS and for that matter most file systems slow down after reaching 80% full. At about 90% full writing really starts to get slow.  

With that in mind I don't believe I would try to shrink your NTFS partition. You stand a good chance of loosing some or all of your data. 

If it were mine I would not try to set it up to dual boot until more space is free on that drive.

---

### Post by kholdstare311 on 2007-07-07
Yeah I figured it would be a problem, but I've got that covered. Right now most of the disk space is being used up by backed up videos and my mp3 collection, which can easily be stored on my ipod temporarily while I fiddle with getting the computer to dual boot. The rest of the drive is taken up by a few programs which take up many gigs of space whether through their actual files or their installation packages.

I also plan to get some kind of external HDD to start storing all of my movies and music on (which would be living peacefully on the iPod until the HDD is bought). I know it's not the place, but if anyones got some suggestions on budget-in-mind external HDDs and the like, I'm all ears.

I've just scanned through and come up with a rough estimate here of how much space I can gain by moving all music and video, as well as program installation files and important documents over to another HDD, and it seems I could gain somwhere around 26 gigs by doing so, and maybe a few gigs by temporarily uninstalling some large apps. This would leave me with roughly 39gigs taken by windows and everything else on the current partition, and about 44 gigs free. Also in looking at the computer I notice I've forgotten to account for a partition on the drive called "HP Recovery", which is 6.36 gigs.

Now, assuming I clear all this space and such, is it a bit easier to help me out?

Also I'd still like to know if I'd lose all my information on the drive as it is, in other words, would I have to reinstall every single program for windows, and make sure i back up every single bit of data?

---

### Post by Martin Witte on 2007-07-07
you can resize your ntfs drive. for space requirements of ubuntu see [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements). if you want to access your data from both  windows and linux you might want to create an extra fat32 partition, and use hat for data storage. i did the resize of partitions not with ubuntu but with the systemrescue cd see [http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue).

---

### Post by kholdstare311 on 2007-07-07
I'm really at a loss for what to do right now. I guess what I want to be able to do is to do like I saw on some illustration that was used in a tutorial I read, which I can't remember where right now. It basically graphically showed a partition for the Windows OS at the beginning of the drive, a Linux partition at the end, followed by the Swap, and a large shared data partition in the middle. I'm assuming it would allow for both Windows and Ubuntu to access all of my music and videos, which would be stored in the middle partition, while the programs for each would be in their repective partitions. Am I correct in assuming this? Or is it that the actual windows OS will be on its own partition, but the installed programs (the Program Files folder basically) would be on the middle shared partition?

---

### Post by Pumalite on 2007-07-07
Windows OS uses ntfs and has to be in separate partition.

---

### Post by Martin Witte on 2007-07-07
see for instance this guide on how to setup a dual boot machine. [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html). more tutrials can be found with google [http://www.google.com/search?q=dual+boot+ubuntu](http://www.google.com/search?q=dual+boot+ubuntu)

---

### Post by kholdstare311 on 2007-07-07
THanks.

So let me get this right, if I clear off all programs i dont use or need, back up all the data i want to keep, defragment the drive a couple times (should I try a third-party defragmenter?), I can set up the partitions to keep about 25 gigs windows NTFS, 20 gigs linux ext3, 34 gigs shared FAT32 and 1gig /swap?

Those are just rough estimates, I'm really open to some more suggestions

---

### Post by louieb on 2007-07-07
Ok I'll try to   
2. ... FAT ... seperate /Home partition? No Linux  cannot run off of a fat partition it can read and write data stored on a fat partition. 

3. ... partition ...keep all of the documents ... on it safe?  Only if they are backed up.

Also, ...Program Files .... Windows .go in .. Documents partition as well? maybe - most windows programs will let you install them wherever you want. One of the the reasons the term _**dll hell**_ was created. 

(should I try a third-party defragmenter?), I use [JkDefrag: A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")

Partition sizes.
Windows XP. I have XP home installed on an 8 gig drive on one PC. it uses a little less that 5 gig of it. Win programs are pretty large give 15-20 gig. 
Ubuntu Linux / (root) 5-10  gig is plenty
Linux swap 1 gig should be enough. 
Linux /home. 1-2 gig. If you don't store any data in your home folder and all it holds is configuration files then 2 gig is plenty. Email eats up the most space in my home  partition. I have a separate data partition  for music, photos and the like.  Separate /home not really necessary but one of those nice to haves. :guitar:  
Shared data partition.  Whatever  is left. 

Really does not matter what order the partitions are in on the disk. The only exception to that is XP should be on a primary partition. 

 ...budget-in-mind external HDDs.... a lot less that your ipod and Wal-Mart or FRYs... that is unless you get monster size drive... which  come to think of it not a bad idea...

---

### Post by kholdstare311 on 2007-07-07
Thanks for the reply. You pretty much summed up the rest of what I needed at this point, which is some decent suggestions on partition sizes for the Windows and Linux partitions. I had already assumed that most windows programs could be installed anywhere I please (obviously), but was unsure of exactly how Linux apps are installed and such, I had no clue how large to make the partition, especially if I needed to install all apps into the / partition. 

Giving myself about 68 gigs (in reality the drive is showing me a little over 68 ) I've come up with this:

Windows NTFS - 20 gigs
Linux Ext3 - 10 gigs
Shared Data FAT32 - 35
/Home - 2 gigs
/Swap - 1 gig

Does this look decent enough, assuming I can clear enough space and defragment enough to squeeze what's on my current Windows partition into 20 gigs? Giving Ubunut 10 gigs won't bite me in the butt by way of making me run out of room for installing apps will it?

By the way, later on in the use of this setup If i happen to need to shrink the shared FAT32 drive and expand on of the others, It should be a fairly painless process, correct? I plan on keeping all of my music and video collection on a separate externall HDD (theres some nice 250gig ones for about $75 on NewEgg, whatcha think?).

Heck, I may even try to upgrade the internal HDD of this thing in the future, however I have no clue how easy or feasable this is for the model laptop i've got...

---

### Post by louieb on 2007-07-07
Just check the space on my year old Dapper 6.06 install / (root) uses  just over 3 gig. 
The Feisty 7.04 install on my laptop  / (root) uses 3.5 gig.  
I have all the normal stuff on both: office, multimedia players, 
Plus the Dapper install has LAMP, Samba and ftp servers installed, it also has the Ubuntu and Kubuntu desktops too.  

:confused: I guess I have to look into that: why does my laptops  / partition use more disk space even though it doesn't have as much software installed on it?    

Good luck with your Ubuntu install.

---

### Post by kholdstare311 on 2007-07-07
Thanks for helping out. 

Almost had a spot of bother - seemed Windows had about 32 gigs it didnt want to give back to me. Fortunately I had just forgotted to delete quite a few of the files I backed up earlier, in addition to some other unneeded stuff. The Windows OS now sits at a comfortable 10 gigs with most of my applications temporarily wiped. I'm thinking that I leave it with about 15 gigs it'll have room to grow, and any applications that I install for it (should be less than what I had earlier today - alot of stuff I rarely used or have better alternatives in Linux) can be installed on the shared FAT32 partition, am I correct in assuming this? And I'm also thinking that about 10 gigs for Linux should be plenty as well. Seeing as how most programs come packaged with Ubuntu already, I won't be needing a ton of space to grow on, right?

Or perhaps I can give my windows partition a bit more growth room with 20 gigs and be able to install most programs on the windows partition. Any thoughts?

Thanks again.

[eidt] One more thing bothering me - does how little I can make my windows partition depend entirely on how compressed I manage to get the files by defragmenting? As in, if all the files are compressed to the front half of the drive, but go all the way to the half, does that mean I have to make the windows partition 50% of the drive, and if I don't, my info gets canned?

---

### Post by kholdstare311 on 2007-07-07
Using the third party defragmenter mentioned earlier I was able to compress everything into a nice small place at the front of my drive, unfortunately there is a chunk of unmovable, undefragable files that are smack dab in the middle of the drive. The suggested article on dual booting on a laptop mentions this and mentions the causes, but doesn't say what to do about it - do i have to keep the windows partition at least large enough to stretch from the beginning of the drive and to include these, or is it safe to partition with it there? If I use the space it is in for the Shared partition would that work?

Please, I really need to know this, I can't go further without the info.

Thanks!

---

### Post by kholdstare311 on 2007-07-07
Okay, never mind. Seems I've taken care of the unmovable file problem, by temporarily disabling the windows Swap and hibernation. Hopefull yboth of these can be restored after the partitioning with no troubles.

Hopefully this will also be my last time defragging the computer - now I ca nfinally get on to the juicy stuff I've been preparing for for 10 hours.

Thanks for all the help guys.

and hey, another plus: with all this defragging and deleting and such, the computer runs like a champ! I don't think I've ever had a faster boot up or restart speed!

---

