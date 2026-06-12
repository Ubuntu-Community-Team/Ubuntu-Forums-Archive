---
title: "'Resize operation failure' when trying to install alongside Windows"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by armendvisoka on 2011-05-14
Hi,

Whenever I try to install Ubuntu 11.04 I get a 'Resize operation failure' error, I've taken a screenshot of it:

[http://imageshack.us/photo/my-images/860/screenshotyj.png/](http://imageshack.us/photo/my-images/860/screenshotyj.png/)

My Specs should be fine with Ubuntu 2GB RAM, 2.2Ghz AMD Athlon 64 and a GeForce 7600 GS 256MB.

Thanks!

---

### Post by Rubi1200 on 2011-05-14
Hi and welcome to the forums :-)

Did you defragment the Windows drive before starting?

Please post the output of the following command from the LiveCD so we can see the partition setup:

```
sudo parted -l
```

(lowercase L not 1)

Thanks.

---

### Post by Lateralis on 2011-05-14
I personally strongly recommend you resizing your Windows partition from within Windows.  In the first instance NTFS support in Linux is not 100% perfect (although it is very good) so you might suffer data loss.  Secondly, Windows gets pretty pernickity if its system partition is fondled by anything other than itself.  So, I would resize your Windows partition using the Windows tools to create the space you need for Ubuntu. Then during the install, select the free space you created as the target partition for your Ubuntu installation.

---

### Post by armendvisoka on 2011-05-14
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Did you defragment the Windows drive before starting?

Please post the output of the following command from the LiveCD so we can see the partition setup:

```
sudo parted -l
```(lowercase L not 1)

Thanks.

No, I haven't defragmented Windows before installing, should I do that now?

Here's the output form the commands:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD160JJ/ (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  153GB  153GB   primary  ntfs         boot
 2      153GB   160GB  6728MB  primary  fat32        lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by Rubi1200 on 2011-05-14
I also suggest you follow the sensible advice posted by Lateralis and will add some more information.

1. backup all important data first

2. if you don't have one, create a Windows recovery disk
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

3. defragment before starting and once you have created the partitions inside Windows, run chkdsk a couple of times and reboot into Windows to make sure all is good
[http://www.sevenforums.com/tutorials/433-disk-check.html](http://www.sevenforums.com/tutorials/433-disk-check.html)

Once all this is done you can install using the method described by Lateralis, which means choosing the option for manual partitioning.

---

### Post by armendvisoka on 2011-05-14
> **Rubi1200 said:**
> I also suggest you follow the sensible advice posted by Lateralis and will add some more information.

1. backup all important data first

2. if you don't have one, create a Windows recovery disk
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

3. defragment before starting and once you have created the partitions inside Windows, run chkdsk a couple of times and reboot into Windows to make sure all is good
[http://www.sevenforums.com/tutorials/433-disk-check.html](http://www.sevenforums.com/tutorials/433-disk-check.html)

Once all this is done you can install using the method described by Lateralis, which means choosing the option for manual partitioning.

I'm running Windows XP, not 7, I can't find any of the stuff the guide is saying to.

---

### Post by Lateralis on 2011-05-14
To resize your partition, click the start menu and then hit Run.  In the dialogue box, type 

```

diskmgmt.msc

```

This will bring up the HD management program.  From there you can resize your XP partition.  For more information see [this]("http://support.microsoft.com/kb/309000") MS documentation page.

For Chkdsk see [this]("http://support.microsoft.com/kb/315265") MS page.

I unfortunately don't know how to create a recovery disc in XP.  In truth, you shouldn't encounter any problems.  At least, I've never had any troubles resizing Windows partitions from within Windows.  But follow Rubi's advice: defrag your computer followed by backing up all of your important data and files to an external medium, e.g. CDs, DVDs or an external hard drive.  It sounds like a lot of effort, but you don't want to be the 1 in a some-largeish-number who encounters a problem and ends up losing everything.  The number of threads on these forums with people saying "I didn't back up and I've lost everything!  Help me please I have lots of important information that I can't afford to lose" is staggeringly large.  

Anyway, once you've done that, you should be 100% safe to resize your partition!

---

### Post by Rubi1200 on 2011-05-14
Okay, thanks for letting us know this important piece of information.

I still suggest you backup data and defragment Windows before starting.

Then use the LiveCD and open GParted to resize the partition, leaving it as unallocated space. 

Once you have done this, reboot and go into Windows again and run chkdsk on XP:
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

If everything is okay and you can boot Windows normally, then start the Ubuntu CD and try installing again.

---

### Post by armendvisoka on 2011-05-14
Okay, so I should defragment first, back up everything etc. Then resize partition in Windows, run chkdsk and finally install Ubuntu?

---

### Post by Lateralis on 2011-05-14
That sounds good to me! 

If you hit a stumbling block or want to know more then don't hesitate to ask. :)

---

### Post by armendvisoka on 2011-05-14
> **Lateralis said:**
> That sounds good to me! 

If you hit a stumbling block or want to know more then don't hesitate to ask. :)

I'm trying to use the Disk Management tool to partition, but wherever I right click, there's no 'make new partition' option or anything like that. I can't see any 'unallocated space' area either.

---

### Post by Lateralis on 2011-05-14
Hmmm, that's curious.  Have you been able to shrink your windows partition?  If yes, then that's fine.  You will need to make (at least) two partitions for Ubuntu: 1 for the '/' ("root") partition and one of a "swap" partition.  Neither partition can be formatted in Windows, as Windows does not support the necessary filesystems.  

If you're really stuck, could you post a screenshot of the disk management tool so we can see what you're seeing?

---

### Post by Rubi1200 on 2011-05-14
There is no option on Windows XP to resize partitions only add logical and extended ones (from what I recall).

You need to use GParted on the LiveCD to resize the Windows partition and create space to install Ubuntu.

---

### Post by Lateralis on 2011-05-14
Oh yes... I just rebooted into and out of XP and you are entirely correct.  I thought I had resized partitions in XP before but I guess not.  All you can do is delete and make new partitions. =(

So I stand entirely corrected and apologise armendvisoka.  You will need to do as Rubi says and boot into the LiveCD to resize the partitions.  But I still implore you to back everything up before you start partitioning up your hard drive.  Nothing should go wrong, but you want to be prepared on the off chance that it does.

---

### Post by armendvisoka on 2011-05-14
Ah okay, I see. No worries, Lateralias :) Thanks for the help both of you, I'll make sure to do that!

---

