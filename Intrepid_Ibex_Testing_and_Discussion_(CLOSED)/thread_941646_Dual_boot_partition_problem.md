---
title: "Dual boot partition problem"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by unabatedshagie on 2008-10-08
I have a 150gig drive, 50gig of it has windows on it, the other 100gig is to be used for ibex.

When I run the install and get to the partition section I am faced with the attached image.

If I don't change anything and select forward I am told that the partition is too small.

If I select guided - use entire disk or guided - use the largest continuous free space then the windows partition gets removed and the whole drive gets used for ibex.

I don't know what partitions I need in order to use the manual option.

Has anyone came across this problem before and possibly could someone explain what partitions are needed if I was to try the manual option.

---

### Post by Sef on 2008-10-08
Applications > Accessories > Terminal

then type or paste this command:

```
sudo fdisk -l
``` small L

If you are not sure, which partition is which, then post the results here.

---

### Post by Patb on 2008-10-08
Unabated, if you can understand Australian, this guide might be a useful source of background information: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

Post that information Sef asked for as well.  It may enable someone to give you useful help. 

Cheers, Pat.

---

### Post by unabatedshagie on 2008-10-09
Here is the result of the fdisk command```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c00a191

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6710    53889024    7  HPFS/NTFS
ubuntu@ubuntu:~$
```

---

### Post by dabl on 2008-10-09
The entire drive is a Vista partition.

You have to use the Vista partitioning tool to shrink the Vista partition and free up space for Linux.  Then you can boot the Ubuntu CD and install Ubuntu on the freed-up space.  :)

---

### Post by unabatedshagie on 2008-10-09
Not according to vista.

---

### Post by SuperSonic4 on 2008-10-09
> **unabatedshagie said:**
> I have a 150gig drive, 50gig of it has windows on it, the other 100gig is to be used for ibex.

When I run the install and get to the partition section I am faced with the attached image.

If I don't change anything and select forward I am told that the partition is too small.

If I select guided - use entire disk or **guided - use the largest continuous free space** then the windows partition gets removed and the whole drive gets used for ibex.

I don't know what partitions I need in order to use the manual option.

Has anyone came across this problem before and possibly could someone explain what partitions are needed if I was to try the manual option.

Doesn't the bold bit mean it will just use the free space that vista created rather than remove it?

It might help if you format it in vista and just get gparted to reformat in ext3.

Have you backed up any important data? Partitioning can be very dangerous

---

### Post by skyviannes on 2008-10-09
i'm having the same problem he is, and it's not an issue with how the other partitions are formatted.  I've got one windows and one other ubuntu and 8.10 still wants to take up the whole drive if i select the 'largest free space' option.  If anyone has a possible fix for this it would be massivly helpful.  I can't risk seeing if it runs right and just displays wrong because there's things on this computer i can't afford to lose.


Also, the only work-around i know of right now is to install 8.04, which partitions right, then update to 8.10 from that installation.  This comes with it's own set of issues to work out, but beta is beta ^_^

---

### Post by Patb on 2008-10-09
Unabated, all looks good here. You are correct that Vista occupies only the first 50G of the drive. 

Ubuntu installation should be quite straight forward. My suggestion is not to use "guided" partitioning. (I've tried it and never been sure who was guiding who!). Use the manual option instead. That way you can see exactly what partitions you will have before you are committed. 
> 
I don't know what partitions I need in order to use the manual option.
I could go on at length here but it is all covered in [Herman's site]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning"). He has some very pretty illustrations there of various partition setups. Your root partition might take up about 10 Gb out of the 97 Gb you have spare. It is always a good idea to create a separate home partition - makes later updates easier - so do that, perhaps another 50 Gb. Then a swap partition (formatted as "swap") usually located at the end of the drive but I understand it can be anywhere, perhaps 1 Gb. Then you will still have 30+ Gb spare for anything else you want. 

Hope this helps. Cheers, Pat.

Edit PS: I just realised that my suggestions will lock you out of creating any other partitions later on because you cannot have more than 4 primary partitions on one hard drive. There is a simple solution however. During partitioning, create one large "extended" partition out of the whole 97 Gb space. Within this "extended" partition, you can then create many "logical" partitions, including those I have suggested above. Each partition can have its own format. Cheers, Pat.

---

### Post by Keen101 on 2008-10-09
Wow. that sounds like a serious bug in the ibex installer. That could potentially cause massive headaches to new users. Try reporting it as a bug on launchpad. 

I recommend using hardy to install (it's stable, and using largest free space with hardy install should not use the whole disk).

you can then upgrade to ibex later.

---

### Post by Patb on 2008-10-09
> **skyviannes said:**
> i'm having the same problem he is, and it's not an issue with how the other partitions are formatted.  I've got one windows and one other ubuntu and 8.10 still wants to take up the whole drive if i select the 'largest free space' option.
Skyviannes, did you try manual partitioning?

Cheers, Pat.

---

