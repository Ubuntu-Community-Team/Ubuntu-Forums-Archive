---
title: "GParted Question?"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-05-21
I just added a second 80 GB IDE HDD to an old PC running XP Pro and KK.

This 80 GB drive has Jaunty on in, runs fine and the old PC recognized it straight away. 

My question is Gparted shows it having a main partition of ~76 GB and I would like to partition it in half into two 38 GB partitons for storage or maybe install another Linux distro on it. I know how to read what GParted shows but I have never modified any partitons with GParted as yet. I re-sized the 76 GB partition into two 38 GB partitions but haven't gone through with finalizing this action yet for fear of messing things up. Do you just go ahead and finalize and will it auto split the drive into two partitions when done? Will it then show a newly created partition, with the other partition being the boot partition, with JJ on it?

It looks simple enough, I just don't want to mess things up.

---

### Post by darkod on 2010-05-21
If you plan to use JJ also, don't resize that way. Yes, Gparted can resize it, but with linux it's better to resize the file system first too.

And new partition will not be created automatically. Gparted will resize it to the size you select. Creating new partition in the unallocated space is your job after that. :)

But I think just resizing the JJ root like that can corrupt it. I can't give you the commands how to do it properly, but I've read it can get corrupted.

It has something to do with turning off the journal first, then resizing, and turning on the journal, etc.

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by cybrsaylr on 2010-05-21
> **darkod said:**
> But I think just resizing the JJ root like that can corrupt it. I can't give you the commands how to do it properly, but I've read it can get corrupted.

It has something to do with turning off the journal first, then resizing, and turning on the journal, etc.

That was my worry.
With Windows you have to defrag it first to avoid corruption but you don't defrag Linux. 

JJ still runs fine on that drive, it even wanted to do ~300 MBs of updates a minute after booting JJ up. JJ hasn't been run on that drive in almost a year. Not sure if I will keep JJ on it but was just curious as to what would happen if I split the drive in half like that with GParted.

---

### Post by Herman on 2010-05-23
> That was my worry.
With Windows you have to defrag it first  to avoid corruption but you don't defrag  Linux. :) We don't really need to defrag Windows first before resizing it. 
It probably doesn't do very much harm to defrag Windows before resizing it, apart from being a waste of time and wearing out your hard drive. 
Most people do recommend defragging Windows before resizing, but is this just a popular myth, repeated by so many web forum 'parrots' that it is now considered to be a fact? 

Actually, the information we're given from those who should know, all refutes the idea of defragging Windows before resizing with GParted.
There are at least three locations in official documentation where it is clearly stated that defragging is not necessary before resizing Windows using GParted. 

