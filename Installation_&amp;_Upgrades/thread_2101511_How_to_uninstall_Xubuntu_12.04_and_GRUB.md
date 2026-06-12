---
title: "How to uninstall Xubuntu 12.04 and GRUB?"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by Sky Aisling on 2013-01-04
How to uninstall **Xubuntu 12.04** and **GRUB v1.99-2lubuntu3.7** ?
What next to try? 

I installed XUbuntu 12.04 along side Ubuntu 10.04 
I installed XUbuntu 12.04 from a Live CD. 
I accepted all the upgrade/updates offered after the install. 
The OS booted from GRUB menu at startup.  No bootup issues. 
I now want to uninstall XUbuntu 12.04 and remove GRUB screen.

Note: I have tried these terminal scripts by entering them from Ubuntu 10.04  installed, XUbuntu 12.04 installed, XUbuntu 12.04 live CD uninstalled. 

I have tried ***removing*** with terminal command from:  [http://www.psychocats.net/ubuntu/pureubuntuprecise](http://www.psychocats.net/ubuntu/pureubuntuprecise) 
No luck. 
I have tried ***purging*** with terminal command from:  [http://askubuntu.com/questions/92084/how-to-remove-xubuntu-desktop/92089#92089](http://askubuntu.com/questions/92084/how-to-remove-xubuntu-desktop/92089#92089) 
[SIZE=2][COLOR=Magenta]*sudo apt-get autoremove --purge xubuntu-* && sudo apt-get autoremove  --purge xfce* *[/COLOR][/SIZE]
Partial luck. 
This last command purged some of the OS but not all. 
The desktop still exists. 

In addition, **Grub v1.99-2lubuntu3.7** screen continues to appear at startup. 
Grub displays and boots: 
[I]Ubuntu with Linux 3.2.0.35-generic [SIZE=1] ED Note: this is XUbuntu 12.04[/SIZE] 
Ubuntu with Linux 3.2.0.35-generic (recovery mode) 
Previous Linux Versions 
Memory Test 
Ubuntu with Linux 2.6.32-45-generic  [SIZE=1]ED Note: this is Ubuntu 10.04[/SIZE] 
Ubuntu with Linux 2.6.32-45-generic (recovery mode) [/I]
The two above lines repeat multiple times on remainder of screen. 

[COLOR=Green]QUESTION: How do I completely rid the machine of XUbuntu 12.04? (without loosing  Ubuntu 10.04) 
*and, *
How do I remove the GRUB screen? [/COLOR]

Previous to this adventure, Ubuntu 10.04 booted beautifully, in full  purple splendor, directly to the OS without intervention from GRUB. 
Ubuntu 10.04 has worked perfect for 3 years.  Thank you Lucid Lynx  developers. The system has been a pleasure to use.

The Machine in use is a **ZaReason Big Lap with 3 gigs of RAM, 150 gigs  storage, Intel Celeron M CPU 410@1.46GHz.** 

Here is a screenshot of the file system and GRUB configuration text. 
I had setup two extra partitions to accept X12.04 and U12.04 (never got  that far with U12.04) but deleted them in hopes of ridding the machine  of XUbuntu 12.04. 

PS-Ubuntu 10.04 appears to be uneffected by the various attempt to purge  the machine of XUbuntu 12.04. 
Yes, I have backed up data. 

Thank you in advance for any guidance you can give. 

-- 
Sky

---

### Post by darkod on 2013-01-05
Do you have only one disk, /dev/sda?

It's simple. Boot yuor 10.04 and open terminal and execute:
sudo grub-install /dev/sda

Under assumption the disk you use is /dev/sda. That will install the grub2 from 10.04 as the main bootloader on the MBR.

After that you can simply open Gparted in 10.04 and delete the Xubuntu partitions. When you are done deleting them, run:
sudo update-grub

To clear the grub2 menu from Xubuntu. That's it.

Later you can either expand the 10.04 partition to include the unallocated space created when you deleted Xubuntu, or simply make a new ext4 partition and use it in 10.04 because sometimes expanding partitions is risky.

---

### Post by Sky Aisling on 2013-01-05
**darkod**,
Thank You!
Yes, the machine has one disk, /dev/sda.
Yes, your suggestion worked perfect, there is no more GRUB screen showing at boot up.  The system goes directly to Ubuntu 10.04 as it's done for years.

> It's simple. Boot yuor 10.04 and open terminal and execute:
sudo grub-install /dev/sdaIn addition you wrote:

> After that you can simply open Gparted in 10.04 and delete the Xubuntu partitions. When you are done deleting them, run:
sudo update-grubPrior to installing XUbuntu 12.04 this is what I did to prepare the disk:
Originally, the entire disk c.a. 150 gb was dedicated to Ubuntu 10.04.
I *resized* the sda1 from c.a. 150 gb to 30 gb with no issues. *(I have small data collection and need only small storage space)*
I created two more 30 gb partitions leaving an unallocated space and a swap partition with no issues.


The reason the two extra partitions were created is that in May 2013 the change-over to a new LTS OS occurs.
I created the two partitions to have space for XUbuntu 12.04 and Ubuntu 12.04 so that I can try them out by May.
[COLOR=DarkRed]Edit: Thank you **Bucky Ball** for the correction to the date of the new LTS release.  My mistake.  *[****]("http://ubuntuforums.org/member.php?u=504316")(see next post by Bucky Ball)*.[/COLOR]

The disk with the two new partitions plus the *resized* Ubuntu 10.04 partition did not show an extended /dev/sda2 partition *prior* to installing XUbuntu 12.04.
Once I determined I wanted to uninstall XUbuntu 12.04, I did the various terminal entries as listed in my original post.
I also deleted the two 30 gb partitions I had created to hold more OSes *(this was a guess to try to rid the machine of XUbuntu 12.04 and regain original GRUB boot)*.
Now that I installed and attempted to uninstall XUbuntu 12.04 the disk shows an extended partition on /dev/sda2.  GParted shows it as *busy*.
See screenshot below.

[COLOR=SeaGreen]Question: Is this extended partition where the remainder of XUbuntu is mounted?  Shall I attempt to delete it?[/COLOR]

---

### Post by Bucky Ball on 2013-01-05
There is no changeover to a new LTS in 2013. There is no LTS released in 2013 actually. The current LTS is 12.04 LTS and has been released since April 2012. It is supported for five years, until 2017. the next LTS release will be 14.04 LTS. They happen every two years.

You need to unmount any partitions you want to delete. You don't need to run code, purge, or anything tricky to get rid of Xubuntu. Boot from a LiveCD, unmount partition(s) in question, delete partitions, job done.

---

### Post by darkod on 2013-01-05
I assume you still didn't delete any partition since the Gparted image is the same as the previous one.

Your swap partition is now a logical partition inside the extended, so you will not be able to delete all of them since swap is in use.

Are you sure there were no logical partitions when you had only 10.04? I ask this since it seems the 10.04 is the /dev/sda5 and that is a logical partition.

In any case, it doesn't matter whether linux is running from primary or logical. You only have to be careful in planning the hdd and all partitions, nothing else.

---

### Post by Sky Aisling on 2013-01-05
Thank you for your timely response, **darkod**.

> I assume you still didn't delete any partition since the Gparted image is the same as the previous one.That is correct, I have not deleted any partitions since I did the restore of GRUB  in 10.04 per this thread post.

> Are you sure there were no logical partitions when you had only 10.04?No, I am not sure there were no logical partitions with the original 10.04 setup.

I am new to understanding partitioning. I am studying this tutorial in order to understand more clearly.
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Being the tidy sort that I am, I am concerned about the system holding unnecessary coding such as parts of XUbuntu.  I find many references to bits and pieces of XUbuntu when I do a search of the *file system*.  But, nothing in the search tells me which partition the left overs occupy.  Perhaps my question should be how to tell the contents of the partition so that I know which partition I can take back to zero?

When looking at the disk via GParted, it appears that sda6 (logical partition?) has some content and is not mounted.   *If* the content is the remnants of XUbuntu then this logical partition can be deleted to eliminate XUbuntu entirely?

---

### Post by Bucky Ball on 2013-01-05
> **Sky Aisling said:**
>    *If* the content is the remnants of XUbuntu then this logical partition can be deleted to eliminate XUbuntu entirely?

Yes.

---

### Post by Sky Aisling on 2013-01-05
If 'yes' then how do I tell what are the contents of sda6?

I want to be sure I am deleting only XUbuntu code.

---

### Post by darkod on 2013-01-05
If you are posting the Gparted from running your 10.04, it clearly shows you the root of 10.04 is /dev/sda1. In that case Xubuntu is /dev/sda6 and should be OK to be deleted.

---

### Post by darkod on 2013-01-05
Well, you have only two linux partitions (except swap), so if one is 10.04 then the other has to be the Xubuntu.

But if you like to see what is inside, open Nautilus (the file browser) in 10.04 and on the left side under Devices click on the 56GB partition. It will open and you can browse the content.

Note that clicking on it will mount it so you can look inside so if you want to delete it right away, when you open Gparted it will have the keys symbol next to it. You have to right-click it, and select Unmount. Only after that you can delete it.

---

### Post by Sky Aisling on 2013-01-05
**darkod**,

Thank you! That is the guidance I've needed. 
Yes, the screenshot was taken and posted from Ubuntu 10.04. 
Yes, sda6 does contain numerous XUbuntu files.
Yes, it makes sense that with only two linux partitions (except swap), one is 10.04 then the other has to be the Xubuntu as there are no other OSes installed on the machine.

I used ***Nautilus*** (the system file browser) to look at the file contents once the file was mounted.
I also used **system/administration/Disk Utility** to access the contents of sda6. 
Note: GParted must be closed in order for the mount and unmount features to work in ***Disk Utility***.

The home folder sidebar indicates a 60GB file system which confused me.  I've been searching for a 56.21GB file per GParted info.

I can now delete that file system using GParted in confidence that I'll not effect Ubuntu 10.04.
Most of all, it will free up space for future OSes.

I'll post after I delete the partition to finish up this thread.
If it ain't to wet to plow and I can dance then I'll mark the thread solved.

Thank you, **darkod** and **Bucky Ball** for your much appreciated assistance today.


Sky

---

### Post by Bucky Ball on 2013-01-05
All good, no probs. Remember though, that if it is sda6 and you want to delete it, it needs to be unmounted_* but so does every number under it; i.e. sda1, sda2, etc.*_ Which is why it is much better to do this from the LiveCD, NOT from the running install on your hard drive. That way everything can be unmounted as you are not running from an install on the hard drive. ;)

Good luck.

---

### Post by Sky Aisling on 2013-01-05
Oh, thank you, **Bucky Ball**, I'd forgotten about that!

---

### Post by Bucky Ball on 2013-01-05
Cool. Keep looking over that four leafed clover and all should be smooth ... ;)

