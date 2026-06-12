---
title: "Mistakingly changed my main NTFS partition to EXT4. Data gone?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by docarchy on 2011-01-06
I was installing ubuntu 10.10 and in the advanced partitioning screen, I was trying to resize my 500GB SATA partition (on my laptop) to make space for ubuntu. I selected the biggest partition (C Drive), selected to change it, entered the new size (which was 15 GB less), selected ext4 as the file system and selected it to be my root /.

After clicking past the warnings that this can't be undone (if only I knew I was doing the wrong thing) I saw the ntfs partition changed to ext4, with the Format option checked. *bang head against desk here*

I don't believe the changing of the file system formatted the partition, did it?

I would like to know if using the same ubuntu partition tool (or some other partition manager) and changing the file system back to NTFS would restore my files.

Or will I need to use data recovery tools to retrieve the data?

Thanks for any help.

---

### Post by Bucky Ball on 2011-01-06
> **docarchy said:**
> 

I don't believe the changing of the file system formatted the partition, did it?

I would like to know if using the same ubuntu partition tool (or some other partition manager) and changing the file system back to NTFS would restore my files.

Or will I need to use data recovery tools to retrieve the data?

Thanks for any help.

Partition has been reformatted, changing it back to NTFS will not restore files, recovery tools won't recover data after changing file format on the partition twice (although you could dig around and try to prove me wrong). Shame you don't have a backup.

:(

---

### Post by docarchy on 2011-01-06
Really? After changing a partition from NTFS to ext4 the data cannot be recovered? Seriously?

Oh, I just realized that the checked box under the Format column meant that partition was formatted. Ok. I see what you're saying.
Guess I'll still give it a shot with the various recovery tools out there.

I have a backup...just didn't do a recent one right before I tried this. :(

---

### Post by presence1960 on 2011-01-06
From ubuntu open a terminal and run ```
sudo apt-get install testdisk
```
After that completes in terminal run ```
sudo testdisk
``` & follow [this]("http://www.cgsecurity.org/wiki/Running_TestDisk")
If your OS hasn't made to many write operations to the affected partition you may be able to recover the partition.

---

### Post by Bucky Ball on 2011-01-07
Just thinking about it, when formatted normally guess it doesn't overwrite the disk with zeros, just marks as 'writable' so there is a chance, as suggested by Presence. But as they hint at, if you've saved anything onto the drive that would have overwritten some of your old data (perhaps).

---

### Post by docarchy on 2011-01-07
Nothing else has been written to the drive. After I saw my mistake, I quit the installer and it brought me back to the live cd desktop. I shut down the laptop and pulled the hard drive out.

I'll try precense's suggestion and also the few gui recovery tools.

Thanks guys.

---

### Post by docarchy on 2011-01-08
I used testdisk but it wasn't working exactly how I wanted it. I needed to find deleted files without the recovery tool looking at the type of file system the partition currently had.

Fortunately, testdisk also has a sister tool called PhotoRec (from the same link presence posted above) that does just that. I recovered my files and formatted the partition as NTFS and reinstalled that "other" OS.

I left 15GB of space at the end of the drive so I can try installing Ubuntu again soon. Hopefully I won't see a repeat of this.

Thanks again guys for the help.

---

### Post by presence1960 on 2011-01-08
> **docarchy said:**
> I used testdisk but it wasn't working exactly how I wanted it. I needed to find deleted files without the recovery tool looking at the type of file system the partition currently had.

Fortunately, testdisk also has a sister tool called PhotoRec (from the same link presence posted above) that does just that. I recovered my files and formatted the partition as NTFS and reinstalled that "other" OS.

I left 15GB of space at the end of the drive so I can try installing Ubuntu again soon. Hopefully I won't see a repeat of this.

Thanks again guys for the help.

Excellent! Glad you got your data back.

---

### Post by Bucky Ball on 2011-01-08
Fantastic. 15Gb is a bit small for Ubuntu though but you should be able to squeeze it on there. Perhaps keep your personal files on an NTFS partition rather than using folders in your Home. That will fill up and you'll find yourself out of space. 

Generally, folks make an NTFS data partition that can be shared between the two OSs.

---

### Post by docarchy on 2011-01-08
Yeah, many of the apps and any large files I have I keep on my networked 300GB NTFS drive. Ubuntu is just to play around with, like surfing and listening to music (which is on my networked HD). So won't be storing anything large on it.

---

