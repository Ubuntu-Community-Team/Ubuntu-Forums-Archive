---
title: "Messed up hard drive in dual boot attempt"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by bball2601 on 2011-07-28
I was attempting dual boot my computer (ubuntu 11.04 and windows 7) and when I got to the stage to allocate drive space I accidentally formatted the largest partition of my hard drive to a linux swap.  My computer froze while it was formatting the drive and I was forced to power off my laptop.  Windows was my original operating system and was installed on the partition that is now formatted (or maybe not because of the crash during the formatting) as a linux swap.  Therefore my windows no longer works and I cannot restore my computer for a backup because it wont let me restore it to the partition that is now a linux swap.  Now when I boot from the linux install cd I get an error and am not able to install ubuntu or format/allocate drive space.  Is there a way I can reformat and fix my harddrive so I can them restore windows.

---

### Post by Frogs Hair on 2011-07-28
It sounds like your Windows installation my be history . If that is the case you could insert the Windows cd if you have one and  do a fresh Windows installation The drive would be reformatted to prepare for the Windows installation .

---

### Post by bball2601 on 2011-07-28
Just now I was able to format the linux swap partition back to ntfs using gparted from the live install disc, however when I tried to install windows using acronis true image it says that out of ntfs 500gb partition there is no usable space.

---

### Post by Hakunka-Matata on 2011-07-28
Welcome to the Forum, sorry about the circumstances!

Boot from your Ubuntu liveCD and select "Try without installing?, and examine your hard drive with Gparted.  
Or use ```
sudo fdisk -lu
```and post the results

---

### Post by bball2601 on 2011-07-29
I was able to fix it with gparted, then restore windows to the factory settings, and finally restore everything from my acronis back up.

Now I want to try to dual boot again, but I am a little confused as how to do this.  My problem is I have a HP dm4, so by default the hard drive is partitioned into 4 primary partitions:

C: 580 gb (which is the main partition where windows is)
HP_TOOLS 99mb
RECOVERY D: 14 gb
SYSTEM 199mb

It is my understanding that there can only be 4 primary partitions on and hard drive, and if I want to dual boot linux needs a primary partition of its own.  However, I don't want to delete any of the current partitions and ruin windows, especially after the recovery files just saved my computer.

Sorry for making this so long, but my real question is how should I set up my hard drive so that I can have everything for windows, along with the recovery and hp partitions, and ubuntu?

---

### Post by Quackers on 2011-07-29
You are correct in that you can only have 4 primary partitions on a mbr partitioned disc.
What others have done in your situation is to delete the HP TOOLS partition, then defragment the C: drive and then shrink the C: drive using Windows Disk Management console.
At this point you will have 3 primary partitions and some unallocated space.
You can then boot from the Ubuntu live cd/usb and open gparted or use the Ubuntu installer and select the "something else" option, and create LOGICAL partitions for swap and Ubuntu's root (/) partition, giving the latter the " / " mount point.
This will create an extended partition, which then becomes your 4th primary partition, inside which you can have as many LOGICAL partitions as you wish.

---

### Post by bball2601 on 2011-07-29
Thanks for the info quacker.

After some consideration I decided I want to leave hp tools just in case there is anything there I would potentially need.

Now I'm thinking of deleting the recovery partition, and the making a new partition for ubuntu.  Before doing this I would make a recovery cd.  With a physical copy of the cd I should be able to completely reinstall windows, having it repartition my drive and restore to factory settings (worst case scenario). Wouldn't this make the recovery partition kind of redundant and unnecessary, therefore a good option for a partition to delete?

---

### Post by Quackers on 2011-07-29
The HP TOOLS partition contains diagnostic tools which, as I understand it, can be downloaded from the HP website, if needed. You can check that first if you wish to do that.
I can tell you one thing though. You are likley to need the recovery partition long before you are likley to need the HP TOOLS partition.
That said, it is ALWAYS a good idea to make the set of recovery dvd's. In fact, I make 2 copies.

---

### Post by bball2601 on 2011-07-29
The only thing I'm worried about with hp tools is I don't know how to access the files or back it up, and I also heard that hp updates can sometimes create the hp tools partition so I'm worried if after I have both OS installed a hp update creates the hp tools partition and then I have 5 primary drives, making it a dynamic drive or something like that.

---

### Post by Quackers on 2011-07-29
If the tools are available on the HP website that shouldn't be a problem.
I have not heard of updates re-creating partitions before and that seems odd to me. Running a recovery would re-create the original partitions (all 4) and over-write Ubuntu. Maybe that is what you've read, perhaps?

Obviously you should do whatever you're happiest with :-)

---

### Post by bball2601 on 2011-07-29
Thanks for you advice, I think I'm just going to get rid of the tools partition.

And what I said about recreating the tools partition can very easily be wrong, its just something someone else posted.

---

### Post by Quackers on 2011-07-29
Whether you delete the recovery partition or the HP TOOLS partition you will still need to defragment the C: drive and shrink it to create free space for Ubuntu to install into (unless you will be happy to use just the space that the recovery partition used).

---

### Post by bball2601 on 2011-07-29
Yea I'm going to do that in disk manager and leave space where ubuntu can be installed.  

From the installation disc will I have to format separate logical partitions for the boot, root, and swap, or can I simply choose the unallocated space left from the shrinking of windows and automatically set up the boot, root, swap partitions?

---

### Post by 23dornot23d on 2011-07-29
There is another option - USB hard drives are cheap ....  just plug one in  and set BIOS to boot from it
install Linux .... 

These also allow you to boot Linux from them ...... just another option ,,,,, 

sorry for butting in .....

---

### Post by Quackers on 2011-07-29
I would do it from within the installer, as you'll need to give the partitions mount points whether you have created them first or not.
Separate boot partitions are not normally needed and just serve to complicate matters. A separate home partition is often used, but that is not necessary, as such.
Any new partitions must be logical type - not primary, that's the important thing.

Edit  See above post for another option.

---

### Post by 23dornot23d on 2011-07-29
Cheers Quackers ..... I should also add the BIOS needs to be able to boot from an external USB device

check this first ..... most newer computers seem to have this ...... but some older ones do not ...

ok hope it solves a problem ...... seen a few threads now explaining 4 primary partitions ...... how crazy
is that ...... ( they are definitely worried about Linux now - to be getting the manufacturers to do this )

---

### Post by Quackers on 2011-07-29
"cynical" would be my word for it :-)

---

### Post by bball2601 on 2011-07-29
Thanks for the suggestion dornot.
I considered the external hd method but eventually decided against it because I am doing this all on a laptop and requiring the external hard drive would make it hard to use ubuntu in class or some other places.

---

### Post by 23dornot23d on 2011-07-29
> 
"cynical" would be my word for it :smile:
                                                                                               __________________
Possibly they do not know how to create extended partitions ..... who knows .... or maybe I am getting a little cynical in my old age .....


> 
Thanks for the suggestion dornot.
I considered the external hd method but eventually decided against it  because I am doing this all on a laptop and requiring the external hard  drive would make it hard to use ubuntu in class or some other places.     
You are welcome .... another thing is Flash Cards for portability ( I have used them before )
 ,,,,, but I have never found one fast enough ...... but maybe they exist now with [[COLOR=Blue]_***greater data transfer speeds***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1813102")  ..... no doubt at a cost too .....

But creating 8 to 20 Gig  or so on the main hard drive is nothing of a task really  .. ok will leave it now best of luck ... ):P

---

