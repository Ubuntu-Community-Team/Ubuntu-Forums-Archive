---
title: "New Install Questions HP Mini 210"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by gurgsnekr on 2010-12-23
Greetings,

I have a question before I try to install Ubuntu.  I have a new HP Mini 210 with Windows 7 Premium with 250 GB hdd and 2 GB Ram.

I know that I can have a dual boot with Windows 7 and Ubuntu, but I am not sure how to set up the partitions.  I read a previous post by someone with an HP Mini 210 and they appeared to have difficulty with setting that up.  My computer has the hdd partitioned out with the system on one side and the recovery on the other.  I need to keep Windows for other projects, so keeping the recovery partition is necessary.  What should I keep in mind when setting the partitions for a dual boot?

I am new to Ubuntu, and when I tried the live USB on my desktop I really liked what I saw with.  I thought it would be easy to set upon my mini, but when I ran the live USB, I could not get the wireless card to work, Broadcom drivers.  I read about a fix where I have to have the system physically connected while I do the install.

Right now, I'm just scared that I am going to mess something up and brick my netbook.  

Thanks for the help.

gurgsnekr
Pacific Time

---

### Post by ottosykora on 2010-12-23
in all such cases I generaly buy new harddrive, copy the contents of the old one to it and then start play...

But, it depends on which kind of partitions the w7 system is on. OK, the w7 will be on primary partition NTFS, no problem, the recovery might be dynamic partiton, this should be changed to basic partition first. This should be possible from the windows.
(in partition managers such dynamic is often shown in yellow color)

Then you can start partitioning with the life cd (gparted on it), shrink existing partitions, in the free space produce extended partition and in it then one home and one root partition, swap possible too.

On my HP mini, I have even separate partition for the grub files only, this makes the thigs sometimes more simple.

---

### Post by luskwater on 2010-12-23
I recorded my experience with our HP Mini 210 in [a blog posting]("http://luskwater.blogspot.com/2010/09/make-way-for-linux.html"), in the hope that others could benefit.  In brief, I found that all four primary partitions were taken up by the initial Win7 installation.  I backed up each partition, resized the Windows partition, and replaced the last partition with an extended partition.  (I then restored that data into a partition in the extended partition.)  The other Linux partitions went inside the extended partition.

All still appears to work, for what it's worth.

---

### Post by gurgsnekr on 2010-12-23
@ottosykora, Thanks!  Looks like I should do a little more research on the partitions and get a little more information on what I need to do.  

@luskwater, Thanks for the blog post, although some of it seems greek to me lol.  I'll figure it out, with the help from your guide.

Can I save the restore image, reformat the hdd as one?  If so, would it then be possible to restore Windows without installing the same partitions I already have?  Sorry for the questions, This is new, and I'm trying to get it straight in my head.

---

### Post by ottosykora on 2010-12-23
so I see I was kind of lucky , I had the mini still with XP and there HP did not have such absurd ideas. I mean if they partition the disk this way, it sounds like the guy making the majjor image had no idea what he was doing. I mean taking 4 prim for just the OS and still no data or what ever parttition around, this is simply gr#@$+...grrr

---

### Post by gurgsnekr on 2010-12-24
@ottosykora
I think I understand why the partitions are set up like they are.  Since these things do not have internal optical drives it is a cheap alternative to sending out disks or USB drives for when something happens.  Although I agree with you, it does seem to be more complicated than it needs to be.  

@luskwater
I have not done much with changing partitions around.  At most I've used Partition Magic to create a partition to break up a drive on another system.  I did get an idea from this.  Create the recovery disk, then format the hdd as one.  Then repartition the drive with the two sides and install Windows on side A and Ubuntu on side B (or vice versa).

Thanks again!

---

### Post by ottosykora on 2010-12-25
Yes, it is OK to have all parts needed in partitions on the disk, but to produce 4 primary and put the things into it is simply not proffesional.
One needs a primary for the system, but the rest should be done from begining in extended/logical drives. This was done so under DOS in 1990 already so. 
So I mean what you had to do yourself, the guys at HP are supposed to know and do.

---

