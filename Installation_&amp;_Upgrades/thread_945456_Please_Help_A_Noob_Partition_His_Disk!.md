---
title: "Please Help A Noob Partition His Disk!"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by Knowbuddy on 2008-10-12
Hi all,

I am a brand new Ubuntu user, installing Ubuntu along-side Windows (XP Pro) for the first time.  I have been doing a lot of research on how I should be partitioning my HDD, and I have yet to find a "clear" answer on the best/most-used method (probably because I'm sure there's not ONE).  

Anyway, after the research I've done on my own, it looks like to me that the way I have it setup is good, but I've run into one problem.

Okay, I've decided to do it like this:

**HDD = 640GB**
15 GB - Windows Partition
15 GB - Ubuntu Partition (mounted to /)
2 GB - Swap Partition 
2 GB - "Home" Partition (mounted to /home)

So, I like that, and I've read about all the advantages to having a separate /home partition...  The problem is now, what do I do with the 500ish unused GB of space on my HDD?  I've tried to figure out how I can format it with NTFS so that Windows XP and Ubuntu can both use it, but I think that since I have 4 partitions already, I can't create another one?  Right?  Am I understanding that correctly?

So what should I do?  

This is a BRAND new machine, so ZERO data.  I will wipe the whole thing and start over a hundred times if I need to, so if that's what it takes - don't be afraid to suggest it.

THANKS!!!!!!!!!!!!!!!!!

~Buddy

---

### Post by noogs on 2008-10-12
Ok I would lose the home partition it's completely unnecessary while it can be useful it isn't needed. Then I would create a new partition with NTFS with all remaining space for both windows and ubuntu to use. If this is something you don't want to do you may be able to create more than 4 partitions using the ubuntu partitioning tool once ubuntu is installed.

---

### Post by mihaiv on 2008-10-12
You will have to make logical partitions inside an extended partition. You can make as many logical partitions as you like.

---

### Post by Knowbuddy on 2008-10-12
Okay, so now that I have everything installed already, how would I got about making a logical or extended partition?  Is it too late?  Do I need to start over and do it from one of the OS installs?

I could remove the /home partition, but I would like to keep it if at all possible.

---

### Post by SuperSonic4 on 2008-10-12
You can create an extended partition and format it to NTFS. However, I don't know if windows likes them but I know Linux does. Also I'd be a little more generous with space, you have 640GB after all unless you have a lot of data.

Data - NTFS - Primary - 540gb

Windows - NTFS - Primary - 60GB

Ubuntu (/)  - ext3 - Primary - 25GB

Home   (/home) - ext3 - Primary - 10GB

var (/var) - reiserfs - extended - 3gb

Swap - Swap - Extended - RAM + 512mb (upto 2gb)

---

### Post by Knowbuddy on 2008-10-12
Ahhh ok, that layout looks good too..

This is the first time I've seen anything about a /var partition though, what's that for? 

Also, I see you don't have a /home partition either, should I just forget the idea of a /home partition?

---

### Post by SuperSonic4 on 2008-10-12
I do have a /home partition, it is between / and /var

/var is where: "Variable files, such as logs, spool files, and temporary e-mail files."
[wiki]("http://en.wikipedia.org/wiki//var") hence it is used for small files that change and reiserfs is good for many small files such as the ones in /var.

Both are superfluous though the simplest setup would be

Windows - 60gb
Ubuntu (/) - 25gb
Swap - 2gb
Data - the rest

---

### Post by Knowbuddy on 2008-10-12
Ah ok!  I see the /home.

I like that, I'm going to try it.  Thanks a lot for the help! :D

Oh. one last questions...

When/where/with what software do I format the NTFS DATA drive?  During Windows install?  From GParted?

---

### Post by SuperSonic4 on 2008-10-12
Windows will do it although I think GParted is a better idea, especially since XP likes the whole drive to itself and is not nice when it comes to partitioning

---

### Post by Knowbuddy on 2008-10-12
Thanks so much for all your help.

---

### Post by Knowbuddy on 2008-10-12
One more question i have after thinking:

When i go to install software in windows (office, games, etc)...  Im going to want to install them to the windows partition, right?  I was thinking this whole time that i could put them on the data partition (which is why i made the windows partition so small originally.  My thinking was that if i had to reinstall windows, i wouldnt have to reinstall all my software again, but that wont work because of registry edits and such, right?

---

### Post by Idefix82 on 2008-10-12
Correct!

Just to add to the advice you have been given: you can [read here some of my thoughts]("http://ubuntuforums.org/showthread.php?t=928600&page=2") on why to create more than the minimal number of partitions. Have a look at my first two posts on this page, particularly the second one. It explains what a separate /var partition is good for.

---

### Post by SuperSonic4 on 2008-10-12
Yeah, install programs to the windows partition (hence I gave it a relatively large amount of space). The data disc would essentially be multimedia and documents (you can change the default save path in some applications and thus set it to save to the media partition)

Just a couple of extras

Installing [fs-driver]("http://www.fs-driver.org/") on windows will give it read and write access to ubuntu's ext3 partition

In ubuntu typing the following code will allow you to set ntfs drives to automount at boot (I found it useful for data most of all)
```
sudo apt-get install ntfs-config
```

---

### Post by Knowbuddy on 2008-10-12
Ok, now I'm stumped again.  

I have blown away all partitions, created an NTFS partition of 60 GB, and installed XP Pro on it.

I booted into XP pro, rebooted using Ubuntu live CD.

1.  Made a ext3 partition of 25GB marked PRIMARY and set it to mount to /root.  

Made a second ext3 partition of 10GB, marked PRIMARY, and set to /home.

Made a single reiserfs partition, marked it LOGICAL (messed up here?), set it for /var.

Made a single SWAP partition of 2 GB. Marked it for LOGICAL (again, was a guess...)

So, if I look at GParted, this is what I see:

/dev/sda1   NTFS   58.59 GiB   Flags-boot

/dev/sda2   ext3   23.28 GiB   

/dev/sda3   ext3   9.32 GiB

<<<drop down arrow>>>/dev/sda4   extended   4.66 GiB
               <>/dev/sda5   reiserfs   Label-set   2.80 GiB
               <>/dev/sda6   linux-swap   1.86 GiB

unallocated   500.32 GiB



So what I tried to do was right click in the unallocated and click "New" and I get the error:

**It is not possible to create more than 4 primary partitions**  

If you want more partitions you should first create an extended partition... etc etc etc...

But I thought that I only had 3 primary partitions thus far?

~B

---

### Post by mihaiv on 2008-10-12
Resize the extended partition in order to include all unallocated space. After that create a logical partition inside the extended partition.

---

### Post by Knowbuddy on 2008-10-12
DUHHHHHHHHHH

Okay, damn think I love you guys.

---

