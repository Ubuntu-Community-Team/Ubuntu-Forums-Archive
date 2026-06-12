---
title: "Ubuntu 9.04 won't install side-by-side with SuSE 11.1"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by socref on 2010-04-17
Hello, everyone.

I have SuSE 11.1 installed on my pooter. The / partition is 20 GB.

I would like to add Ubuntu 9.04 (factory disk) to the computer so I can select SuSE or Ubuntu on start up.

So I put the Ubuntu disk into the drive and clicked until I was given three options:

1) add Ubuntu side-by-side with SuSE (of the 20GB /dev/sda1 partition it indicated 2.5GB would be allocated to Ubuntu),

2) use the entire disk for Ubuntu,

3) Repartition (advanced).

So I selected the first option since that seemed best for someone not very sophisticated in the magic of all this.

When I clicked to proceed after a bit an error box came up that said:

"Resize Operation Failure"

"An error occurred while writing the changes to the storage devices. The resize operation has been aborted."

I tried multiple times but got the same error each time.

I looked at option #3 but could not figure out what to do there to accomplish the same thing as option #1.

Your help is appreciated. Seems that option #1 should be a simple process, but I'm just not having any luck with it.

Thx
socref

---

### Post by ajgreeny on 2010-04-17
You will struggle if you only have 2.5GB for ubuntu, and find that you can do nothing with it because there is not enough room for any new files etc etc.  I think a new installation takes about 2.6 GB, from memory, though that me be slightly wrong, however, 2.5 is definitely not enough.

If that is all the room you can really afford, then either you will need to re-assess you partitioning, or you will have to choose a much smaller OS than ubuntu to try.

Just for clarification, can you attach the output from suse of ```
fdisk -l
``` from a root terminal, or use the live ubuntu CD and run ```
sudo fdisk -l
```in terminal.  From the live CD it would also be useful to see a gparted screenshot, which will give a full picture of what is on disk already.  Open gparted in live CD and hit Alt+PrintScreen, and still using the live CD attach that .png to a new post here by using the paperclip in the text entry box.

---

### Post by socref on 2010-04-17
> **ajgreeny said:**
> You will struggle if you only have 2.5GB for ubuntu, and find that you can do nothing with it because there is not enough room for any new files etc etc.  I think a new installation takes about 2.6 GB, from memory, though that me be slightly wrong, however, 2.5 is definitely not enough.

If that is all the room you can really afford, then either you will need to re-assess you partitioning, or you will have to choose a much smaller OS than ubuntu to try.

Just for clarification, can you attach the output from suse of ```
fdisk -l
``` from a root terminal, or use the live ubuntu CD and run ```
sudo fdisk -l
```in terminal.  From the live CD it would also be useful to see a gparted screenshot, which will give a full picture of what is on disk already.  Open gparted in live CD and hit Alt+PrintScreen, and still using the live CD attach that .png to a new post here by using the paperclip in the text entry box.


Hello. Thx. for reply. The reference to 2.5GB for Ubuntu was not something I chose. That is what Ubuntu told me it was allocating from the 20GB already set aside for the SuSE / partition. I tried to figure out how to use the repartitioning option (choice #3) in the Ubuntu install program, but I can't figure it out.

Attached is the screen shot you requested (taken using gparted in SuSE). Hope it's clear enough to read. 

Note that this is a fresh install of SuSE, so the pooter is almost virgin. I have LOTS of room on it, but I can't figure out how to repartition the drive to give me space to add Ubuntu. That is why I chose the "side-by-side" install option. I figured Ubuntu was smart enough to do it.

Finally,  here is the output you asked for from fdisk -l

phred:/home/gil # fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d344f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        2611    20964825   83  Linux
/dev/sda2            2612        2872     2096482+  82  Linux swap / Solaris
/dev/sda3            2873       60801   465314692+  83  Linux
phred:/home/gil #

Thanks for your assistance.
socref

---

### Post by ajgreeny on 2010-04-18
You appear to have 20GB for Suse root partition at the moment, and a huge /home partition for it of nearly 444GB.

I think the simplest way is to use gparted from the live CD before you do the installation of ubuntu to shrink your Suse root partition to about 10GB, leaving about another 10 unallocated into which you can install ubuntu's root partition.  You will not be able to safely share the /home partition between the two OSs, so I suggest you backup all your data files from Suse, shrink the current Suse /home and then make two new partitions, one for the new ubuntu /home and one large one for all your data files.  make each /home partition about 10GB; that should be plenty as you will not put any data in either of them in future, onlythe configuration folders and files from each OS.

You will not need another swap partition, as that can be shared, as long as you do not hibernate one OS then boot to the other, all should be OK.

I hope that makes sense;  making the partitions before you install can make the whole business less confusing when you do the manual partitioning option, and is the way I always do it now.

---

### Post by socref on 2010-04-18
> **ajgreeny said:**
> You appear to have 20GB for Suse root partition at the moment, and a huge /home partition for it of nearly 444GB.

I think the simplest way is to use gparted from the live CD before you do the installation of ubuntu to shrink your Suse root partition to about 10GB, leaving about another 10 unallocated into which you can install ubuntu's root partition.  You will not be able to safely share the /home partition between the two OSs, so I suggest you backup all your data files from Suse, shrink the current Suse /home and then make two new partitions, one for the new ubuntu /home and one large one for all your data files.  make each /home partition about 10GB; that should be plenty as you will not put any data in either of them in future, onlythe configuration folders and files from each OS.

You will not need another swap partition, as that can be shared, as long as you do not hibernate one OS then boot to the other, all should be OK.

I hope that makes sense;  making the partitions before you install can make the whole business less confusing when you do the manual partitioning option, and is the way I always do it now.

Thanks, I appreciate the help, but I am confused. Please clarify:

1) You suggest shrinking the the 20GB SuSE / partition using gparted. I could not figure out how to use gparted. It is not intuitive.

2) You suggest making two 10GB partitions, one for each of the two OS, but you describe that as two /home partitions rather than two / partitions. I don't understand.

3) Once I understand what you're suggesting will I end up with two (2) / partitions, one SuSe and one Ubuntu, one (shared) swap partition, and one shared /home partition, or will I end up with two /home partitions, one for each OS?

I would love do the partitioning with gparted. If you could provide some concise instructions that would be wonderful.
Thx
socref

---

### Post by socref on 2010-04-21
Any help on using gparted to resize my SuSE partition and allow me to install Ubuntu side-by-side?

Thx
socref

---

### Post by socref on 2010-04-30
AJGreeny (or anyone else), can you help?

Thx
socref

---

