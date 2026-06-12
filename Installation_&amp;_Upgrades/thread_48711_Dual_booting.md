---
title: "Dual booting"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by chupucabras on 2005-07-13
Hey

I downloaded the ubuntu live cd a while ago, and I like what I've seen so far. I'd like to do a proper HD installation and run a dual-boot system with windows XP. I know you're all probably completely fed up with questions about dual-booting, but although I've read all the posts here and elsewhere that I can find over the last few days, I'm not feeling particularly confident about going ahead with this. At least not until I've asked some specific questions which I've either not found an answer to elsewhere, or found seemingly conflicting answers in different places.

For example, the vast majority of info I've found about dual-booting seems concerned with installing linux on the same HD as XP, but a different partition. This seems quite complicated, with numerous ways to accidently screw up the MBR and prevent XP from working. I'm thinking it must be easier to install linux on a completely separate disk. Here's what I have currently in terms of HD drives:

Two 80GB IDE drives, one is the primary master, the other is primary slave.

The primary master is partitioned into two; approx. 15GB for XP, 65GB for programs, files, etc. 

The primary slave is fairly new; I got it for extra storage space, before I decided to install ubuntu. So it is set up as one large NTFS partition currently. I would like to move the files from this drive to either the other HDD or onto DVD+/-R and install ubuntu here, repartitioning etc. as needed. 

Questions:

1. Will this work? One site I looked at seemed to say that the /boot partition (?) for linux must be on the same physical drive as XP (ie. the primary master, but not the same partition as XP). Other sites seem to imply that this is not the case, but don't seem to elaborate further on this.

2. What file system should I use when I repartition my drive? NTFS? FAT32? EXT2/3? If I can use any of these, what are the benefits/drawbacks of each?

3. How exactly should I partition the drive? I've seen several recommendations to use multiple smaller partitions instead of one huge one, possibly with separate partitions for the linux kernel itself, another for the swap file, and another (FAT32? does this mean that linux cannot understand NTFS drives?) for sharing files between xp and linux. Any recommendations here would be appreciated.

4. Which boot manager should I use? Grub seems like the best from what I've read, but there is something on the ubuntu wiki about people having trouble with it. Does this need to be installed to the primary master, or to the drive with ubuntu on? What exactly do I have to avoid doing to make sure I don't screw XP up?

5. What order should I do everything in? Do I need to format/partition my second HD from windows first, or can I just backup everything I want, boot from the ubuntu CD, and install away?


I think those are all the questions I have for now, although I may have more specific questions when I've had some answers to these.. 

Many thanks,

Dan

---

### Post by alastair on 2005-07-13
This is no problem. A very common and useable setup.

1) Yes, this will work. All of Linux on the 2nd disk (/dev/hdb in linux, (hd1) in GRUB)

2) For Linux, stick with the default, normal filesystems e.g. ext3

3) For the Linux disk, have the OS and your home directory on different partitions e.g. this should do :

/ - part 1
swap - part 2
/home - part3

4) GRUB is fine. On install, before installing GRUB to the MBR of disk 1, it will show you what it has found i.e. it should list XP as well as an option.

5) Install away - but back up any data on the disk you install Linux on first. You can partition the disk from the installer.

Come back if you have problems.

Good luck.

---

### Post by chupucabras on 2005-07-13
Excellent, thanks Alastair. One or two minor questions though:


[QUOTE=alastair]

2) For Linux, stick with the default, normal filesystems e.g. ext3

3) For the Linux disk, have the OS and your home directory on different partitions e.g. this should do :

/ - part 1
swap - part 2
/home - part3

[/quote]

I assume XP will not read ext3 partitions? Could I make part 3 (/home) FAT32 or NTFS so it could be accessed from both operating systems? If not, would it be easy enough to add a fourth partition that could be accessed from XP as well as Linux? How big should each of these partitions be? (particularly the swap drive).

> 

4) GRUB is fine. On install, before installing GRUB to the MBR of disk 1, it will show you what it has found i.e. it should list XP as well as an option.



Does this mean I should install GRUB onto my master drive (ie. the one with XP on it)? When you say disk 1 are you counting from 0 or from 1?


Once again, many thanks for the prompt and relevant response.

Dan

---

### Post by alastair on 2005-07-13
OK - I did not consider you might want access to a filesystem from XP.

I would NOT make any native linux partition FAT or NTFS (i.e. / or /home). But by all means make an extra partition (/shared as /dev/hdb4 say) - of whatever size you can live with. You might want to leave this partition "as is" (no mount, no format/filesystem in linux). Format it in XP - then return to Linux and mount it.

Partitions - a rough guess, I cannot be specific for you :

/ == 12 GB say (remember we also have /var here for cached packages etc.)
swap == 2x RAM say? == 1 GB?
/home == 30 GB ?
/shared == rest (~35 GB?)

But I do not know the split that is best for you (/home, /shared).


If the install sees XP, and mentions it in the "list" it presents, then things should be fine installing GRUB on the MBR of disk 1 i.e. the first, XP disk (primary IDE).

Hope that helps.

---

