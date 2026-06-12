---
title: "problem resize windows partition"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Nifio on 2010-02-18
I have reinstalled windows, and when I wanted install ubuntu, during the partitioning, I had not the possibility to resize the windows partition and to make a new ubuntu partition. I could only completely delete windows to install ubuntu on the all disk. When I tried a manual partitioning, the used space on the windows partition was 'unknown', and I couldn't resize it. 
What is the problem and how could I arrange that?

---

### Post by Mark Phelps on 2010-02-18
> **Nifio said:**
> What is the problem and how could I arrange that?

Well basically, you've provided very little useful info ...

For starters, if your machine came with Vista or Win7, you should have used the builtin Disk Management utility to do the resize.  Then, it would have been a simple matter of booting from the Ubuntu CD and installing to the free space you just created.

If your machine came with XP, and you resized using the Ubuntu installer, it should have worked.

Also, HOW did you attempt to do the install -- to a new partition? Or, using Wubi inside Windows?

What version of Ubuntu were you trying to install?

And finally, boot from the Ubuntu CD, run in LiveCD mode, open a terminal, enter the following command "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

---

### Post by darkod on 2010-02-18
Also, at the start you said you reinstalled windows. If you were planning to add ubuntu why did you let windows take the whole hdd? If that's something you did recently, and you still haven't loaded windows with tons of software and data, just reinstall it again this time only on the part of the hdd you want to allocate to windows. Then just install ubuntu in the remaining unallocated space. Much better than shrinking.

---

### Post by ravosava on 2010-02-18
I am actually having a similar problem, any chance someone could help me?


I've been dual-booting with **Vista** and Ubuntu for a while, screwed up Ubuntu (never been able to get wireless working, although it works from the LiveCD) and am trying to do a fresh install. 

When I originally partitioned my harddrive, I gave Windows 120GB and Ubuntu 116GB, with 10GB going to Windows recovery and 4GB going to Linux swap. 

I've deleted the Linux partitions and have a partition that is 112 GB that is nothing but free space (where'd my other 17GB go?) and I want to allocate some of that space back to Window before I re-install **Ubuntu 9.10** but I don't know how. 

I'm using the Disk Management tool on Vista, but it doesn't give me the option to extend the drive. When I right-click on the free space, it just gives me the option to delete the partition. What should I do?
[COLOR="Red"]EDIT:[/COLOR] I figured it out, and now I feel silly.

---

### Post by Nifio on 2010-02-19
> **Mark Phelps said:**
> Well basically, you've provided very little useful info ...

For starters, if your machine came with Vista or Win7, you should have used the builtin Disk Management utility to do the resize.  Then, it would have been a simple matter of booting from the Ubuntu CD and installing to the free space you just created.

If your machine came with XP, and you resized using the Ubuntu installer, it should have worked.

Also, HOW did you attempt to do the install -- to a new partition? Or, using Wubi inside Windows?

What version of Ubuntu were you trying to install?

And finally, boot from the Ubuntu CD, run in LiveCD mode, open a terminal, enter the following command "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

I have windows vista, and used Ubuntu 9.10 doing the partitioning during the installation with the cd boot.

Here are the results:

Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xa8000000 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63      144584       72261   de  Dell Utility 
/dev/sda2          145408    21116927    10485760    7  HPFS/NTFS 
/dev/sda3   *    21116928   451411647   215147360    7  HPFS/NTFS 

Disk /dev/sdf: 1999 MB, 1999634432 bytes 
255 heads, 63 sectors/track, 243 cylinders, total 3905536 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x0047786d 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1   *          63     3905535     1952736+   e  W95 FAT16 (LBA) 
Partition 1 has different physical/logical endings: 
     phys=(242, 254, 63) logical=(243, 27, 40)

---

### Post by darkod on 2010-02-19
Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR=Red]625142448[/COLOR] sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xa8000000 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63      144584       72261   de  Dell Utility 
/dev/sda2          145408    21116927    10485760    7  HPFS/NTFS 
/dev/sda3   *    21116928 [COLOR=Red]  451411647[/COLOR]   215147360    7  HPFS/NTFS

You seem to have already shrunk vista, one way or another. You have around 85GB unallocated space after /dev/sda3.

Can vista boot OK right now? If it can, just boot with the ubuntu cd, select Install Ubuntu and in step 4 tell the installer to Use Largest Available Free space.
And that should be it.

---

### Post by Nifio on 2010-02-19
> **darkod said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR=Red]625142448[/COLOR] sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xa8000000 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63      144584       72261   de  Dell Utility 
/dev/sda2          145408    21116927    10485760    7  HPFS/NTFS 
/dev/sda3   *    21116928 [COLOR=Red]  451411647[/COLOR]   215147360    7  HPFS/NTFS

You seem to have already shrunk vista, one way or another. You have around 85GB unallocated space after /dev/sda3.

Can vista boot OK right now? If it can, just boot with the ubuntu cd, select Install Ubuntu and in step 4 tell the installer to Use Largest Available Free space.
And that should be it.

