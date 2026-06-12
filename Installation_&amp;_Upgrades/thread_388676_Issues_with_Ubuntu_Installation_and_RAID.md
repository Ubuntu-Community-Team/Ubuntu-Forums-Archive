---
title: "Issues with Ubuntu Installation and RAID"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by Kazol on 2007-03-19
I am about to install Ubuntu on an old spare system (for a server):

PIII 800Mhz
256MB RAM
17+20 GB HD
DVD-ROM, CD-RW, Intel 10/100

I want to use RAID-1 to get 17GB of space, but had trouble installing it on the alternate cd. I followed all howto guides, but still the system would not install after I created 2 equal RAID partitions on both HDs, 768MB for swap and the rest for /. I specified "Software RAID", tried both combinations of 2 active devices and 1 active and 1 backup, but still it keeps getting stuck at the partitioner. I tried applying changes then manually going ahead in the installation, but it still goes back to the partitioner. One theory I have is that when I use RAID, it marks the disk as "K", to keep the partition instead of "F". Someone told me to press enter, and I tried that, along with every other combination.

So someone told me I could use mdam or something to add a RAID volume after I installed Ubuntu, so I installed the regular version off the live cd. When I booted, I got error messages:
> Target filesystem doesn't have /sbin/init
/bin/sh: can't access tty: job control turned off
Before booting, during the installation, the installer told me it could not create a filesystem. Funny thing, I successfully installed Ubuntu this way before, although the hd was different. However the same hd was used on a different computer with Ubuntu also installed. I also tried completely wiping the disk out by full NTFS formatting using the Windows setup.

What should I do? I'm hoping to find out some way to install RAID with the alternate CD, because then I wouldn't have to worry about creating a RAID volume, or that boot error message above. I am very close to installing Windows Server 2003, but I haven't given up yet.

---

### Post by Foudre on 2007-03-20
i'm in a simalair situation, 800 mhz pentium 3, 1024 meg ram, 4 scsi 10000 rpm raided hard disks 18 gig a piece (chained, would like to unchain them so i can get 4  x 18 gig, instead of just 18 gigs, its hardly enough space to do what i want with it as a server is conserned, the software will have plenty of room but what good is a ftp server, with like 2 gigs of space left for it after i get my radio server running on it) any ways, during the install of the normal ubutnu it stops when it trys to format the drive, (SuSE did this fine, but for other reason i'm using ubuntu if i can) and when i try to manually edit partitions it says can't access blah blah blah. Going to try the ubuntu server, I figure they would have better raid support on it, I tried suse cause it had good raid support, but i said screw it after i remember why i hated it to begin with (fricken yast blows, when it come to package managment)

I'll let you know if the ubuntu server edition works decently with the raid scsi setup, i assume you have scsi in yours too. Will if it installs and works i'll let you know, their description of these things aren't very good, (I may have to install windows server 2000 something on it again, but i kinda want remote access with what i want to do, and it doesn't have it, sigh)

---

### Post by Kazol on 2007-03-20
I'll maybe try installing Ubuntu off the alternate CD. Can someone tell me one thing, could I enable RAID-1 after installation? (supposing I have made 2 equal partitions on both hds-swap and /)

Also is Gentoo Linux a good choice for servers, Linux newbies like me, and has RAID-1 support (with easy installation)?

---

### Post by Kazol on 2007-04-01
Has anyone ever set up RAID-1? How difficult is this?

---

