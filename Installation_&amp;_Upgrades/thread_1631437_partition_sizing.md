---
title: "partition sizing"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by wgarider on 2010-11-26
I have the opportunity to install Ubuntu on a new laptop and want to create a separate partition for /home. 

I've never manually partitioned a drive and am not sure about what to do. I've looked at some of the 'how to' guides but haven't found anything that details the different sizes.

I know I need / and swap, (and /home).....what else should I do?
Thanks

---

### Post by apollothethird on 2010-11-26
> **wgarider said:**
> I have the opportunity to install Ubuntu on a new laptop and want to create a separate partition for /home. 

I've never manually partitioned a drive and am not sure about what to do. I've looked at some of the 'how to' guides but haven't found anything that details the different sizes.

I know I need / and swap, (and /home).....what else should I do?
Thanks

That's correct, for what you would need.  Boot to the Ubuntu Live CD and run "Try Ubuntu".  Go into Gparted from System -> Administration.  The GUI application usage is seamless.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by skillet-thief on 2010-11-26
As for the sizing, I suppose it depends on the size of your hard drive and what you plan to do with your system.

My personal experience is that I used to overestimate the capacity needed for all the system stuff. The system really only needs a few gigs (unless you have special needs). With a 300GB drive, I would use 270GB for /home, and most of the time 30GB for the system is total overkill.

But your needs and situation may vary.

---

### Post by wgarider on 2010-11-26
> **apollothethird said:**
> That's correct, for what you would need.  Boot to the Ubuntu Live CD and run "Try Ubuntu".  Go into Gparted from System -> Administration.  The GUI application usage is seamless.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Thanks!

---

### Post by wgarider on 2010-11-26
> **skillet-thief said:**
> As for the sizing, I suppose it depends on the size of your hard drive and what you plan to do with your system.

My personal experience is that I used to overestimate the capacity needed for all the system stuff. The system really only needs a few gigs (unless you have special needs). With a 300GB drive, I would use 270GB for /home, and most of the time 30GB for the system is total overkill.

But your needs and situation may vary.


This helps - thank you.

---

### Post by karthick87 on 2010-11-26
Use Gparted partition manager,
```

sudo apt-get install gparted
```

---

### Post by apollothethird on 2010-11-26
> **wgarider said:**
> This helps - thank you. Any thoughts about specifying /boot or is that created under / ?

After you have set the size you want (by the way, Gparted is very easy to use and fast, which I'm sure you may have already noticed) just mount it from the Places menu in the Try Ubuntu session.  Use:

You can find the UUID of the drive by typing "mount" from a terminal window.

Install boot for that partition with:

```
grub-install --root-directory=/media/[UUID} /dev/sd[X]
```

Replace [UUID} for the ID you see with the mount command.

Replace the [X] with the leter you see after sd from the mount command.  Use the letter only, not the number after the letter.  The letter will be a lowercase a, b, c, etc.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by wgarider on 2010-11-26
> **apollothethird said:**
> After you have set the size you want (by the way, Gparted is very easy to use and fast, which I'm sure you may have already noticed) just mount it from the Places menu in the Try Ubuntu session.  Use:

You can find the UUID of the drive by typing "mount" from a terminal window.

Install boot for that partition with:

```
grub-install --root-directory=/media/[UUID} /dev/sd[X]
```

Replace [UUID} for the ID you see with the mount command.

Replace the [X] with the leter you see after sd from the mount command.  Use the letter only, not the number after the letter.  The letter will be a lowercase a, b, c, etc.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

OK - you convinced me to try this in a VM, to get a feel for the process....many thanks for the help!

---

### Post by wgarider on 2010-11-27
So i installed Xubuntu on a VM.....got to the partitioning part of the install process and only specified a / , /home and swap.

I completed the install and compared the file system to my current system, which was done with the automated partitioning..... I see /home mounted as /dev/sda5, and / on /dev/sda1..... I also specified swap..... Is the process really this easy????

I was expecting to have to do some shenanigans after the install and am not sure if it worked like I wanted it to. Seems as though it worked? How can I check to be sure?

---

### Post by apollothethird on 2010-11-27
> **wgarider said:**
> So i installed Xubuntu on a VM.....got to the partitioning part of the install process and only specified a / , /home and swap.

I completed the install and compared the file system to my current system, which was done with the automated partitioning..... I see /home mounted as /dev/sda5, and / on /dev/sda1..... I also specified swap..... Is the process really this easy????

I was expecting to have to do some shenanigans after the install and am not sure if it worked like I wanted it to. Seems as though it worked? How can I check to be sure?

If you can see all your partitions and you're able to test and use your chosen partitions the way you want, i would assume that it's working.

I did lot of experimenting on a freshly formatted hard drive to check the workings of Gparted also, before committing it to my main drive.  All the tests worked perfectly.  I had three partitions. Ubuntu was in the middle, partition #2.  Swap was partition 1.  Windows was on the end, partition 3.  The install of Windows and Linux went smooth.  However Microsoft made the Windows root directory in drive "E" because it was on the third partition.  So I moved my middle Linux partition to the last #3 since it'll work the same no matter which partition.

I did this by deleting partition #3 (the windows partition).  Then I resized the Linux to extend to the end of the drive.  Then I resized it again to provide space in the middle.  Then I deleted the swap partition and made two new partitions in the front, #1 for Windows and #2 for swap.

Now the new install of Windows sees Windows as drive #C.  The integrity of the Ubuntu install remained totally intact during the reorganizing.  The whole operation was very seamless... easier done than said.

Hope this makes it clear that you're not locked into any of your choices.

By the way, if Windows hadn't been a fresh install and I saw a need to preserve the content I would have used Clonezilla to relocate the data, which also works very well.  I just wish Clonezilla was part of the "Try Ubuntu" suite.  But it doesn't hurt having two utility disk within easy reach.

Again, the resizing and reordering of your partitions with Gparted is so easy I can understand that you might feel you're missing something when you're looking for a tedious job.  But it's just that easy.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by wgarider on 2010-11-27
> **apollothethird said:**
> 
The whole operation was very seamless... easier done than said.

Again, the resizing and reordering of your partitions with Gparted is so easy I can understand that you might feel you're missing something when you're looking for a tedious job.  But it's just that easy.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

That sums it up well - it seemed so easy, I thought I'd missed or messed up something.
Thanks again for the help!

---

### Post by 12apennachi on 2010-11-27
Speaking of gparted. I recently installed another bootloader on a flash drive, I forgot the name. Anyways, it somehow destroyed my partitions on my hd and I spent 6 hours trying to fix it, unable to use my OSs on my hard drive I had to do it from usb. Anyways, I ended up using testdisk and it worked great, everything was back to normal, but when I go to gparted it says it is all unallocated. Disk utility gives me the proper partitions though. Should I try to do something about this? or should I just leave it and not worry about it?

---