1. According to the Parted Users Manual, you don't need to, [2.4.13  resize]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25") - Parted Manual> Note that Parted does not require a file system to be "defragged" (Parted can safely move data around if necessary).  It's a waste of time defragging.  Don't bother!   2. The ntfsresize documentation says defragging doesn't matter, [How  to resize NTFS without data loss?]("http://darkstar.ucd.ie/timosh/links/ntfsresize.html#example"). > Choosing a distribution  including **ntfsresize version**  **1.9.0 or later** is recommended, at least until NTFS gets resized, because it can  also resize [fragmented  NTFS]("http://darkstar.ucd.ie/timosh/links/ntfsresize.html#fragmented") safely, there isn't even need for    defragmentation in advance. 3. According to the Linux manual page for ntfsresize it's not necessary, 
```
man ntfsresize
```> NTFSRESIZE(8                                                                                                                                                                               NTFSRESIZE(8

NAME
       ntfsresize - resize an NTFS filesystem without data loss

SYNOPSIS
       ntfsresize [OPTIONS] --info DEVICE
       ntfsresize [OPTIONS] [--size SIZE[k|M|G]] DEVICE

DESCRIPTION
       The  ntfsresize program safely resizes Windows XP, Windows Server 2003, Windows 2000, Windows NT4 and Longhorn NTFS filesystems without data loss. All NTFS versions are supported, used by 32-bit
       and 64-bit Windows.  Defragmentation is NOT required prior to resizing because the program can relocate any data if needed, without risking data integrity.
More than that, it doesn't even make sense that defragging would likely do anything to prevent file system corruption during a resize when we think about it a little.
Since the idea of defragging is supposed to be to re-arrange parts of files so they will be grouped together in a more sequential order and not necessarily do anything about fixing file system, I can't see the logic in thinking it will do anything to 'avoid corruption' during a resize operation. [Defragmentation]("http://en.wikipedia.org/wiki/Defragmentation") - wikipedia

Windows CHKDSK, on the other hand, is the program designed to find and correct file system errors in Windows file systems,  [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK") - wikipedia
Running CHKDSK should help to make sure the file system isn't corrupt, prior to attempting a resize operation by GParted, (or any other partition editor).
Most partition editors would take some kind of a look at the file system's metadata before attempting a resize operation and refuse to start the operation if file system corruption is detected.
Running CHKDSK before attempting to resize a Windows partition with GParted avoids that problem.
I would recommend running a file system check before resizing any kind of file system, but I don't think defragging really does anything.  :)

---

### Post by Herman on 2010-05-23
> My question is Gparted shows it having a main partition of ~76 GB and I  would like to partition it in half into two 38 GB partitons for storage  or maybe install another Linux distro on it. I know how to read what  GParted shows but I have never modified any partitions with GParted as  yet. I re-sized the 76 GB partition into two 38 GB partitions but  haven't gone through with finalizing this action yet for fear of messing  things up. Do you just go ahead and finalize and will it auto split the  drive into two partitions when done? Will it then show a newly created  partition, with the other partition being the boot partition, with JJ on  it? :) I agree with darkod for that part where you'll need to 'And new partition will not be created automatically. Gparted will resize  it to the size you select. Creating new partition in the unallocated  space is your job after that.', but it's a long time since I have heard of resizing the file system manually as a separate operation.
Before GParted or even Parted came along, Linux users needed to do that, or so I have read. 
I'm not sure how old that given link would be, [http://www.howtoforge.com/linux_resi...xt3_partitions]("http://www.howtoforge.com/linux_resizing_ext3_partitions"), but it was last edited back in the end of December 2006, and while there's nothing at all wrong with doing things in the traditional manner, you would probably find that GParted runs the same or similar commands for you and saves you a lot of work.
I have been using GParted since its alpha days and I have never needed to  go to the trouble of resizing a file system separately from the partition yet. To the contrary, I have used GParted run resize2fs for me after using a dd command to restore a smaller file system to a larger partition sometimes.
 > Not sure if I will keep JJ on it but was just curious as to what would  happen if I split the drive in half like that with GParted.     Probably nothing would go wrong in a million times, GParted would just do the work for you. There's always the chance a hardware glitch of some kind could upset things, so you are always recommended to make a backup of your files before working on a hard disk no matter what partition editor you use. :)

---

### Post by wilee-nilee on 2010-05-23
I can understand the argument not to defrag, but if the files are spread out on the partition does a optimizer help free up space. It seems with W7 that this can make a difference when using the virtual disk manager in W7, to shrink a partition. You would know that's why I ask.

---

### Post by cybrsaylr on 2010-05-23
Update:

I now have a triple boot system of Lucid, XP Pro and Karmic.

Ending up dumping JJ.
Then Used the LL Live-CD to split that 80GB second drive in half and formated both partitions into Ext4.

Then installed LL onto the first partition on the slave drive.
This did not go smooth. Kept getting I-O errors saying the Live-CD may have errors, the CD ROM may be dirty, the HDD may be old or running too hot or have bad sectors, etc.

Checked them errors out, then pushed it on through till after the 5th try LL fully installed and appears to be running very well. This took a couple hours but this is an old Pent 2 that LL 32 bit was being installed on. After the install, update manager popped up with 79 updates than went in without any issues. 

Had a bit of a scare on first restart after the install. PC wouldn't restart! Got an Error 15 from GRUB. Then I realized I had to change settings and reboot off the Primary drive instead of the slave drive. After changing back to boot up off the primary drive it worked like a charm. GRUB shows 3 OSs, LL, XP PRO and KK in that order now. Tried it out and all 3 OSs boot up as they should when selected.

First time ever attempting something like this and am very pleased how well it worked out. LL seems to run a bit slow but decent on this old Pent 2 PC.
I was curious how LL would run on a PC this old that's why I gave it a whirl.

Ended up creating the 2 partitions desired with Live-CD and never had to use GParted.



PS: Have my first bug to report on Lucid. Just came back after shutting down the PC for the first time. What happens is Lucid shuts down but the power remains on the PC. I have to hit the power button to kill power to the PC. What is needed to fully shutdown everything like my other PCs do?

---

### Post by dino99 on 2010-05-23
****  What is needed to fully shutdown everything like my other PCs do?  ***

this forum is fullfilled with shutdown issues: this has come up with grub2+udev+ext4, hope this will be fix on coming month/year :(

---

### Post by Herman on 2010-05-23
> I can understand the argument not to defrag, but if the files are spread  out on the partition does a optimizer help free up space. It seems with  W7 that this can make a difference when using the virtual disk manager  in W7, to shrink a partition. You would know that's why I ask.     :)  To answer your question, 'I don't know', (right now), but I intend to  find out more about this.
Interestingly, the official technical pages I looked at didn't mention anything about the need to defrag before using Microsoft's Disk Manager.

I looked at 
[Can I Repartition my Hard Disk?]("http://windows.microsoft.com/en-us/windows-vista/Can-I-repartition-my-hard-disk") - Windows.Microsoft.com
[Shrink a Basic Volume]("http://technet.microsoft.com/en-us/library/cc731894.aspx") - TechNet
and one which might not be an official Microsoft website, [How to Shrink a Volume in Windows 7 ]("http://windows7news.com/2009/10/23/how-to-shrink-a-volume-in-windows-7/")- Windows 7 News and Tips.

When I was experimenting with Windows 7 a while back and I tried out the Disk Management utility and it worked very well for me. I didn't have any Windows installation that had been used very much though or had files in it. I imagine that might make a difference! 
It might be interesting to try some experiments and install Windows 7, fill it up with files and then delete some of the first files and try resizing it with its own Disk Management utility without defragging first to see if the Disk Manager really is incapable of moving normal files or not. I would imagine it will move them without any problems.
The place where I think the Disk Manager gets stuck is at the probably at the page file, and there's some interesting info in that first link about that.

It's not that I'm *against *defragging. I don't think it hurts to run a defrag in Windows, I'm just trying to stimulate some logical thought and discussion behind what we tell people in web forums and promote the idea of running a file system check instead of or as well as defragging.  :)

---

### Post by wilee-nilee on 2010-05-23
> **Herman said:**
> :)  To answer your question, 'I don't know', (right now), but I intend to  find out more about this.
Interestingly, the official technical pages I looked at didn't mention anything about the need to defrag before using Microsoft's Disk Manager.

I looked at 
[Can I Repartition my Hard Disk?]("http://windows.microsoft.com/en-us/windows-vista/Can-I-repartition-my-hard-disk") - Windows.Microsoft.com
[Shrink a Basic Volume]("http://technet.microsoft.com/en-us/library/cc731894.aspx") - TechNet
and one which might not be an official Microsoft website, [How to Shrink a Volume in Windows 7 ]("http://windows7news.com/2009/10/23/how-to-shrink-a-volume-in-windows-7/")- Windows 7 News and Tips.

When I was experimenting with Windows 7 a while back and I tried out the Disk Management utility and it worked very well for me. I didn't have any Windows installation that had been used very much though or had files in it. I imagine that might make a difference! 
It might be interesting to try some experiments and install Windows 7, fill it up with files and then delete some of the first files and try resizing it with its own Disk Management utility without defragging first to see if the Disk Manager really is incapable of moving normal files or not. I would imagine it will move them without any problems.
The place where I think the Disk Manager gets stuck is at the probably at the page file, and there's some interesting info in that first link about that.

It's not that I'm *against *defragging. I don't think it hurts to run a defrag in Windows, I'm just trying to stimulate some logical thought and discussion behind what we tell people in web forums and promote the idea of running a file system check instead of or as well as defragging.  :)

I will have to look at the links, I have generally advised people to defrag with a optimizer like auslogics to move what isn't locked down to the front of the partition. Usually it is with people who are kind of new with dual booting or partitioning, sort of a pseudo insurance policy. 

I have W7 though I hardly use it, but I like the idea of a virtual partitioner, as long as it works correctly as you suggest under all conditions. 

Many MS users may not know how to get to the command line to run a chkdsk in case something is amiss, especially with computers having recovery partitions so they don't have a install disc, but the neosmart recovery discs work well as long as they're bootrec.exe files aren't borked.  Your correct though with defragging wears on the HD.

---

### Post by cybrsaylr on 2010-05-23
I've always heard defragging wears down your HDD. However both Vista and W7 by default, schedule a once a week defrag if you leave your PC on 24/7. 

That said since I use Ubuntu 99% of the time now the Windows side seldom is used or defragged. When I got my new PC it had a 1 TB drive. I basically split it in half with KK for a dual boot within hours of booting it up to avoid Windows files being scattered all over the new 1 TB drive. Even so I still defragged it first and this did push some W7 files more to the front of the drive, with Ubuntu being installed on the back of the drive. 

On my older PCs defragging before installing a dual boot setup always helped push files toward the front so as not to mess up Windows when installing Ubuntu. Doing this I have never had a dual boot problem and all has run well with both OSs.

---

### Post by Herman on 2010-05-23
> Many MS users may not know how to get to the command line to run a  chkdsk in case something is amiss, especially with computers having  recovery partitions so they don't have a install disc, but the neosmart  recovery discs work well as long as they're bootrec.exe files aren't  borked. :) Yes, exactly! And that's a good reason to encourage them to try to run CHKDSK *before* they start operations to their partitions and file systems.
If they can run CHKDSK beforehand, it will may actually do something to prevent problems such as the file system not being read properly at installation time which could be leading to a lot of the problems people are reporting here in the forums, such as their operating systems not being detected and added automatically to the boot manager. I'm not sure of it will prevent all of those problems but it seems sensible to me to guess that it might prevent a good percentage of those kinds of problems.
Not only that, but if they know how to run CHKDSK /R and have had a practice run at it beforehand, (like a fire drill), then people will know how to run it again in case it's really needed after the resize operation, (regardless of what partition editor is used).

It's easy for Windows users to schedule a thorough file system check at the next reboot by going 'My Computer', and right-clicking on the 'C:' drive and looking in the tools tab and clicking 'Check now, and make sure both checkboxes are activated. Of course Windows can't really run a file system check on itself while it's running, but it will pretent it's trying to, (sense of humor by Windows programmers?), and offer to do it at next boot-up. Then they should reboot and allow the process to complete before they begin any partition resizing operations.

Really people should be making some effort to get themselves a disk that  contains the tools for maintaining the operating system they're using. I'm sure everyone can get a Windows CD of some kind if they try hard enough. 
It would be a lot better to encourage people to learn to run CHKDSK /R from a CD, because then it things go badly wrong for some reason during the resize operation, they will already have proved they know how to recover. I have fixed broken Windows operating systems many times just by running CHKDSK /R, it's a great program and we'd really be doing Windows users a big favor by encouraging them to learn to run their file system checker. The main thing is though, it would mean, (I hope), fewer problems and complaints with installing Ubuntu in a dual boot configuration.  :)

