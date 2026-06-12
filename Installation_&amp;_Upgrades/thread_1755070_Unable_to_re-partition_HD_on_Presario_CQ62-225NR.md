---
title: "Unable to re-partition HD on Presario CQ62-225NR"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by thinkren on 2011-05-10
Last year, I bought a Presario CQ62-225NR running 64 bit Windows 7 Home Premium.  With the recent release of Natty, I’ve decided to take the plunge and try out the Unity interface.  In preparing the hard drive for dual booting Ubuntu, I shrunk the C: Windows partition using Disk Manager and deleted the D: RECOVERY partition. 
 
The 200mb hidden SYSTEM boot partition and the 100mb E: HP_TOOLS partition were untouched.
 
So far so good.  I now have an unallocated block of free space roughly 140 GB in size between the Windows Partition and HP_TOOLS partition.  Disk Management shows the three remaining partitions to be healthy.
 
However, after I boot into the Gparted live-CD, I’m presented with a small mess.  Every partition is lite up with caution signs.  A new partition that doesn’t appear under Disk Manager has popped up out of nowhere. And all the labels have now been shifted.
 
In short, before partitioning:
 
/dev/sda1; ntfs; SYSTEM; 199mb; boot
 
/dev/sda2; ntfs; [no label]; 286.29gb

/dev/sda3; ntfs; RECOVERY; 11.5gb

/dev/sda4; fat32; HP_TOOLS
 
After partitioning, as reported by Gparted:
 
