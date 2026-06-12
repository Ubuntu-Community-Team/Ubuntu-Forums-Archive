---
title: "Is there a way to undo mkswap?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by clypp on 2007-01-11
In an attempt to fix a missing swap signature I made my Ubuntu partition a swap using the mkswap command.  I have since rebooted the computer and GRUB is broken too.  Is there anyway to change this back to ext3? 

I have loaded the live CD and in GParted I see two swap partitions (the real one and a large one that was my Ubuntu partition.)  If I format to ext3 here all my data will be lost, correct? Is there a mkext3 command to set things right?

---

### Post by clypp on 2007-01-11
Up once before I reformat.

Please help with suggestions, even if only to recover some data.

---

### Post by louieb on 2007-01-11
seen one of the moderators of this forum suggest[ testdisk]("http://www.cgsecurity.org/wiki/TestDisk") several times. Hope it works for you.

---

### Post by meng on 2007-01-11
> **clypp said:**
> In an attempt to fix a missing swap signature I made my Ubuntu partition a swap using the mkswap command.  I have since rebooted the computer and GRUB is broken too.  Is there anyway to change this back to ext3? 

I have loaded the live CD and in GParted I see two swap partitions (the real one and a large one that was my Ubuntu partition.)  If I format to ext3 here all my data will be lost, correct? Is there a mkext3 command to set things right?
mkswap formats a partition as a swap partition.
mke2fs -j formats a partition as an ext3 partition.
Whenever you format, you lose any data on that partition. It is a tricky business to recover data from a partition that has been formatted.

---

### Post by clypp on 2007-01-11
I'm hoping for the best wrt data.

I'm in testdisk, got it running OK and I'm trying the convert option.  I selected the correct partition and what to switch it to ext3 however it is not listed.  The list has everything else under the sun such as 4 versions of FAT16 and FAT32, Amoeba, OnTrack, etc, etc.  Is ext3 sometimes called a different name perhaps?

EDIT: There is a "Linux" and a "Linux LVM" listed.  Is this the correct format?

---

### Post by Sef on 2007-01-11
> EDIT: There is a "Linux" and a "Linux LVM" listed. Is this the correct format?

Use Linux.  That would likely be ext3.

---

### Post by clypp on 2007-01-11
Likely?

OK, you have over 4600 posts.  I'll trust your word.:)

***Does it - seems to work***

My GRUB is broken, error 17, "Does not recognize format"

I suppose GRUB can be reinstalled or corrected somehow. I will check my data with the Live CD now.

EDIT: It didn't take.  After reboot hda4 is back to being a swap

Now to try meng's solution...

---

### Post by clypp on 2007-01-11
It did something! Recreated some stuff and took about 15 seconds to complete.

Now on boot I get error 15 from the GRUB rather than error 17. "This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK."

Looks like I have to repair the GRUB .conf file or something. This could be bad...

EDIT:
Back on the old Live CD I mounted the newly found harddrive. /mount/hda4 came out to have a file(?) called Lost+Found which I could not access.  Since I cannot access it I cannot try fix the Grub and this is all likely a moot point anyway.  I think I will try to recover my documents with PhotoRec and reformat.  I wont do the reformat today though so if you have a clever idea on how I could fix things...;)

EDIT2(no need to bump right now):
PhotoRec did not help, recovered files were limited by RAM size.  I did however run TestDisk again and I clear the MBR with the TestDisk version.  I can now boot into XP which should help me get some use from the machine and allow me to use the windows version of recovery software which does not have the annoying permissions that the Live CD has.

---

### Post by kolesarm on 2007-02-24
clypp, how did the data recovery go?

I have the [same problem]("http://www.ubuntuforums.org/showthread.php?t=366912"), basically ran mkswap on my root partition, not swap partition.

I managed to dd an image of the partition, reinstall ubuntu on a different partition, and now I'm in the process of recovering the data. testdisk nor photorec didn't help, but foremost managed to recover most of my images. It's the LaTeX text files I had there i'm worried about the most, but so far no success with them:(

---

