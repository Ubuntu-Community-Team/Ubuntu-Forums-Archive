---
title: "3 partitions on extension"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2006-09-23
Hello: I'm installing 6.06 on a Compaq laptop.
I have Windows XP installed on the primary partition.
And a FAT32 extended partition. At the "Prepare Disk Space" screen,
I have selected "Manually Edit Partition Table".
Upon that selection, I am presented with the "Prepare Partitions"
screen.

Three partitions were displayed (as I would expect)
/dev/hda1     NTFS ...
/dev/hda2     Extended ..... 28 G
   /dev/hda5  FAT32
:( 
Unhappily the situation has been complicated unexpectedly. It appears
that ubuntu has deallocated about half of the hda5 partition. I don't
want this arrangement.

Here is what I wish to:
Use all of hda2 for my ubuntu installation, 
  --leaving hda1 alone for a dual boot arrangement with windows
Have 3 partitions of hda2:
  /home
  / (root)
  / swap
How do I proceed from here?
thanks
tim

---

### Post by K.Mandla on 2006-09-23
I think if you ...

[LIST=1]
[*]Boot Ubuntu to the partitioner
[*]Manually edit the partition
[*]Select hda2
[*]Choose delete this partition
[/LIST]
That should free up the space and mark it as unpartitioned. From there you can draw up your own partition configuration or you could (probably) use guided partitioning and let the partitioner detect that space.

Let us know if that helps. It's kind of an odd thing to visualize. ... :)

---

### Post by tim042849 on 2006-09-23
Thanks! I'll try that. Didn't expect such a quick reply.
Won't get to it 'til tomorrow.
stay tuned.
cheers
tim

---

### Post by tim042849 on 2006-09-24
> **K.Mandla said:**
> I think if you ...

[LIST=1]
[*]Boot Ubuntu to the partitioner
[*]Manually edit the partition
[*]Select hda2
[*]Choose delete this partition
[/LIST]
That should free up the space and mark it as unpartitioned. From there you can draw up your own partition configuration or you could (probably) use guided partitioning and let the partitioner detect that space.

Let us know if that helps. It's kind of an odd thing to visualize. ... :)
No success. Here's what happens:
I choose to delete the partition. OK some progress bar activity, then
the screen is refreshed to "Prepare Mount Points"
      With *only* hda1 presented.
If I go "back" to "Prepare Partitions" I can highlight the unallocated
space and choose "New" from the menu. A "Create New Partitions" Dialogue
comes up. 
After some activity, I am taken forward to "Prepare Mount Points". Again,
only hda1 is shown. 
I go back to "Prepare Partitions". 
Choose the unallocated space under hda2. 
Choose "Create Logical Partition" with ext3 as filesystem. 
Some activity, then screen refreshed again to
"Prepare Mount Points", hda1 only. 
Go Back to "Prepare Partitions". 
Now I see a hda5 extension, *but* the filesystem is tagged as "Unknown".
If I pick either hda2 or hda5 and go "forward" to "Prepare Mount Points",
only hda1 is presented.

I'm inclined to "Go back to the Drawing Board" and use windows to
repartition and format. Perhaps it is better to add the unallocated
space to the NTFS partition, because it might be that Ubuntu "Understands" 
the "Resize" option better.
tim

---