But I want for example give 60G to the windows partition, 50 to Linux, and another partition (±190GB) with the documents to share it between windows and Linux (/home)
Is it possible?

---

### Post by darkod on 2010-02-19
> **Nifio said:**
> But I want for example give 60G to the windows partition, 50 to Linux, and another partition (±190GB) with the documents to share it between windows and Linux (/home)
Is it possible?

At the moment it seems:
/dev/sda2 is ntfs approx 5GB
/dev/sda3 is ntfs approx 102.6GB

I guess /dev/sda2 is a recovery partition and /dev/sda3 is your windows system partition. Have in mind that you can create only one more partition because the limit is 4. So it would have to be an extended partition with all the other partitions as logical inside it.

You can have one ntfs partition to serve as data partition that both windows and ubuntu will read, but that can't be your /home partition because /home needs to have linux filesystem as far as I know and windows can't read that.

The first task is to shrink the windows system partition to 60GB if that's what you want. So just boot windows and open Disk Management, and resize the partition to 60GB. Reboot vista few times after that.

Then start the ubuntu install process and select manual partitioning and create as LOGICAL partitions:

- 190GB ntfs partition

- approx 50-swap GB ext4 partition, mount point /
- swap partition with size 2GB or 150% of your ram size if you plan to hibernate regularly

In the above calculation, sit down and calculate how big swap you plan to create, so you know how big / partition to create.

Another alternative for the ubuntu partitions is:

- 20GB ext4 partition, mount point /
- approx 30-swap GB ext4 partition, mount point /home
- swap

That should be it. It all depends how you want to organize your hdd layout and your system.

---

### Post by Nifio on 2010-02-19
> **darkod said:**
> At the moment it seems:
/dev/sda2 is ntfs approx 5GB
/dev/sda3 is ntfs approx 102.6GB

I guess /dev/sda2 is a recovery partition and /dev/sda3 is your windows system partition. Have in mind that you can create only one more partition because the limit is 4. So it would have to be an extended partition with all the other partitions as logical inside it.

You can have one ntfs partition to serve as data partition that both windows and ubuntu will read, but that can't be your /home partition because /home needs to have linux filesystem as far as I know and windows can't read that.

The first task is to shrink the windows system partition to 60GB if that's what you want. So just boot windows and open Disk Management, and resize the partition to 60GB. Reboot vista few times after that.

Then start the ubuntu install process and select manual partitioning and create as LOGICAL partitions:

- 190GB ntfs partition

- approx 50-swap GB ext4 partition, mount point /
- swap partition with size 2GB or 150% of your ram size if you plan to hibernate regularly

In the above calculation, sit down and calculate how big swap you plan to create, so you know how big / partition to create.

Another alternative for the ubuntu partitions is:

- 20GB ext4 partition, mount point /
- approx 30-swap GB ext4 partition, mount point /home
- swap

That should be it. It all depends how you want to organize your hdd layout and your system.

In fact, I have already schrinked the windows partition, but I couldn't schrink it more than 82,84GO.

---

### Post by darkod on 2010-02-19
> **Nifio said:**
> In fact, I have already schrinked the windows partition, but I couldn't schrink it more than 82,84GO.

As I said, it all depends how you want to organize it. :)

---

### Post by Nifio on 2010-02-19
> **darkod said:**
> As I said, it all depends how you want to organize it. :)

Yes but I can't resize the windows partition to less than 205 GO.

---

### Post by darkod on 2010-02-19
Windows is known to write files all over the partition. And even though vista has a resize tool, in fact it only offers to shrink until it hits data. That's why it can offer to shrink much less than you have unused.
You should defragment the vista partition few times and also temporary turn off System Restore in vista. I think it helps shrink it further.

Another alternative is to use Gparted from the live desktop because Gparted can actually move the data, but sometimes it can corrupt a vista or 7 system partition. In fact, windows might complain after being resized by Gparted. So try to avoid that for now, but if nothing else works to shrink as much as you want, Gparted is an option.

---

### Post by Mark Phelps on 2010-02-19
You would do better not trying to share /home between MS Windows and Ubuntu.

If you want to share data, best to create a separate data partition, format it as NTFS (since MS Windows and Ubuntu can both use that), and put only data files into it.

---

### Post by Nifio on 2010-02-20
Thanks

---

### Post by kaldor on 2010-02-27
I have this problem on my father's computer as well. I cannot resize Windows using Gparted or the installer. Free space is "unknown" and I cannot do anything except erase the entire HD.

---

### Post by Mark Phelps on 2010-02-28
> **kaldor said:**
> I have this problem on my father's computer as well. I cannot resize Windows using Gparted or the installer. Free space is "unknown" and I cannot do anything except erase the entire HD.

The link below provides some suggestions on actions you can take to get more shrinkage out of the Vista/Win7 Disk Management utility:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Since this is not YOUR computer, unless you want to render the Vista/Win7 OS completely unbootable, strongly suggest you do NOT again try using GParted or the Ubuntu installer to shrink the OS.

---

