---
title: "Increasing my root directory size"
date: 2016-04-16
forum: Installation &amp; Upgrades
---

### Post by Liamdale on 2016-04-16
My Ubuntu OS informs me that I have only 1g of root space left.

I've researched the problem, including this forum and have pieced together the following:

I have a dual boot(ubuntu/Windows) configuration
Ubuntu is on one hard disk and Windows on another

The Ubuntu hard disk has the recommended ubuntu partitions (recommended at the time I set-up the dual boot in 2014)

NTFS        468g with 175g free space (data both accessible with linux and windows
EXT4        20g for the root directory
extended      8g for the swap directory
EXT4      435g for Home directory

process:

1. Backup the root directory using Clonezilla.
2. The NTFS partition has been defragmented using the windows utility.
3. Reduce de NTFS partition by 40g to create an unassigned partition.


The Gpart Diagram of the Ubuntu drive is:
NTFS – EXT4(root)– Swap – EXT4(home)


The free part of the NTFS partition is to the left of the root directory


So if I reduce the partition of the NTFS I should have the freed disk space adjacent to the Root directory


I only have to increase the root directory from 20 to 60g


Is my reasoning correct?

---

### Post by Bucky Ball on 2016-04-16
You are asking if you are going the right way about shrinking the NTFS partition by 20Gb and expanding the Ubuntu / partition into the free, unallocated 20Gb this creates? Then yes, what you have posted looks all good.

You will need to boot to a live session (Ubuntu install media> Try Ubuntu> Gparted) to resize the / partition. That partition needs to be unmounted and you can't do that when it's running the OS.

---

### Post by papibe on 2016-04-16
Hi Liamdale.

Your approach is correct, however, there's catch, and an alternative.

You have to do this using a Live Media, like an USB or a CD/DVD because you can't modify partitions that are being used.

Since you would be reducing the NTFS partition, the safest bet would be to also backup the data on that partition. Usually gparted is pretty safe, but that is what I would do.

If I remember correctly, once you create empty space before the root partition, you may need to first move the partition up, and then increase its size. If that's the case, it would be an extra step.

The UUID of the root partition may change, and you would need to update your /etc/fstab to reflect that.

One alternative would be to either clean as much as possible your root partition, or move some directories, for instance games on /opt, to your home partition and then do a bind mount back to the original place.

Another alternative could be to reduce your /home partition and then move it to the end of the disk, then move swap, and then resize root.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by Liamdale on 2016-04-17
Thanks for the input Papibe and Bucky Ball;

Although I neglected to include the fact that GParted must booted from a live media, I did realize that would be necessary.  I only have a live version of GParted, it is not on my hard disk.

It is the first time I've heard of the UUID.  My preliminary search has uncovered a lot of data to read and absorb.

I will mark this threat as Solved but one further question:
> [COLOR=#000000]once you create empty space before the root partition, you may need to first move the partition up, and then increase its size.[/COLOR]

I assume you mean that the empty partition and the root must be adjacent.

HHD partation (breakdown left to right)

NTFS - Unassigned part. - Root part. - Swap - Home part.

I'll look into cleaning my root directory.

I thought of reducing my Home directory but quickly discarded that because the NTFS directory is the partition the least used of all my partitions and the Home the most used.

I don't know if this is important to the forum but when I'm finished (and successful) I'll write up my detailed procedure I used (including any unforeseen problems)

---

### Post by Bucky Ball on 2016-04-17
> **Liamdale said:**
> I don't know if this is important to the forum but when I'm finished (and successful) I'll write up my detailed procedure I used (including any unforeseen problems)

Yes, it is important to the forum and is considered forum etiquette to do so here. Thanking you and good luck. :)

---

### Post by jay_bowles2 on 2016-04-17
Just to add my little bit of advice... The above is all good. However there may be a safer way in reducing your windows partition. That is to use windows own tools. Unfortunately I can't remember where they are in the settings but they are provided out of the box in at least Windows 10. Having used them I can say that it worked a charm and is recommended by windows experts I have spoken to. Anyway worth a look maybe before committing. I have also used Gparted and it is good and you will be able to expand change your Linux partitions which windows partitioner can't do.

---

### Post by Bucky Ball on 2016-04-17
> **jay_bowles2 said:**
> Just to add my little bit of advice... The above is all good. However there may be a safer way in reducing your windows partition. That is to use windows own tools. Unfortunately I can't remember where they are in the settings but they are provided out of the box in at least Windows 10. Having used them I can say that it worked a charm and is recommended by windows experts I have spoken to.

Agreed, but if you read the OP's first post you'll find that the NTFS partition they're shrinking is a data partition and their Windows partition is on a completely different drive. ;)

But yes, note well: Always shrink the Windows partition with Windows software, NOT Gparted.

---

### Post by Liamdale on 2016-06-16
[I]2nd time I'm posting this.  Don't know what I did with the first post but it seems non-existent.

[/I]I posted that once I had successfully resized my Root directory the process I used would be posted.

What had to be done:

[LIST]
[*]An existing partition had to be reduced to create an unallocated partition
[/LIST]



[LIST]
[*]Backup up the target Partition to be reduced
[/LIST]



[LIST]
[*]Backup the root directory using Clonezilla.
[/LIST]



[LIST]
[*]Defragment the NTFS partition (partition to be reduced) with the windows utility.
[/LIST]



[LIST]
[*]Reduce de NTFS partition by 60Gb to create an unassigned partition.  Used GParted.
[/LIST]


***Note: I have dual boot but when I set-up the dual boot originally, I chose place windows on one hard disk and Linux (Ubuntu) on another.***


The Gpart Diagram of the Ubuntu drive is:
NTFS – EXT4(root)– Swap – EXT4(home)


The free part of the NTFS partition is to the left of the root directory



[LIST]
[*]So I reduced the partition of the NTFS  by 60Gb in such a way to have the available disk space adjacent to the Root directory.
[/LIST]



[LIST]
[*]I only had to increase the root directory from 20 to 80Gb.
[/LIST]


The entire process went off without a hitch.

I reBooted and voila Ubuntu booted and the disk analyser reported 80Gb


The process although a little involved is relatively easy.

---

