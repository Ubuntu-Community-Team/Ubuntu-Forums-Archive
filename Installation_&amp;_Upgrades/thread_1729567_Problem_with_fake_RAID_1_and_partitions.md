---
title: "Problem with fake RAID 1 and partitions"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by N4zroth on 2011-04-15
Hey guys,
I recently got a new computer, and so I'm trying to install Ubuntu alongside my already installed Windows 7 I had it running fine on my old one which also had a fake RAID 1.
So first to my hardware, then my problem: I got 16 GB of RAM, 2 TB HDD space in RAID 1 with an onboard Intel controller on my ASUS P8P67 and an i7 2600k.
When I try to use the desktop CD 11.04 or 10.10 it just crashes/hangs with an error due to casper. So I started trying the alternate installation CD, but both 11.04 and 10.10 don't detect the partitions correctly, they look this way: [http://tinypic.com/view.php?pic=28mfp75&s=7](http://tinypic.com/view.php?pic=28mfp75&s=7) . So I booted into a live CD (with 11.04 desktop cd) and checked fdisk which is as follows: [http://pastebin.com/kFvDRZ0g](http://pastebin.com/kFvDRZ0g) . cfdisk doesn't even start. The way everything is supposed to be (and is seen under Windows 7): [http://tinypic.com/view.php?pic=2qv5url&s=7](http://tinypic.com/view.php?pic=2qv5url&s=7) . On IRC I was told to remake all partitions, is there any other way you can think of?
Thanks for your help.

---

### Post by ronparent on 2011-04-15
Generally 10.10 desktop has worked well with raid and 11.04 to some degree but with problems. What partitioning system are you using? We need to boot a live cd - with a live cd we can get a look at what an installed system will see. If you can't get the live cd to boot you are unlikely to have better success with an installed system.

I suggest you focus on 10.10 since 11.04 has not been released yet and still has problems with raid (live cd will probably run but probably not install a run-able system without workarounds). A casper error suggest a corrupted iso image. Do a checksum check with the drive you are using. Post your results here. 

Your system specs seem to be leading edge and we may ultimately have to resort to a bug report to get it supported. Meanwhile we may be able to eliminate the usual suspects. Hang in there.

---

### Post by N4zroth on 2011-04-15
Thank you very much, I'll boot into the 10.l0 live CD as soon as I'm back home (I'm away for the weekend), what info do you need from there?
I'll also look at the checksums and verify them.
I partitioned the whole disk using the Windows 7 disk management utility which worked fine for me the last time and on my 32 bit laptop, so I suspected no harm there :)
Thanks again in advance for your help.

---

### Post by psusi on 2011-04-15
Dynamic disks are a Microsoft proprietary format that is unsupported.  You will need to convert the disk back to basic.

Also out of curiosity, why are you running raid1?  Raid is no substitute for backups.  The purpose of raid-1 is not to keep your data safe ( you need backups for that ) but rather to keep the machine running when a drive fails.  Lately people have been confusing the two and thinking they don't need backups if they have raid-1, then learn the hard way this is not the case.

---

### Post by N4zroth on 2011-04-15
I don't think I created a dynamic disk, did I? I didn't have an option to change that while creating a volume, and it worked the same way on my old computer.
I'm running RAID-1 mainly for the increased speed, for backup I use a NAS with RAID-0 and mirror the important data to a portable HDD.

Edit: Oh actually I see you're right, sorry, but how comes that? I created the partitions the same way I did on my laptop/old computer, how can I change the type? And if I have to recreate them, how do I tell Windows to not make them dynamic? I don't think I saw an option for that.

---

### Post by psusi on 2011-04-15
Raid-0 increases speed, not raid-1.

You used to have to explicitly convert a disk from basic to dynamic, but you are prompted to do so if you try to create more than 4 primary partitions.  I'm not sure how things are now as I've been off using Windows for a while.

I'm not sure if you can convert back to basic without totally reformatting.

---

### Post by N4zroth on 2011-04-15
Sorry, I messed up the 1 and 0 levels, I think I'm never going to learn that ;-)
I'm using stripe (at least I know that, lol) on my computer and mirror on my NAS, to make things clear.
Ah 4 partitions, I see ... so the 100 MB Windows created partition destroys the whole thingy :p
On the topic of converting them I found this topic: [http://www.wilderssecurity.com/showthread.php?t=191006](http://www.wilderssecurity.com/showthread.php?t=191006) but I'm not really sure if that's a safe way (in fact, I rather doubt it at this does seem a bit TOO hacky). Does anybody have experience with that? I'll do further research I think, completely formatting again isn't funny in any way :(

Edit: I found several topics on Google about reading dynamic NTFS drives under Ubuntu so that should be essentially possible, shouldn't it?

---

### Post by ronparent on 2011-04-15
I agree with psusi's observations. 

Win7 introduce some new curves into the mix. Generally I've had little problem using a raid0 with Win7 NTFSs partitions alongside my Ubuntu/mint installs. In general, though, I use Win7 to create the NTFS primary partitions and gparted to create the extended partition as well as the ext4 partitions for installing to as well as any extended NTFS partitions. That way the extended ext4 partitions are defined so that the linux systems can use them and the extended NTFS partitions are usable by win7. It does get complicated when I state it that way.

Bottom line is that the win7 partitioning utility will not create a normal extended partition!

---

### Post by N4zroth on 2011-04-15
Another question, is it even possible to have more than 4 basic volumes on a RAID disk under Windows 7/in general? I didn't find a solution anywhere. I'm currently toying around with dynamic and basic partitions on and old computer.

Edit: Seems like that's not possible. So I have to find out if I can delete the Windows created volume and then convert it back.
Edit 2: Yes, both seems possible, converting with the EASEUS Partition manager is easy, just need to delete the damn System Reserved Volume and I should be ready to finally install Ubuntu. Yey!
So until the install fails again after the changes, everything should be fine (except that I hate the dynamic volumes from Windows 7). Thanks a lot for your help!

---

### Post by ronparent on 2011-04-15
It appears that win7 allows more than four primary partitions but is only an illusion. My experience when I didn't know what I was doing was to delete any but required win7 primary partitins (the first 2) and to use gparted to create an extended partition and any ntfs or ext4 partitions I wanted within that extended. In my case win7 then id'd all the extended partitions correctly. Any partitions I then attempted to then create with win7 would then appear as a primary partition. So I made a rule for myself to never use win7 to create any partitions in the extended space. That seems to have worked. I know that sounds wierd!

---

### Post by N4zroth on 2011-04-19
Okay, now I've got only 4 Basic Volumes on the RAID, the Ubuntu setup detects them correctly but it says that the 350 unused GB are unusable for installing Ubuntu on them. Any ideas why and what to do?

---

### Post by srs5694 on 2011-04-19
Chances are you've got four primary partitions, and that's the limit under the Master Boot Record (MBR) partitioning system. You may be able to convert one or more of those partitions into logical partition(s) with my [FixParts](http://www.rodsbooks.com/fixparts/) program, but I can't be positive of that without more detail. I recommend you run the following command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to keep the results legible. Also tell us if you plan to resize any of the partitions, and if so which ones.

---

### Post by N4zroth on 2011-04-20
Thanks a lot, you were right. I managed to convert all except the windows partition to logical ones and now I've got Ubuntu up and running. Thanks a lot!
To convert the partitions I used "Partition Wizard", just if anyone has the same problem.
So thanks a lot to you all!

---

