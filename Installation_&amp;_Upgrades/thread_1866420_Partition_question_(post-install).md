---
title: "Partition question (post-install)"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by pcar916 on 2011-10-21
The goals: 
1. Split the 11.10 /root partition into /root and /home.
2. Resize the swap partition (should be easy, haven't tried it yet)

I've just upgraded from 10.10 to 11.10. Unity is weird but I'll get used to it. This is a dual-boot with Win7. Both work just fine so far with my limited testing. As long as I can get to the command line and continue actually learning Linux I'm good. 

I was testing the Ubuntu interface so I allowed the default partition to be a combined /boot and /home. I know this isn't ideal and now want to isolate the system from my data.

Here's a GParted view of my current partition scheme.

[IMG]http://ubuntuforums.org/home/ron/Pictures/GParted_Current.png[/IMG]

Here's what makes sense to me on this laptop.

1. My swap size is too small and /dev/sda6 needs to be 3.5Mb to reflect 3Gb of RAM.
2. Resize the /dev/sda5 partition to 8Gb to contain only the system
3. Devote the remaining space to /dev/sda7 and 'Move" /home to that partition

The two ultimate questions: 
1. Can I do this post-install or should I reinstall since this is a fresh installation with few applications?
2. Is moving /home as simple as copying it to the new partition or are there other files that need to go there as well and more configuration to do?

Happy to RTFM and did, but I haven't seen the solution yet in this forum.

Thanks in advance.

---

### Post by lightwarrior on 2011-10-21
I was not able to see your gparted info.

The best is to re-install Ubuntu.  Otherwise you will need to play with fstab file and UUID, things that might get tricky, and haven't played with them in a long time.

Apparently you already know this, but I must say that when you partition the hard disk, you can only have 4 primary partitions.  If you need more, you will need to create a logical partition on the fourth primary.

The swap partition in Linux is different than in Windows page file.  In Linux, it doesn't need to match the ram.  Only assign the necessary swap to fit all your open files and expected ram usage.  Linux is very efficient, if my Ram is above 2GB, I usually use a 256 MB swap, I haven't seen my swap used at all.  If you intend to open large files or have big processing, then use as much swap you think you need.

If I need to share data between Windows and Linux, I create a NTFS partition to save files and both OS will see them.

Back to partitions.  Once you created all partitions, you need to assign the directories to each partition.  In the old days, you could have a 100MB partition for /BOOT.  You can have your /HOME directory pointing to a partition during install.

---

### Post by pcar916 on 2011-10-21
Obviously I haven't figured out how to copy a .png screen shot into the post. I first dragged-and-dropped it, then I used the "Insert Image" button with the file location. i.e. /home/... <filename>
While I solve that operator issue, The table looks like this.

Win7 
/dev/sda1                ntfs                              100.00 GiB     used 33.59 MiB
/dev/sda2                ntfs                              129.18 GiB     -

Oneiric Ocelot
/dev/sda3               extended                       103.61 GiB
          - /dev/sda5   ext4  mount point: /       101.74 GiB     used: 4.49 GiB
          - /dev/sda6   linux-swap                        1.87 GiB

Thanks

---

### Post by 2F4U on 2011-10-21
I would also suggest to do a fresh installation. The things you want to change are complicated and may easily leave you with an unusable system.

---

### Post by satanselbow on 2011-10-21
IMHO it would be simpler (quicker and cleaner) to just bite the bullet and reinstall with your required partition scheme.

If you fancy making it more of a "learn a few things along the way"
this page has what you need ;)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2011-10-21
I like 10 to 20GB for / (root). If you write a DVD for backup it may use 4GB in /tmp and if / is too small it will use swap.

Swap only has to be the size of RAM in MiB if you want to hibernate. With dual booting and how fast Ubuntu boots, I do not hibernate at all.

