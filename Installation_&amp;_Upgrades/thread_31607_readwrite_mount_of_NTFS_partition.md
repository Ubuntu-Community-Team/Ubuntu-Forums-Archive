---
title: "read/write mount of NTFS partition"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by vinthund on 2005-05-03
hello,

As far as I could read at the forum it is impossible for Ubunu (or Linux generally) to write at such partition, right? Or is it possible byt risky/not recommended? Whai is the risk then?

And what is "libntfs5" package?

regards

vinthund

---

### Post by heimo on 2005-05-03
You can compile kernel with NTFS write support, but there's still limitations.

> The only supported operation is overwriting existing files, without
changing the file length.  No file or directory creation, deletion or
renaming is possible.  Note only non-resident files can be written to
so you may find that some very small files (<500 bytes or so) cannot
be written to.

While we cannot guarantee that it will not damage any data, we have
so far not received a single report where the driver would have
damaged someones data so we assume it is perfectly safe to use.

Note:  While write support is safe in this version (a rewrite from
scratch of the NTFS support), it should be noted that the old NTFS
write support, included in Linux 2.5.10 and before (since 1997),
is not safe.

---

### Post by hoeken_ on 2005-05-04
How do I mount a NTFS drive?
I just want to read from it...

---

### Post by vinthund on 2005-05-04
[QUOTE=hoeken_]How do I mount a NTFS drive?
I just want to read from it...[/QUOTE]
 [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

have a look, this should work fine

vinthund

---

### Post by vinthund on 2005-05-04
[QUOTE=heimo]You can compile kernel with NTFS write support, but there's still limitations.[/QUOTE]


So, according to your quote, not much can be done? Well, actually hardly anything, right? Surely it is not possoble to make amule incoming and incomplete directories there?

vin

---

### Post by Gandalf on 2005-05-04
[QUOTE=vinthund]So, according to your quote, not much can be done? Well, actually hardly anything, right? Surely it is not possoble to make amule incoming and incomplete directories there?

vin[/QUOTE]
 nope that is not possible, and i don't advise you to mount NTFS as rw this could be dangerous for the drive itself, you have been warned!

---

### Post by heimo on 2005-05-04
I second Gandalf. I think it's common to use FAT32 partition to exchange data between dualboot Linux and Windows.

---

### Post by mohaham on 2005-05-04
yes, thats how i do it too..i use FAT32 to exchange data between Linux and Windoze..

---

### Post by hoeken_ on 2005-05-05
Well, my problem is that I can't create a FAT32 partition, Windows doesn't wanna format it unless it's NTFS....

---

### Post by rpgcyco on 2005-05-05
Partition Magic can create FAT32 partitions for you in Windows, though it costs money.

However, I think the free Linux tool GParted, can create FAT32 partitions. Haven't tried it myself. [http://www.ubuntuguide.org/#gparted](http://www.ubuntuguide.org/#gparted)

- Rpg Cyco

---

### Post by hoeken_ on 2005-05-05
[QUOTE=rpgcyco]Partition Magic can create FAT32 partitions for you in Windows, though it costs money.

However, I think the free Linux tool GParted, can create FAT32 partitions. Haven't tried it myself. [http://www.ubuntuguide.org/#gparted](http://www.ubuntuguide.org/#gparted)

- Rpg Cyco[/QUOTE]

I have tried Partition Magic...
The thing is that even though I create a FAT32 partition there, it still appears like an unformated drive in My Computer, and Windows asks me to format it.
I have tried to boot from the Windows CD as well, but even there I can only choose NTFS.

---

### Post by DaveH on 2005-05-05
Haven't used windows for a while :) 

However - I think the way to give a partition a drive letter in XP/2000, is to go into disk management. It's in Control Panel --> Administration tools --> Disk management. Then right click the partition and give it a letter. 

I *think* this is what you're after...
Ugh, Windows - I feel sullied.

Cheers
Dave

---

### Post by hoeken_ on 2005-05-05
[QUOTE=DaveH]Haven't used windows for a while :) 

However - I think the way to give a partition a drive letter in XP/2000, is to go into disk management. It's in Control Panel --> Administration tools --> Disk management. Then right click the partition and give it a letter. 

I *think* this is what you're after...
Ugh, Windows - I feel sullied.

Cheers
Dave[/QUOTE]

No it's not that.
The disk appears in my computer under a drive letter, but Windows tells me it's not formatted, even though I have formatted it in Partition Magic.

---

