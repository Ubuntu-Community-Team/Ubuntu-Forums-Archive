---
title: "Reclaim XP Partition"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by timjohn7 on 2008-10-05
I have what I would assume to be a common issue.
After dual booting Ubuntu and XP for some months, I have taken the plunge and delested my XP installation and want to dedicate my 40Gb HDD to Ubuntu.
I'd also like to separate my \ and \home partitions.
My problem is that 
  a.  my XP partition has been "shrunk" over time as I claimed more & more space for Ubuntu apps and data and is now too small to copy my Ubuntu partition into;
  b.  my Hardy installation is fully updated, and tweaked for my various peripherals, so I don't really want to do a fresh install; and
  c.  I didn't defrag the XP partition before deleting critical windows folders, so the partition may well be highly fragmented. Can I check/fix this?  I have reformated this partition from NTFS to ext3 so I assume this is moot?

I do have an External HDD to which I can copy/backup any partitions and I am also happy to do a fresh Intrepid install, but I'd really like to keep my current /home intact if possible.

Please advise...?

---

### Post by qpieus on 2008-10-05
OK, if you have already formatted the xp partition to ext3, then problems #1 and 3 are moot.
As for #2, that's not a problem either. You can move your /home to the old xp partition if you'd like (that seems reasonable to me since you just freed up that partition). This way you can keep your current installation AND make a separate /home.

Here's how I made a separate /home:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

It's pretty easy. The basic procedure is to copy over your /home files to the new partition, then edit your /etc/fstab file to make the new partition mount as /home.

Take your time and read the comments in that link, too. Many people have some really helpful comments there.

psychocats also has a how-to:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here's a few commands you can run in a terminal to find out what partitions you have and where they are currently mounted:

sudo fdisk -l
df -h
mount

---

### Post by linfidel on 2008-10-05
Also, if the partiton is too small for your /home directory (which could be bigger than the rest of the drive), you can make the old XP partition simply be a directory mounted to /home until you figure out how to best divvy things up. 

I had some extra space on a drive that I made into a misc directory, mounted as /home/misc.  But I already had a separate /home.

Using gparted, you can shrink partitions without losing data, so you don't need to copy the data off first.

---

### Post by timjohn7 on 2008-10-06
> **linfidel said:**
> Also, if the partiton is too small for your /home directory (which could be bigger than the rest of the drive), you can make the old XP partition simply be a directory mounted to /home until you figure out how to best divvy things up. 

I had some extra space on a drive that I made into a misc directory, mounted as /home/misc.  But I already had a separate /home.


Us ing gparted, you can shrink partitions without losing data, so you don't need to copy the data off first.
Yep... that is exactly my problem. 
Partition 1 (ex XP) 10Gb Empty ext3
Partition 2 Ubuntu 27Gb 23Gb used ext3
Partition 3 Swap 1Gb
So ideally I'd like to move \ to the 1st partition & leave \home on the 2nd partition. I've backed up \ & \home to an external HDD using Quickstart..
I'm thinking fresh Intrepid installation, separate \home
partition and then restore \home to that partition using Quickstart.
Does that make sense or am I overcomplicating the problem?
  .

---

### Post by timjohn7 on 2008-10-06
Thanks very much for the advice, links and help. My only remaining problem is the relative size of the 2 partitions (ex XP partition=10Gb, current Ubuntu Partition=27Gb of which 22Gb is used).
I've backed everything up to an external USB HDD so I'm considering a fresh Intrepid installation, designating my 27Gb partition as \home and the 10Gb partition as \.  Thereafter restoring the backed-up \home to the 27Gb partition and fixing fstab as instructed.
Does that make sense to get around the partition size problem?
Alternatively... should I temporarily transfer extra data to my external drive, resize partitions, move \ and \home to the 1st partition, follow instruction to separate \home back to the "old" partition, and then copy extra data back, in other words leaving my currently installed and updated \ on the 10Gb ex XP partition?

---

### Post by vanadium on 2008-10-06
You are going to reinstall anyway. In your case, I would go for a single ubuntu system partition and a swap: your hard drive is too limited in space to conveniently divide it into partitions.

---

### Post by timjohn7 on 2008-10-06
Mmm... I hear you.
What about the principle of a separate \home partition so that new distros or updates could be installed without losing data?
Or would a /home backup & restore approach solve that problem more elegantly?

