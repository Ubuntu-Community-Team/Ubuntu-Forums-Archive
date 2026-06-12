---
title: "Help with partitioning?"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by kiriyama on 2007-05-27
Hello, I am trying to install Ubuntu 6.06, and I have run into a problem with partitioning.  I currently am running winXP, and would like to be able to still use it, so I am creating partitions in the remaining unallocated space, after resizing a NTFS partition called /dev/sda2.

The problem I have run into is creating a second partition for my user directories (already created the system partition).  The installer tells me I cannot have more than 4 primary partitions -- the ones I currently have are called /dev/sda1 (fat16 filesystem),  /dev/sda2 (ntfs filesystem), New Partition #1 (ext3 filesystem) and /dev/sda3 (fat32 Filesystem).  What should I do?

Thanks for your help,
Kiri

---

### Post by louieb on 2007-05-27
Need more that 4 partitions? Time to learn about extended and logical partitions. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by kiriyama on 2007-05-27
Hmm... I'm a bit worried.  I read up on the extended partitions and whatnot, and when I deleted the 4th partition that I had made, created an extended partition, with 3 logical partitons inside of it, (two of type ext3, one linux-swap), and clicked forward, it messed up creating the linux swap partition, said that this may affect my other partitions, and now my previous NTFS filesystem is back at it's original size(144 from 130 gb), colored black, labled an "unknown" filesystem, and has a warning logo next to the partition name.  the extended partition is now only 7.84 mb (from around 14 gb), the linux-swap partition is missing, and the two logical partitions inside of the extended are also labled "unknown", with warning triangles.

I'm lost.  is windows now damaged? have I essentially destroyed the 120 gb that was in the NTFS partition?  I really don't know what to do, and I'm really worried.

Thanks,
Kiri

---

### Post by kiriyama on 2007-05-27
Is there a way to revert what has been done?  I'm seriously sweating bullets over this.  I have thousands of dollars of music, 5 years of media, game saves, documents (nothing that could ruin my life or anything like that.  I graduated yesterday, all my school work I was going to get rid of anyways, no real important information... but still.) etc etc.  I'm not going to do anything till I get a response, lest I make something that could be recovered unrecoverable.  But if I were to cancel the installation, eject the disk, and restart my computer, would windows boot?  I now realize how goddamn stupid it was to go ahead and install without backing everything on my disk up, so just telling me that I should have done that would not help... any suggestions? Anyone?

Kiri

---

### Post by merlinus on 2007-05-27
Can you boot from your original windows disk?  If so, there may be a restore option that will let you load your windows partitions.

You need to try to restore the MBR, which is the master boot record.

Another thing to try is booting from the Ubuntu live cd, and see if you can find your two windows partitions.

Good luck!

-merlin

---

### Post by louieb on 2007-05-27
So where are you at with the install? 
Were you able to boot to win after your first attempt to partition. (before you created the extended partition)?
Do you have a external hard drive?  if windows is trashed you may still be able to copy your data off. 
If you haven't finished the install the machine should still try to boot windows. I would try that first. 
If that doesn't work. You can try useing your XP CD and run fixboot and fixmbr. I've not had much luck with either. 
But  I have been able in the past to use a Live CD to copy my data off. 
I can think of 4, two of which I've used. they are [Knoppix Linux]("http://www.knoppix.net/") , [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1")  , [SystemRescueCd]("http://www.sysresccd.org/Main_Page") , and [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") ,and one more  [TestDisk - CGSecurity ]("http://www.cgsecurity.org/wiki/TestDisk")  its also on the System Rescue CD.
Try one of the first two. Use there file manager and try to browse your NTFS data. If you can browse it you can copy it off. 
If not get one of the other two. I've not had to use one of them yet but they have instructions for repairing messed up partitions and copying data off. Good Luck.

---

### Post by jerrylamos on 2007-05-27
> **kiriyama said:**
> Hello, I am trying to install Ubuntu 6.06, and I have run into a problem with partitioning.  I currently am running winXP, and would like to be able to still use it, so I am creating partitions in the remaining unallocated space, after resizing a NTFS partition called /dev/sda2.

The problem I have run into is creating a second partition for my user directories (already created the system partition).  The installer tells me I cannot have more than 4 primary partitions -- the ones I currently have are called /dev/sda1 (fat16 filesystem),  /dev/sda2 (ntfs filesystem), New Partition #1 (ext3 filesystem) and /dev/sda3 (fat32 Filesystem).  What should I do?

