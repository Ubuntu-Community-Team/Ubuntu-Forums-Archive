---
title: "something went wrong with the partitioning"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by muzcuk on 2006-10-06
First of all, I did this a thousand times. I pretty much know what I am doing. The thing is, this is the first time I am installing linux on a sata hdd and I didn't even know that it was sata before I was half way in. 

Well, I don't see a reason to explain it from scratch, but somehow at some point something went wrong with the partitioning.

Before I booted linux, I did some partitioning with windows (partition magic). I had a 10 gb win partition (ntfs) then about 6 gb of free space and then another ntfs partition which is like 40 gb.

So I put 2 partitions (1 ext3, 1 swap) in that 6 gigs of free space, sounds fair, right?

But installation fails (I can worry about that later) and when I reboot my windows doesn't work at all. It's not even saying anything, just rebooting itself at some point while starting up (it does start up, I don't have anyth&#305;ng wrong with the bootloader). I can barely see a blue screen before it reboots. This is why I don't like that OS.. How can I possibly fix it if I don't know what the **** is wrong..!?

Ok, so I boot the live cd and see my 40 gig partition as an extended partition, though it was primary in the beginning, and it says "unknown" for the filesystem, yet it does say "ntfs" for the other windows partition.

Forget about the linux, I'll do a clean dual boot install (school requires the ******* windows) right after I save my 40 gb partition. I just have to take care of my 40 gigs now. It was full of rare stuff.

I've seen this kind of problems, I know I can fix it. I know what the problem is, theorically, but I can't find a pratic solution. The data is in there, I know it. There has to be something wrong with the partition tables, or the formattig.

So someone please tell me something. How do I save my data? I can sacrifice the first win partition, I can do a linux install to the first 15 - 20 (whatever) gigs of the drive, but that doesn't have any use if I can't mount my 40 gig partition. 

Or would it be rather simpler to do a new win install (or save the old one, maybe) and use win based data recovery tools?

Ooooor maybe all this is not necessary at all? Can I fix the whole thing manually?

---

### Post by marcelm on 2006-10-06
I had the same problem. It was Gparted that tried to resize the Ntfs partition of my win xp, but Failed. ('error' without any more text). 
After a reboot the win XP was corrupt. I tried the recovery console and type: 

 fixboot

and that worked a bit but the partition was messed up. So try a chkdsk and a fixboot maybe it fixes itself, otherwise get your win XP disc.. :eek:

---

### Post by randomnumber on 2006-10-07
I think that you may try the recovery util's on the windows cd. This sometimes fixes boot problems. It basicly reinstalls all esential files if it can. If your partition is realy corupted that badly you may not be able to fix it. 

I like my partitions to be simple and have ,through experience, found that windows is picky about where is goes on the harddrive.

My disk on my laptop looks like this:
sda1   ntfs   winXP
sda2   fat    a shared partition for moving files between os
sda3   /      root file system for ubuntu
sda4   swap   swap

If you notice I use a partition for data to be used on both os's. I do not want my os's changing data on the other partition. I dont trust either one that much.

There can only be max of 4 primary partitions. Extended partitions can be made of the primary to make it look like more partitions. I think that winXP can only be installed on a primary. I have tried to install winxp on a partition at the end of the harddrive and it failed, I did not even have ubuntu or any other os on the computer. The failure of xp happened after installation that gave no indication that something was wrong. When I rebooted all I got was the bios and then nothing.

Another consideration is hidden partitions. I corputed a harddrive when I ran a gentoo live cd on it and the harddrive had a hidden partition. I might have done something more to cause the issue but I dont remmeber.

hope that some of this may have helped. this is my first post.

---