+1 on pcar916 of a shared NTFS partition. Windows does not like a lot of writing into its system partition. Even some Windows users suggest a d: drive so when you have to reinstall you do not have to reinstall your data (backups still required).

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Minor changes to partitions should not change UUID or /dev/sdaX. But if they do change you will have to reinstall grub2's boot loader and edit fstab, so have an up to date liveCD available, just in case. Should be using latest LiveCD for Gparted anyway.

Three similar sets of instructions using different commands for copy.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by lightwarrior on 2011-10-21
Ok, now I see.  I don't know how to post images either :)

This is the Ubuntu guide to move your /HOME to another partition without reinstalling:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You will need to shrink your sda5.

I would strongly suggest you to reinstall Ubuntu.  I don't believe in OS upgrades, but that's me.

My 11.10 new installation is quite buggy.  I went back to my 10.04 LTS.  I like LTS because its support lasts for 3 years, and it is very stable.

---

### Post by pcar916 on 2011-10-21
> **lightwarrior said:**
> I was not able to see your gparted info.

The best is to re-install Ubuntu.  Otherwise you will need to play with fstab file and UUID, things that might get tricky, and haven't played with them in a long time.

[COLOR=Red]I thought this might be the case but figured this is a good time to learn more about Linux partition tables and tools.[/COLOR]

Apparently you already know this, but I must say that when you partition the hard disk, you can only have 4 primary partitions.  If you need more, you will need to create a logical partition on the fourth primary.

[COLOR=Red]I'd forgotten the 4 primary rule, but adding a /dev/sda4 should still leave me ok with that.[/COLOR]

The swap partition in Linux is different than in Windows page file.  In Linux, it doesn't need to match the ram.  Only assign the necessary swap to fit all your open files and expected ram usage.  Linux is very efficient, if my Ram is above 2GB, I usually use a 256 MB swap, I haven't seen my swap used at all.  If you intend to open large files or have big processing, then use as much swap you think you need.

[COLOR=Red]I was going by the installation guides for the sizing of swap-space and saw 2x RAM. Am I reading the wrong stuff?[/COLOR]

If I need to share data between Windows and Linux, I create a NTFS partition to save files and both OS will see them.

[COLOR=Red]Since my WIN7 partitions are already ntfs, and Ubuntu can see it as well. Other than the obvious advantage of splitting WIN7 system from data files, do I need another one? [/COLOR]

Back to partitions.  Once you created all partitions, you need to assign the directories to each partition.  In the old days, you could have a 100MB partition for /BOOT.  You can have your /HOME directory pointing to a partition during install.

[COLOR=Red]The mount point chosen when each partition is created will assign the directories yes?[/COLOR]
[COLOR=Red]
The reason I didn't split the partitions up in the beginning was that I was presented with five or six file systems to choose from. None were ntfs and I didn't know the differences during the install. Naturally, I don't remember them now but one was clearly obsolete, but the others required research I need to do now, and there wasn't a default system.[/COLOR]

[COLOR=Red]I do know that ext1-4 are primaries and ext5 and greater are logical.  Reading suggests that ext4 journaling file system is the correct one for 11.10.
[/COLOR]
One correction is that I'm running 11.10 (Oneric Ocelot) not Natty Narwhal. I'll edit that in the original post.

---

### Post by pcar916 on 2011-10-21
Thanks to all of you for the clarity. The path is clear. 

I'm going to reinstall for my ultimate solution, but first, moving /home looks like a good lesson in some tools/commands I've never used before and a much needed primer in fs architecture. An outstanding response this was.

I'll mark this as solved and attack this over the weekend. Is it useful to report back on lessons learned or problems solved?

---

### Post by pcar916 on 2011-10-23
Success.  I've done the suggestions above as follows.

Created...
1. a separate shared (11.10/Win7) ntfs partition
2. separate partitions for /root (20GiB) and /home
3. Swap partition is the size of my RAM

The result is a faster 11.10 this time... remarkably faster in fact. I don't know if that's a result of a separate /root partition, larger swap space, or something else. 

At any rate, thanks to all who contributed and for the reading suggestions. Now I have to work command line mechanics and re-learn permissions (from many years ago).

---

