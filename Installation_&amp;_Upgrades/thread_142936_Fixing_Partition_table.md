---
title: "Fixing Partition table"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by hotpurple on 2006-03-11
Hi,

I have 2 hard disks. One contains Windows XP pro, Windows XP X64, and Ubuntu 5.10. The other has a repository of all my data on it in compressed NTFS format. When I installed Ubuntu, for some reason it overwrote or corrupted the partition table on the second disk with all my data on it. The drive now appears to be unformatted in windows an Gparted. I have tried gpart but that also seems to think the disk is empty. I'm fairly certain the data is still there, but the partition table is corrupt or just not correct. As I know the whole disk is full of 1 single large NTFS partition, is there any way to rewrite the partition table?

Many thanks

Chris

---

### Post by EdZ^2 on 2006-03-11
I have also just had this problem occur. After having to re-install windows, this is just adding insult to iinjury. I can access the partition though the ubuntu live CD, where it shows up correctly as NTFS and at the correct size. Windows shows it as RAW, and at less than half it's size (about half the size of the used portion, in fact).

::EDIT:: When examing the pertition properties, it displays the partition style as 'Master Boot Record'. It also shows this for the drive that windows is on (which *should* be the MBR. The old drive was never the MBR in the old installation). Before re-installing windows, I ran FIXMBR, couldthis have resulted in setting both drives to MBR status, and thus causing the problem?

Additionally, the problem drive shows up as C: (It was F: before), with the new windows drive showing up as F: (And no, I didn't format the wrong disk).

Lastly, [this](http://groups.google.co.uk/group/microsoft.public.win2000.general/browse_frm/thread/1ffd98ffa52d5fab/b0e16a0530c539b3?tvc=1#b0e16a0530c539b3) reccomends I reset the permission under 'Properties\Security\Advanced\Owner', though I have no 'security' tab under properties.

::UPDATE:: Installed the free partition magic trail, and checked for errors. It found 3 'file table mismatches', one 'uppercase table incorrect, File 10 (128), and then 'Cluster crosslinked or not allowed'. It could not fix any of these, and when the 'skip all' button is pressed (usually it will stop on every error detected) it finds too many errors to handle (all of them appear to be the 'cluster crosslinked or not allowed' errors).
It does, however, see the correct size of the disc and identify it as NTFS, though shows it as empty.

---

### Post by hotpurple on 2006-03-12
Well I found a program called EaseUS Recovery Wiazard, which can read my data off the disk in RAW format, and appears to be able to read the files, but not the file names correctly (in that it comes up with FIL0001.mp3 etc.) So if this program can do it, surely there must be a way of getting the partition table to read that there is a 57.2gb NTFS partition on the disk, and to restore all the file names. The data is clearly still there, it just needs a partition table and the location of the MFT I guess.

Chris

---

### Post by OfficeLinebacker on 2006-03-12
I've had a similar situation, and the best I could do was get the FIL0001.mp3, FIL0002.mp3, etc. copied over to another drive, and I was lucky to get that.

---

### Post by hotpurple on 2006-03-12
Well, my openoffice odt files appear to have survived, but the msword files appear to be totally shagged. I think my best bet is still to recover the partition table. Does anyone know how to write one from scratch? I just need a table with 1 ntfs partition in it I think for a 57.25gb drive. I also think it needs to know where the MFT is, which could be more tricky.

Chris

---

### Post by vjones777 on 2006-03-31
There are some tools out there which will attempt to find partitions by looking for characteristic signatures.  I think theres on on the 'ultimate boot CD'.  If you havnt repartitioned the drive before you may have some luck with that approach.  Problems can arise if the drive has been reformatted a few times - the remenants of the deleted partitions will be found and you have to make sure you dont restore those. 
When you get around to reinstalling Linux, I'd suggest recording what your partition table is BEFORE the install.  A good (now freeware) tool for that is PARTINFO by partition magic.   Googling it with 'download' should find it.  You also want to get PTEDIT - you'll need that and your printout of the partinfo info to edit the partition table back.
Its worth doing a bit of reading of Dan Goodalls site on multi-booting.
Best of luck.

---