Thanks for your help,
Kiri

I use one partition for Ubuntu and one for swap.  I don't see any use in fragmenting the Ubuntu partitioning with the chance that one partition would fill up and others be not full but a mess to re-allocate.

By the way, I have best luck with CD Live doing System, Administration, Gparted for the partitioning, not the limited function partitioner in Install.

Frankly, with 4 partitions I would do:
Partition 1 hard drive 1 for Microsoft.  They demand to be first.

How much space did you free up when you resized XP?  I defrag with paging space 0 to get as much as I can.

Suppose you had 40 G left over.  Then I'd do:
Partition 2 Linux 20 G  for Dapper?  Edgy?
Partition 3 Swap 1 G    used by whichever Linux partition is booted
Partition 4 Linux 20 G  for another Linux to try - Feisty?  Competitive?

Now 10 G each will do, but I like to download new Linux CD's to try.  Photos or music can chew up some space too.  That's a triple boot system.  (The one I'm using now is quad boot.)

I always like to have a Linux that works, example Edgy 6.10 or Dapper 6.06, and then have a Linux partition to try a new Linux example Feisty 7.04.  That way  if something doesn't work on the new one, I've still got the previous one to use.  Note it is easy to copy files between them.

Or,  Partition 4 could be an extended Partition, and within that if you have enough space several more partitions.

Do note the Grub bootloader will use the /boot/grub/menu.lst (where l is lower case L) from the last Linux to install, in case you want to edit it.  I always do.

Cheers, Jerry

---

### Post by kiriyama on 2007-05-28
> **louieb said:**
> 
1. So where are you at with the install? 

2. Were you able to boot to win after your first attempt to partition. (before you created the extended partition)?

3. Do you have a external hard drive?  if windows is trashed you may still be able to copy your data off. 

4. If you haven't finished the install the machine should still try to boot windows. I would try that first. 

5. If that doesn't work. You can try useing your XP CD and run fixboot and fixmbr. I've not had much luck with either.
But  I have been able in the past to use a Live CD to copy my data off. 
I can think of 4, two of which I've used. they are [Knoppix Linux]("http://www.knoppix.net/") , [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1")  , [SystemRescueCd]("http://www.sysresccd.org/Main_Page") , and [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") ,and one more  [TestDisk - CGSecurity ]("http://www.cgsecurity.org/wiki/TestDisk")  its also on the System Rescue CD.
Try one of the first two. Use there file manager and try to browse your NTFS data. If you can browse it you can copy it off. 
If not get one of the other two. I've not had to use one of them yet but they have instructions for repairing messed up partitions and copying data off. Good Luck.


1.  I had just set the partitioner from the installer to leave the 3 partitions for windows, and set up an extended partition with 3 logical partitions for linux (root, directories, and swap).  I clicked next, it started to perform the operations, and failed on the last one, creating the swap partition.  A warning appeared saying this, and saying that it could affect the other partitions, and I clicked OK.  Now the installer shows the partitions as I described.

2. I did not reboot the computer after my first, failed attempt to create a 5th primary.  I went on here and asked what to do, then I created the extended partition, etc, as I said in #1.

3. Yes, I have an external terrabyte, but I have windows installed, and was trying to install linux, on my internal 144GB hard drive.  I did nothing with the external one, and it appears to still work.

4. I think this is what I'm going to try first thing tomorrow.  I havent touched my computer since the operation failed(I've been using my mom's macbook to post), because I didn't want to cause any more damage than I possibly have already.  Correct me if I am wrong, will I just cancel the installer, reboot, eject the CD before it tries to boot an OS, and hope it boots windows?

5. I don't think I have an XP installer CD, but I do still have the ubuntu live CD, as well as a knoppix one.  One thing I'm worried about though is that it does not currently recognize my NTFS partition as being any kind of filesystem.  It says "unknown" and has a triangle with an exclamation point next to it (same with the 2 logical partitions in the extended;  the swap partition is gone, but it still recognizes the extended partition as such.)

Alright, I'm going to leave the computer alone for now, and try #4 in the morning.  Thanks for all your help, and wish me luck!

Kiri

---

### Post by darell_m on 2007-05-28
Take very much care with partitions as I **used **to have a dual boot with XP and got playing with gparted and now only have Ubuntu as reloaded for full disk, as deleted the Windows Partition (sounds silly doesn't it) adn many attempts to fix MBR failed. Guess on the bright side I had all important data files backed up on data deposit box server and now I will learn to use Ubuntu and enjoying it. Mind, I have 2 other XP's in the house on LAN.

---

### Post by kiriyama on 2007-05-28
> **darell_m said:**
> Take very much care with partitions as I **used **to have a dual boot with XP and got playing with gparted and now only have Ubuntu as reloaded for full disk, as deleted the Windows Partition (sounds silly doesn't it) adn many attempts to fix MBR failed. Guess on the bright side I had all important data files backed up on data deposit box server and now I will learn to use Ubuntu and enjoying it. Mind, I have 2 other XP's in the house on LAN.

This is what I am worried about.  I have no idea whether or not my NTFS partition is ruined or not.  It shows up as existing, but as an unknown filesystem.  If I can possibly get windows working with my documents and all intact, the first thing I am going to do is copy my whole hard drive to my external one.  It was really stupid of me to start this without first backing up all of my information. After a scare like this, I am NEVER not backing all my stuff up before messing with anything... Besides, after I get both up and working, I'll not have to mess with partitions again (I never had any desire to), because if my directory gets filled up, I can just put stuff on my external.

---

### Post by louieb on 2007-05-28
> **kiriyama said:**
> 1.  I had just set the partitioner from the installer to leave the 3 partitions for windows, ...

2. I did not reboot the computer after my first,

3. Yes, I have an external terrabyte, 

4. ...Correct me if I am wrong, will I just cancel the installer, reboot, eject the CD ...

5. I don't think I have an XP installer CD,...[LIST=1]
[*]OK
[*]I would not go any further with the install. Best to abort and reboot.
[*]Great
[*]... and Hope it boot to windows.
[*]The Knoppix live CD should have an icon on the desk top for your NTFS partition. If things go great clicking on it will open the file manager .... copy away to the external.[/LIST]I hope windows boots. If it does it will probably  complain and want to run scandisk, go ahead and let it. 
The only time I trashed XP trying to dual boot a pc I got in a hurry and did not defrag first. Had partitioning problems similar to yours. Lucky  was able to get my data copied off with Knoppix.

---

### Post by kiriyama on 2007-05-28
> **louieb said:**
> [LIST=1]
[*]OK
[*]I would not go any further with the install. Best to abort and reboot.
[*]Great
[*]... and Hope it boot to windows.
[*]The Knoppix live CD should have an icon on the desk top for your NTFS partition. If things go great clicking on it will open the file manager .... copy away to the external.[/LIST]I hope windows boots. If it does it will probably  complain and want to run scandisk, go ahead and let it. 
The only time I trashed XP trying to dual boot a pc I got in a hurry and did not defrag first. Had partitioning problems similar to yours. Lucky  was able to get my data copied off with Knoppix.

Hmm... when I went to reboot, all that was displayed was something about a "bad pbr".  When I booted knoppix, there was no icon on the desktop for the NTFS partition (possibly because it is not labled as such?  I think that just the filesystem identity could be messed up, because neither knoppix nor puppy linux had any clue that there was 144 gb of unidentified space on my harddrive.  Right now, I am downloading systemrescuecd.  I'll let you know how that goes.

Thanks,
Kiri

---

### Post by kiriyama on 2007-05-28
> **kiriyama said:**
> Hmm... when I went to reboot, all that was displayed was something about a "bad pbr".  When I booted knoppix, there was no icon on the desktop for the NTFS partition (possibly because it is not labled as such?  I think that just the filesystem identity could be messed up, because neither knoppix nor puppy linux had any clue that there was 144 gb of unidentified space on my harddrive.  Right now, I am downloading systemrescuecd.  I'll let you know how that goes.

Thanks,
Kiri

UPDATE:  SystemRescueCD worked!  I still have all my files, data, etc.  Thank you so much for your help, you really saved my butt big time.  I will try to install linux again, but not without first understanding what went wrong the first time, defragging my harddrive seveal times (I did once, but it still was rather fragmented), and backing up my entire hard drive to my external.


Again, thanks so much!
Kiri.

---

