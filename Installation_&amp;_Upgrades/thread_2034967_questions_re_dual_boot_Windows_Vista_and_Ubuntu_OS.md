---
title: "questions re dual boot Windows Vista and Ubuntu OS"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by Eagle Nest on 2012-07-29
Hi friends. I currently have a dual boot set-up with Windows Vista Business and Ubuntu 10.04. The Windows Vista OS is now crashing pretty well every time I use it. 

I still need some recent version of a Windows OS along with an Ubuntu Linux OS, so I have decided to re-install the Windows Vista using 2 Recovery DVD disks that I created back in 2009 when I got the (Toshiba Satellite Pro) laptop. It's a good notebook (intel duo @ 2 GHz, 2 Gig RAM, 32-bit OS) for my home and work needs. I can't dispose of the Windows OS due to work. The partitions are not the best sizes as Windows takes far too much of the hard drive. 

So here's where it seems complicated and confusing to me. 

I've backed up all data on both systems, so that's done. Seems to me that I have to re-install Windows first. When I do that, I've been led to believe that the laptop will stop recognising the Linux OS. So I will have to go through the dual-boot set up again when I install the Ubuntu OS. 

Have I got that right? And which version of Ubuntu would be appropriate for now?

---

### Post by darkod on 2012-07-29
Installing windows will delete the grub2 bootloader from the MBR and the windows bootloader it will install can't boot linux. So in any case, ubuntu will not appear as a boot option after the vista installation.

But what happens next also depends on how the vista recovery DVDs work. In many cases, the recovery DVDs (or partitions), actually delete the whole disk, and install the factory state system, how you received it from factory. If that happens, that means it will delete the ubuntu partitions with all data, so make sure you have a backup of that too.

Situation 1: If the recovery process only installs vista on the current partition, not touching the ubuntu partitions, you can simply use the 10.04 ubuntu cd in live mode and return grub2 to the MBR with these instructions for example:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Situation 2: If the recovery process does delete the ubuntu partitions and installs vista on the whole disk, first you will need to open in windows Disk Management and shrink the C: partition to the size that you want to keep for windows. Let it finish the shrink process and restart few times in case it wants to do some disk checks. Leave the newly created space as unallocated, DO NOT create any partition in it from windows. Ubuntu doesn't install on ntfs partition and windows can't create linux partitions. Just leave the space as unallocated.
After that is done and vista is booting happily after the shrink, install ubuntu and it will automatically use that unallocated space you left.

As for what ubuntu version to use if you need to reinstall it, it's up to you. You can test the latest 12.04 LTS in live mode first for example, and see how you like it and whether it loads OK on your hardware.

---

### Post by Eagle Nest on 2012-07-29
Outstanding. I will get on it and let you know how it goes. I might have more questions, of course.

---

### Post by Eagle Nest on 2012-07-30
OK, so I've successfully re-installed the Vista OS. I was able to do this without using the 2 Recovery DVD disks. 

It was annoying as heck trying to change the boot sequence to the CD/DVD drive to run the Ubuntu Live CD, but I eventually found that "ESC" followed by "F1" worked at start up. Anyway, enough about Windows. Other than to update the OS at 3 a.m. every few days, I don't really want to think about it. 

 I think what I have is that the Windows OS has, as predicted by darkod, deleted the Ubuntu partition and left a (blank) unallocated block of 7 Gigs or so.

** I just want to be sure that what I have is "situation 2"**, i.e., my Ubuntu Linux OS and data has been deleted.

Computer Management in Windows describes the partitions as follows:

1. Simple/Basic/Healthy (EISA Configuration)w/ 1.46/1.46 GB free;
2. Simple/Basic/Healthy (Primary Partition) w/ 7.87/7.87 GB free;
3. Simple/Basic/C Drive/NTFS/ Healthy (System, etc) 107/133 GB free; and 
4. 7.21 GB unallocated - which I think was my old Ubuntu OS and data.

Gparted in the Live Linux CD mode notes

1. with 0.5/1.46 GB used in Toshiba System Volume
2. with 6.79/7.87 used in HDD Recovery partition
3. with 25.7/132.5 GB on the C drive
4. with 7.21 GB as unallocated as well,

which seems to match what Windows is saying.