/dev/sda1; ntfs; SYSTEM; 992.5kb --- {Warning:Unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

/dev/sda2; ntfs; [no label]; 199mb; boot --- {Warning: unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

/dev/sda3; ntfs; HP_TOOLS; 156.68gb --- {Warning: ntfsresize v2.0.0 (libntfs 10:0:0)  Failed to startup volume: invalid argument.  ERROR(22): Opening '/dev/sda3' as NTFS failed: Invalid argument. The device '/dev/sda3' doesn't have a valid NTFS.  Maybe you selected the wrong partition?  Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?  This error might also occur if the disk was incorrectly repartitioned (see the ntfsresize FAQ).  Unable to read the contents of this file system!  Because of this some operation s may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

Unallocated; 141.11gb

/dev/sda4; fat32; [no label]; 103.34mb --- {Warning: Can't open /dev/sda4: No such file or directory.  Cannot initialize 'H:'  mlabel: Cannot initialize drive  dosfsck 3.0.9 (31 Jan 2010)  dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN  open: No such file or directory  Unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cuase might be a missing software package.  The following list of software packages is required for fat32 file system support: dosfstools, mtools.}
 
I have no idea how to interpret these results.  The whole point of repartitioning was to free up one of the 4 primary partitions for the use of Ubuntu.  If Gparted is to be trusted, it appears Windows 7 has for unspecified reason conjured up a new first partition and carefully hidden that fact from normal processes.  Appearance-wise, nothing has changed in Windows.  I can still boot the machine normally and do all the computing I did before with no ill effect.  But I’m back to square one with all partitions occupied and no room for Ubuntu.  
 
I took the precaution of saving a disk image with Clonezilla before starting this adventure.  Though the computer can run Windows just fine right now, I may choose to find out soon if the stored image can properly restore everything.  Then I’ll have another go at repartitioning the HD to get Ubuntu installed.  However before I do so, can anyone shed some light on what happened and tell me how to avoid the same results?

Thanks for your time,

-Ren

---

### Post by Quackers on 2011-05-10
Did you defragment Windows before you shrunk its C: partition?
If Windows still boots I would recommend that you schedule a chkdsk to be run at next boot (with the fix option checked) and then reboot. In fact, you should keep doing that until no errors are reported.

[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

---

### Post by thinkren on 2011-05-11
Thanks for responding Quackers.  I've since discovered the source of my problem to be something that was completely overlooked.  At some point, I am no longer certain when or how, the hard drive was converted from a basic disk to a dynamic disk.  I don't understand it completely just yet, but dynamic disks can be considered a form of RAID and are much more versatile in certain contexts.  Unfortunately, they are not set up like the familiar basic disks which max out at 4 primary partitions.  It is clear now that Gparted freaked out because it can't find the expected partition table with the expected data.
I am in new territory without a map.  But at least I'm closer to understanding the problem.  This is getting more serious, but I'll try to continue posting if I make any progress.

---

### Post by Quackers on 2011-05-11
Normally the culprit for this is Windows. If you try to create a 5th primary partition on a single disc and there is a Windows system already on that disc, Windows will change the partitions from simple to dynamic disks. This is one cause. 
As far as Windows is concerned it's not too bad.
Sadly, if you are wanting to install another operating system as well it's very bad.
There is a guide or two about for changing them back to simple partitions, but I am uncertain as to the success of that. 
I have seen many more people scrapping everything and starting again - making sure that partitioning after installing Windows does not exceed the maximum of 4 primarys.
Have a look at some of oldfred's posts. He sometimes gives links to guides for this issue.

---

### Post by thinkren on 2011-05-11
the story so far......

After wrestling with the mess of a HD for some time last night, I did make the decision to try and start over.  I was hoping it wouldn't be completely from scratch as I'd used clonezilla to image both the affected partition as well as the whole drive before I started mucking about.  I don't know if the HD at that time had been turned into a dynamic disk yet.  But either way, restoring the image was a no go.  

For some reason, even after I deleted all partitions and had what appeared to be a blank HD, clonezilla still thinks I'm trying to restore the original partition over the one I shrank in size to acomodate the intended Ubuntu install.  Size don't match, blah, blah, try -C to skip checking size (which I can't get to work).  

I ended up restoring from the recovery disks I made prior to dumping the recovery partition.  But I'm still hopeful that I can find some way to restore the C: partion of my original windows.  Otherwise, reinstalling all my post-"factory condition" software would be a painful annoyance.  I very much regret being unable to restore a copy of MATLAB bought last year due to lose of physical media.

---

### Post by Quackers on 2011-05-11
Are you trying to restore partition images with clonezilla, or an image of the whole drive?
I have had problems with restoring clonezilla partition images, but never with disk images.
As you say, it depends on when the images were made as to whether or not they would restore the dynamic disk system.

---

### Post by thinkren on 2011-05-11
I have images of both single partitions as well as the whole drive.  Despite my cautious paranoia, it may turn out to be a moot point.  After further digging, it appears the nails are in the coffin.  Clonezilla's incompatibilty with dynamic disks has been known since 2007.

[http://old.nabble.com/Re%3A-Need-Help-with-DRBL-Clonezilla-errors-p10867368.html](http://old.nabble.com/Re%3A-Need-Help-with-DRBL-Clonezilla-errors-p10867368.html)

A feature request to add support was apparently made in 2008, but so far, it remains open.

[http://sourceforge.net/tracker/?func=detail&aid=2012576&group_id=115473&atid=671653](http://sourceforge.net/tracker/?func=detail&aid=2012576&group_id=115473&atid=671653)

With all that I do have, however, I can't help but still try.  The critical component seem to be a 1mb set of metadata at the end of the disk.  But if that metadata is all that is missing, there might still be a long shot chance that it could be MacGyvered.  The "factory-condition" restore has been successful.  If the metadata from this clean-slated drive can be substituted, perhaps I can cajole the thing piece-by-piece through a combination of clonezilla, dd, or whatever else is necessary.

Furthermore, what information does this metadata contain anyhow?  I do not know yet exactly what clonezilla put in the image I initially created.  But I do believe however that image was created, all my stuff is still intact. I wonder if it is feasible to restore the image created from a dynamic disk to a partition created as a basic disk.  There has to be a way to get the actual files, directories, data out in a coherent way.  I would very much appreciate any help from the community in gaining a better understanding of dynamic disks and clonezilla images.

---

### Post by Quackers on 2011-05-11
AFAIK clonezilla makes a bit by bit copy of all data, including the mbr. If the disk image was made before your partitions were "doctored" by Windows, you should be alright to restore it.
What data are you trying to recover? I thought Windows still booted ok? Or is the data elsewhere?

---

### Post by srs5694 on 2011-05-11
Please run the following command from an Ubuntu install disc in "live CD" mode:

```

fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This won't solve any problems, but it will tell us what you've got. If the results indicate you've got "SFS" partitions, then the disk is a "dynamic disk" and you'll have to fix it. If not, then it's probably been restored to a state that will enable you to install Linux on it. Just don't try to create new partitions in Windows, lest it decide to convert from a "basic disk" to a "dynamic disk" again.

---

### Post by thinkren on 2011-05-11
Remember, I'd said that after wrestling with the dynamic disk all night to no avail, I'd decided to start all over.  This was before I knew that clonezilla couldn't handle dynamic disks.  If I'd been aware of that, I wouldn't have wiped the HD which despite being dyamic could still be booted into Windows.  Although I'm unsure if the images were made before the disks became dynamic, it is leaning that way given the problems I keep experiencing.

Again, having successfully used the set of recovery cd made before said partition was deleted, I can reinstall all my post-factory acquired programs except the very coveted MATLAB.

---

### Post by thinkren on 2011-05-11
Hi srs5694,

There is no mystery as to what I currently have because last night I restored the computer to factory condition.  Perhaps this thread is veering away from the original topic but my priority has changed.  My problem is no longer being unable to install Ubuntu on a dynamic disk.  My objective now is getting all my stuff back from disk/partition images that clonezilla made out of a dynamic disk.

---

### Post by Quackers on 2011-05-11
This guide was done a couple of years ago. It's a bit involved and I didn't manage to follow it through, but many others have got their files back with it.
Good luck
[http://ubuntuforums.org/showthread.php?t=872832](http://ubuntuforums.org/showthread.php?t=872832)

---