---

### Post by wilee-nilee on 2010-05-23
It makes sense in what your considering as a more inclusive use of the built in tools like chkdsk /r and  other variations. I am just a enthusiast, but I have to much free time and I like to learn so I watch those that know, to pickup tips and links that will be useful to myself and others. Your site is certainly one of them.

I had never touched a computer until about 2 & 1/2 years ago, but I was lucky to be directed to a local computer recycler that used Open Source OS to reload the computers. So when I finally got around to MS Windows it was like this is easy since I have some very basic knowledge, from using open source. I already knew form trying out multiple open source OS that all OS have some similarities, but you have to find the specifics that work for some more then others. I learned a lot from using a bunch of different Puppy Linux, and puplets.

In the end I know very little compared to a open source IT tech, but all I can do is try to move forward and not leave a wake of destruction of others OS.

The other problem that seems to be seen on the forums is where to put grub, and the gui that says if your not sure put it everywhere or in a partition, this is confusing to somebody who doesn't understand how the MBR works. People just pop that Ubuntu disc in expecting it to install perfectly which it will but you have to know what to look for since you have much more control then a MS install. You can do custom install with MS but I suspect most don't use this if they are just running MS. 

There probably should be some sort of system that detects where your installing to better, and pointing grub to the right place, and a help window that gives somewhat of a explanation, for us noobs.

---