---

### Post by Sky Aisling on 2013-01-05
Sda6 is deleted.
I used a Live CD of **Lucid-Puppy-528.005** (sans *save-file*) as it loads instantly into RAM and doesn't involve a HDD.
I used ***GParted*** to do the delete.
I am still confused as why there is a sda2 showing and it is mounted.
Where did sda2 come from? What's it purpose? Is it necessary?
I note that I left the swap file mounted when I did the delete. I wonder if that makes a difference?
I was hoping to see a system showing just sda1 with a lot of unallocated space, plus a swap file. (available to configure for other OSes)
Instead I see sda1 with unallocated space and sda2 with unallocated space.
But, perhaps that is a question for another thread and some woodshedding on my part to figure it out.  ;)
[COLOR=DarkRed]Edit:  Think I will try turning off Swap then deleting swap which will accumulate space into sda2 unallocated area.  Then I'll delete sda2 (extended) and that space will accumulate into the unallocated area of sda1. Then I'll recreate the swap file.   I'm hoping.  Any reason why not?[/COLOR]

Sky

---

### Post by Bucky Ball on 2013-01-05
You are looking for free space. Delete the partitions and recreate when you install by hitting 'Something Else' when you get to the partitioning part of the install. You can actually kill those partitions and make free space when you get there ...

---

### Post by Sky Aisling on 2013-01-06
**Addendum**

It worked!
I unmounted Swap which unmounted sda2.  
I deleted both swap and sda2.  
I created another swap from the pile of *unallocated* that was left over.
Now just sda1 with boot is present plus swap and a bunch of unallocated.
Ubuntu 10.04 presents properly.
Bootup appears to run faster.

---

### Post by Bucky Ball on 2013-01-06
Great news! Any more issues, post with a descriptive thread title in the appropriate forum. As mentioned, support for 10.04 LTS runs out in April this year. 12.04 LTS is five years, but in the case of Xubuntu it is the regulation three. 

Good luck, have fun and enjoy the new OS, the forums and the learning curve ... :wink:

---

