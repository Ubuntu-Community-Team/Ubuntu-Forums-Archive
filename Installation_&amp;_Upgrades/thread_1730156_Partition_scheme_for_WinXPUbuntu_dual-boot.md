---
title: "Partition scheme for WinXP/Ubuntu dual-boot"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2011-04-15
I've done quite a few installs, but have not used the method
of partitioning prior to installation. Therefore, I would like
to have opinions as to whether I have done the right thing.
FYI: I have a HP 110 mini netbook with a 160-Gig hard drive (HD).
I have wiped the disk and repartitioned to prepare for a dual-boot
install of windows XP and Ubuntu.
It currently has 1 Gig of RAM, but am ordering a 2-gig stick.
I used gparted to create the following partitioning scheme:
/dev/sda1 primary partition ntfs 68 Gig for Windows
/dev/sda2 primary partition fat32 5 Gig for data exchange
/dev/sda4 extended partition divided as follows
--/dev/sda5 logical partition ext3 28 Gig for /
--/dev/sda6 logical partition ext3 28 Gig for /home
--/dev/sda7 logical partition ext3 14 Gig for /usr/local/bin
/dev/sda3 swap partition
Any comments and/or caveats are welcomed.
thanks
tim

---

### Post by Dutch70 on 2011-04-15
> **tim042849 said:**
> I've done quite a few installs, but have not used the method
of partitioning prior to installation. Therefore, I would like
to have opinions as to whether I have done the right thing.
FYI: I have a HP 110 mini netbook with a 160-Gig hard drive (HD).
I have wiped the disk and repartitioned to prepare for a dual-boot
install of windows XP and Ubuntu.
It currently has 1 Gig of RAM, but am ordering a 2-gig stick.
I used gparted to create the following partitioning scheme:
/dev/sda1 primary partition ntfs 68 Gig for Windows
/dev/sda2 primary partition fat32 5 Gig for data exchange
/dev/sda4 extended partition divided as follows
--/dev/sda5 logical partition ext3 28 Gig for /
--/dev/sda6 logical partition ext3 28 Gig for /home
--/dev/sda7 logical partition ext3 14 Gig for /usr/local/bin
/dev/sda3 swap partition
Any comments and/or caveats are welcomed.
thanks
tim

Just things I'm curious about...

Swap in a primary partition? not necessary & you only get 4. 

I'm not sure why you want a prtn for /usr/local/bin.

No reason for a FAT32 formatting that I'm aware of, you can use ntfs. 

Also, is there a reason you're not using ext4? 

I believe I would make "/" about 15-20GB max, and give the rest to /home. Forget the /usr/local/bin prtn unless there is a reason you need it. 

Edit: Here's my partitioning scheme for you
sda1 - windows
sda2 - Extended
sda5 - / - 20GB
sda6 - /home - the remainder of your hdd.
sda7 - data - ntfs 5GB
sda8 - swap - 3GB

Of course you could skip the separate /home partition and just use a large data partition for all your files.

Let's see what others have to say.

---

### Post by tim042849 on 2011-04-15
Hi Dutch70:
I'm with you on a couple of things. I could change the second
partition to ntfs since linux can write to ntfs. I could put the
swap partition into the extended partition.

As for the the /, /home, /usr/local/bin schema: I'm sticking
with that one. I do a lot of compiling - thus /usr/local/bin
partition - and with /home on a separate partition I retain both 
user settings and 'hand-compiled' applications in an OS upgrade.

So my remaining question is: Why do you recommend ext3 over ext4?
And I would welcome other comments on ext3 vs ext4. (even tho I
am inclined to go with your recommendation).
Thanks for the reply.
Very helpful
Tim

---

### Post by Dutch70 on 2011-04-15
Ok, I see why you need the /usr/local/bin now.

I recommended ext4, not ext3. Mostly just because it's the latest. 

I fully understand the /home, it's a great thing for sure. 

However Keeping a large data partition formatted to ntfs can be used by both windows and Ubuntu & you can symlink folders in your home folder to your data prtn. Also, you can retain your settings by backing up your .config folder. 

Since we're talking about partitions, have a look at mine. My data prtn was ntfs until about 3 days ago. I decided I didn't care about accessing it from windows anymore. However I can access my /home prtn in Ubuntu Mav which is formatted to ext2, using a program called ntfs driver.

---

### Post by tim042849 on 2011-04-15
Yeah, I'm going to drop the fat32 partition and just go with
one ntfs partition. I've been thinking like the 'old days' when
linux couldn't read ntfs at all, thus the fat32 thinking. Got to 
get over that...

My business partner, who has been using linux since the very
first distro/version recommended that I stick with ext3. He's
the sysadmin in the business and suggested going with tried and
true vs latest and (possibly) greatest. 

Anyway, thanks for the screen shots and the input Dutch70.
cheers
tim
P.S. - On this forum, what is the process for marking the
thread as 'solved'?

---

### Post by Dutch70 on 2011-04-16
You're welcome, hope everything goes well for you. 

To mark it solved, click on Thread Tools at the top of the page.

---