---

### Post by vanadium on 2008-10-06
> What about the principle of a separate \home partition so that new distros or updates could be installed without losing data?

Practically, this will mostly work, especially with single user systems. However, you should know that Linux is not designed for this. If an application in a new distro changed its config files slightly, there will be a problem with that application.

Also, you should not rely on this as a way to keep your user data (=documents, spreadsheets, pictures, ...) safe. You need a good and up to date backup of these data at any time. Your user data are unique and if lost, lost forever. An operating system is free and installed and mostly configured in less than two hours (there are notable exceptions).

You have a hard drive with limited space, in which case I would not hesitate and stick to a single partition. Do not backup your home (= user data + application configuration settings). Do backup your /home/$USER/Documents, /home/$USER/Pictures, and selected application data such as evolution or thunderbird mail.

That is just my opinion and advise for your case. Other ways are also possible and are equally valid with their advantages/drawbacks, or possibly added complexity. Linux is a free and highly configurable OS after all.

---

### Post by linfidel on 2008-10-06
I somewhat concur with vanadium; if you don't have lots of space, you'll be wasting some with two partitions.  10 GB is more than enough for the distro without /home, so you'll waste half that space.  If you have plenty of space, that doesn't matter.  If you don't have lots of media files, though, you'd probably be fine, especially if you make the XP partition smaller.

When I upgrade, I only format the system partition, and keep /home.  I have had no problems with this.  I think linux **is **designed to be used this way, and there are usually no conflicts with new versions.  If the configuration file format changes, they usually change the name of the file or directory.  It does require a little more attention to what's used and what's no longer used.

I have lots of customizations that I don't like to redo when I upgrade.  I use bash at work and home, and there are a lot of things I like to have available on both.  It's nice to be able to upgrade, and have most of the same settings available.

---

### Post by vanadium on 2008-10-06
> I think linux is designed to be used this way
It is not, but it usually works fine nevertheless.

---

### Post by timjohn7 on 2008-10-06
To all who have replied...
Thanks for your contributions which, as usual for this forum, have been enlightening, practical and provided in a friendly way.
Despite my small hard drive, I think that I will shrink the XP partition down to 5Gb, use it for a fresh Intrepid install and use the remaining 34 Gb as a separate \home partition.
As with most things in life, there are viable alternatives and pros & cons.  I certainly respect your views, vanadium, and accept that I may be wasting time & space but having installed way too many apps (for evaluation) and with a dangerous level of knowledge, I'm going to keep things separate until I have more experience.  The one advantage of a small HDD is that it imposes a degree of discipline when deciding what to keep or not.
I may call for your help during the process (hopefully not with a mouthful of humble pie)!

---

### Post by vanadium on 2008-10-06
> I certainly respect your views, vanadium, and accept that I may be wasting time & space but ..
It is your choice, and your option is equally valid and has its particular advantages. A nice thing of Linux is that is is very customizable. There are several ways to achieve something. I am sure you will succeed fine.

---

### Post by linfidel on 2008-10-06
> **vanadium said:**
> It is not, but it usually works fine nevertheless.
I get the impression you are one who likes to have people accept your statements without question, but unless you can come up with something better than "linux is not designed for this", I can't accept it as an absolute truth.  

Perhaps I should have said it is designed to be able to be used that way, but at least I came up with some advantages.  You are only saying it like you are Linus Torvalds and know all about the design.  Perhaps that's true, but you should come up with something to back up such an absolute statement to have credibility.  Or just say you don't think it works well that way, and give some reasons.

---

### Post by qpieus on 2008-10-06
> **timjohn7 said:**
> To all who have replied...
Despite my small hard drive, I think that I will shrink the XP partition down to 5Gb, use it for a fresh Intrepid install and use the remaining 34 Gb as a separate \home partition.

Sounds like a good plan. With the ease of installing nowadays, it's no sweat. I can highly recommend the separate home partition. I've had no trouble at all with it. As far as being able to set up your new installation similarly to how you have it now, I suggest backing up the /etc directory for sure. A lot of your system-wide setting are there, like xorg.conf, fstab, smb.conf, etc. The whole thing is approx. 10 MB, so it's no hassle to save all of it. Then once your new install is set up the way you like you can delete the /etc backup. I would also backup your /home directory to your external drive before you reinstall, just in case...

---