So **I think I need to reduce the space for the Windows OS, leaving as much unallocated space as I need for the Ubuntu OS, and then install the Ubuntu** (again). **Some suggestions for the relative size of these partitions would be helpful**. I sometimes get gifted some proprietary music (ITunes), some apps might need to store data, etc. on the Windows side, but I want the lion's share to go to Ubuntu. 

 I can't actually remember what I did last time for the dual boot. **Do I just go through the procedure for installing the Ubuntu OS and the install disk** will do the rest?

How is that all? Sound good?

---

### Post by oldfred on 2012-07-30
You can either move the sda3 recovery partition all the way right to move the unallocated next to the space you will make when you shrink the Windows partition. Or you can make the set of DVDs to restore your system and just delete it. I might also make a full back up of Windows and a Windows repairCD.

NTFS partitions need 30% free to work well. If wanting to share some data between Windows & Ubuntu I might make another NTFS partition (also logical) for shared data. I used that with my XP install so whichever system I was in I had the same Firefox bookmarks & Thunderbird email as I put both profiles in the NTFS partition.

All the new partitions will have to be in one large extended partition as logical partitions. That is why we want the unallocated all together. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:

Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Eagle Nest on 2012-07-31
That's rather a lot of information, Fred. I think I'm going to have to look at a partition tutorial, or something. Thanks anyway.

---

### Post by oldfred on 2012-07-31
Some more info if you like.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Eagle Nest on 2012-07-31
Ok, my next task is to put all the unallocated partitions together. I wasn't able to reduce the Windows partition as much as I would have liked but them's the breaks. 

I will look at the above links and do a search but if anyone can quickly tell me how to put the unallocated partitions together (using Gparted I presume) then that would speed things up for me. How quickly we forget stuff when we don't use it for a while.

---

### Post by Paddy Landau on 2012-07-31
Slightly off-topic, but this may help you next time.

Once you have everything set up as you want it, back up your Windows partition using [CloneZilla]("http://www.clonezilla.org/"). (I used to do this every month with Vista because it was so unreliable.) Then, if Windows starts its problems again, just back up your data; restore the partition; run the Windows updates; restore your data -- and you're done. Saves you hours and hours.

---

### Post by Austin Texas on 2012-07-31
As oldfred said, use gparted to move the sda3 recovery partition all the way right.
Just right click on it and choose move and drag it right

---

### Post by Eagle Nest on 2012-07-31
OK, that's done. Unallocated are all together. I need to look at some of the recommended reading from oldfred.

OK, Paddy, I will have a look at Clonezilla once I've got all this behind me. BTW, my own nephew has disposed of Windows altogether and is running ONLY a recent version of Ubuntu Linux. Then again, the kids are pretty smart these days. :)

---

### Post by techexpert666 on 2012-07-31
This link might be useful:

[www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/]("http://ubuntuforums.org/www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/")

Corrected
[http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/](http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/)

---

### Post by miegiel on 2012-07-31
> **techexpert666 said:**
> This link might be useful:

[www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/]("http://ubuntuforums.org/www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/")

```
**[COLOR="Red"]http://ubuntuforums.org/www.expertslogin.com/[/COLOR]**linux-administration/boot-process-of-linux-in-detail/
```
That's an odd link.

---

### Post by oldfred on 2012-07-31
It is an error. If you remove the ubuntu forums at the beginning it works. It does show the boot process but discusses grub legacy, so a bit dated. BIOS booting has not changed, but now we also have UEFI booting.

---

### Post by miegiel on 2012-08-01
Thx **[COLOR="DarkOrange"]oldfred[/COLOR]** I guess I'm getting parranoid :D I hope some sleep wil fix that.

---

### Post by Paddy Landau on 2012-08-01
EDIT: Sorry, ignore this post. I missed some posts.

---

### Post by techexpert666 on 2012-08-01
Hey sorry for that link. That was by mistake. This is the proper link:

[http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/](http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/)

---

### Post by Eagle Nest on 2012-08-10
Ok the install went well which means my original question is solved. If I have further (related) questions should I postpone marking this thread as solved?

---

### Post by oldfred on 2012-08-10
If new questions are not related to title then best to post as solved and start a new thread with good description of issue in title. Then you get those who may know more about that type of issue responding.

---

### Post by Eagle Nest on 2012-08-17
Thanks oldfred. I was successful with the dual OS install. However, I didn't carry it out quite as I would have liked. In particular, I didn't create a /home directory as you suggested. That's problem number one. 

I'd like to post an image of my hard drive just to get any advice about other improvements. So I think I will leave the thread open for a bit. 

Much thanks, in any case.

---

