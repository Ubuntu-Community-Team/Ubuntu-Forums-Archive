---
title: "Resize Operation Failure"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by xX-Felipao-Xx on 2008-10-13
Hi guys, this is my first thread, as I'm new in the forum, so I hope to be lucky here :)

Well, I have an unique HD with an unique Primary Partition (Windows XP), which works good.
My plan, is to resize this NTFS partition up to leaving 15GB for Ubuntu (my HD capacity is 80GB).
So, in the installation, I selected Manual , resized the NTFS partition (set as 65.000 MBs) and press OK (or whatever to continue, dont remember).

Then, a message appears that the changes should be saved before continuing, so I accept that, and starts "Applying the changes" or processing, where stays at 0% for a few seconds, and then, the following error message appears:

[I]Resize Operation Failure

An error occurred while the changes to the storage devices.

The resize operation has been aborted[/I]

I tryied resizing with PQMagic (PartitionMagic), and an error is annoying there too.
I tryied defragging a few times too, and then, nothing (as I saw some answers in this forum)

And maybe is useful to mention that I've done this before in this same PC, and I've tryied with 8.04 and 7.10 version, and I get the same error.

What can I do? 

Thanks everybody :)

---

### Post by bogdan_mbe on 2008-10-17
hello,

considering that i've just solved a similar problem, i think it would be nice to write in all the similar threads i've found my solution. from the beginning i must add i was using a windows vista, on a single hdd notebook, and i was trying to install the latest lts ubuntu (8.04).

i was suggested to try to resize partitions with a third party software like gparted live, and i did. i burned a bootable cd of it and used successfully to set my partitions just the way i wanted them.

also i've tried to defrag partitions several times, but it didn't work.

so, for me gparted live was the answer.

---

