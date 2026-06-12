---
title: "Dual boot, laptop came with all 4 primary partitions used"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by nickasummers on 2012-07-26
I was attempting to dual boot win7 and linux on my laptop. When i shrunk the win7 partition the extra space was marked "unusable". After a quick search i realized this is because this laptop has 4 primary partitions in use already and cant have more. Is there any good way to deal with this? I am afraid to just delete one, not sure what it would do.

The four partitions are
SYSTEM (boot stuff i think)
500gb filesystem
Recovery (im assuming this is just the stuff to do a factory reset?)
HP_TOOLS (no idea what this is)

---

### Post by dino99 on 2012-07-26
> **nickasummers said:**
> 
The four partitions are
SYSTEM (boot stuff i think)
500gb filesystem
Recovery (im assuming this is just the stuff to do a factory reset?)
HP_TOOLS (no idea what this is)

*** you says :  i think, im assuming, no idea ****

and what you think we can answer with such comments ?

you surely can help yourself i suppose, by browsing these partitions, and backup/move up/erasing etc what you dont care.

---

### Post by Ubun2to on 2012-07-26
Screenshot of GParted, please.
SYSTEM-the Windows boot partition. Want to boot to Windows? Keep this partition.
500 GB FS-most likely Windows, as when the manufacturer ships the PC, they give the majority of the space to Windows, and usually there is some unallocated space.
RECOVERY-this is the factory image partition. If something goes bad in Windows, this restores it with all the original drivers, Windows files, bloatware, and free antivirus trials.
HP_TOOLS-I haven't come across this partition on my HP machine, but I'm pretty sure that would be for things like data recovery. But, that's just a guess.
You can delete HP_TOOLS, as they are not OS files (although you probably should email HP and ask them what it's used for before you do it-I'm not sure what it contains, and you should decide if you feel like going without them), and you might want to delete the RECOVERY partition, if you feel comfortable with not having the factory image in case your Windows ship begins to sink. But, the factory image will wipe your hard drive if you use it-those things wipe out everything so there are no viruses (or whatever caused your problems) remain on the system.

---

### Post by Mark Phelps on 2012-07-26
Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Finnicella on 2012-07-26
I have an hp and I deleted the HP Tools partition after saving the internal files. Now it work with Ubuntu and windows very well.
Sorry for my english.

---

