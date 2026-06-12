---
title: "Help Partion"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by dark_nano on 2007-06-27
I have an 71.2GB HDD and I wanted to install ubuntu on it. So I have 15 gb of it used up and have 56.2GB left. When I try to partion (dual noot using alternate install) It says that for an unknown reason it cant resize the disk. I am trying to resize disk from 71.2 to 56.2 so I have a 2gb swap and a 13gb root. but it wont let me resize (it is filesystem ntfs)

---

### Post by merlinus on 2007-06-27
If you are using vista, you must use its disk manager to shrink your windows partition.

-merlin

---

### Post by dark_nano on 2007-06-27
im on xp I hate vista

---

### Post by merlinus on 2007-06-27
Did you defrag xp several times first?  This can help with the re-sizing.

-merlin

---

### Post by dark_nano on 2007-06-27
i have defraged but it jst tells me it cant resize or can that be caused by not defragging?

---

### Post by merlinus on 2007-06-27
You might have better luck with the gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It is an updated version from the one on the ubuntu install cds.

-merlin

---

### Post by dark_nano on 2007-06-27
thank you ill post here if it doesnt work

---

### Post by dark_nano on 2007-06-27
I ran gparted and it didnt work it told me i had to run chkdsk
I ran chkdsk and it told me it found an error so i did chkdsk /F
it fixed it and i booted into gparted and again it told me to use chkdsk

should i defragment repeat then chkdsk then try again

and when i do partion do i just leave as free space and assign as swap and root on install or just do it with gparted

---

### Post by merlinus on 2007-06-27
Try defragging again a few times, run chkdsk c: /f and then see if gparted live can re-size the partition.

You can make the ubuntu partitions with gparted, or do it whilst installing.  In any event, you will still have to specify the mount points, / and /swap, during installation.

-merlin

---

### Post by dark_nano on 2007-06-27
thank you ill try that and get back

---

### Post by dark_nano on 2007-06-28
I defraged and it went fine then I ran chkdsk and got this
CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage
Security descriptor verification completed.
CHKDSK is verifying Usn Journal...
Usn Journal verification completed.
CHKDSK discovered free space marked as allocate
master file table (MFT) bitmap.
Correcting errors in the Volume Bitmap.
Windows found problems with the file system.
Run CHKDSK with the /F (fix) option to correct

  74686184 KB total disk space.
  17030980 KB in 86542 files.
     32000 KB in 7305 indexes.
         0 KB in bad sectors.
    266768 KB in use by the system.
     65536 KB occupied by the log file.
  57356436 KB available on disk.

      4096 bytes in each allocation unit.
  18671546 total allocation units on disk.
  14339109 allocation units available on disk.


so i did as it said and ran chkdsk c: /F and rebooted and ran chkdsk (read only mode) and got the same message that there is an error and i still cannot partion

---

### Post by dark_nano on 2007-06-28
i checked defrag and it said 0% file fragmention

---

### Post by stchman on 2007-06-28
> **dark_nano said:**
> I have an 71.2GB HDD and I wanted to install ubuntu on it. So I have 15 gb of it used up and have 56.2GB left. When I try to partion (dual noot using alternate install) It says that for an unknown reason it cant resize the disk. I am trying to resize disk from 71.2 to 56.2 so I have a 2gb swap and a 13gb root. but it wont let me resize (it is filesystem ntfs)

You need to run a chkdsk /f on your NTFS partitions.  Once you do that and a defrag you can resize them.

---

### Post by dark_nano on 2007-06-28
i have but evem then it wont let me

---

### Post by stchman on 2007-06-29
> **dark_nano said:**
> i have but evem then it wont let me

Does the chkdsk /f ask you to schedule the check for the next time you boot up?

---

