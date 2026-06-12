---
title: "Resizing pre-existing partition"
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by S{yndrom}e on 2006-05-23
Hi I was wondering if i could resisze existing partitions. When i first installed ubuntu, i was skeptical at first, and so installed it with a dual boot config with Windows XP. At the partition table in the installer i gave ubuntu a meager 20GB in total. Now that i got the hang of ubuntu i love it so much i was wondering wiether i could resize the partitions or something to give my ubuntu partition more space, but at the same time not having to reinstall everything on ubuntu.

Thank you in advance

---

### Post by aysiu on 2006-05-23
You can add to the end (right side) of a partition but not to the beginning (left side of it).

Likewise, you can shrink only from the right side.

---

### Post by S{yndrom}e on 2006-05-23
So any recomended readin i should do, or a program i could use to do this?

Thanks again!

---

### Post by aysiu on 2006-05-23
[QUOTE=S{yndrom}e]So any recomended readin i should do, or a program i could use to do this?

Thanks again![/QUOTE] For partition planning, you might want to take a look at this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

For a good program, try [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

DiskDrake has never failed me, but it does entail downloading another distribution. GParted with *ntfsprogs* and QTParted should theoretically also work.

---

### Post by S{yndrom}e on 2006-05-24
k i downloaded gparted and ran it. Unfortuantly, remeber you said you can't reformat partitions from the begining? Well my ubuntu partition is at the end =(

Anyway to fix this?

Also i can post  a screenie if u want.

---

### Post by S{yndrom}e on 2006-05-24
here is a screenie

---

### Post by az on 2006-05-24
If you can remove some stuff from hda1, you can shrink it, to create some space (greater than the size of your linux partition) and then copy your linux partition there.  Then, delete the original and extend the copied partition to fill the free space.

After all is said and done, your partition names should not be changed and you should be fine.  At worst, you may need to edit /etc/fstab and /boot/grub/menu.list to accommodate a hane change, if you funk around with extended partition and end up remaning your partition to something different.

---

### Post by S{yndrom}e on 2006-05-24
thanks will try now.

---

### Post by S{yndrom}e on 2006-05-24
I deleted Hda1 as you said but i the copy option for hda4, my ext3 linux partitions is greyed out.

---

### Post by Mustard on 2006-05-24
I'm not sure you followed the instructions given by Azz, which would be unfortunate, except that you haven't actually applied the changes yet, so you can still undo at this stage and save yourself from making a mistake.  I suggest you read the instructions given by Azz more carefully, and this time when you do it, remember to 'Apply' the changes after you have made them.

The instructions didnt say to remove hda1, but to shrink it to a size that created sufficient free space that you could move your linux partition to that free space.  This may entail going into the hda1 partition and deleting some files so as to allow the partition to be shrunk sufficiently to provide the necessary free space.

---

### Post by S{yndrom}e on 2006-05-24
still, its not that that is not working, it is that the "copy" function of the ext3 partition that is grayed out, meaning it that it cannot be selected.

---

### Post by Mustard on 2006-05-24
[QUOTE=S{yndrom}e]still, its not that that is not working, it is that the "copy" function of the ext3 partition that is grayed out, meaning it that it cannot be selected.[/QUOTE]

The copy function is greyed out because you have only told gparted what you intend to do, and they are still just 'pending tasks'.  You won't be able to copy until such a time as you 'apply' these pending tasks.  The way you are currently doing it, it is going to wipe all data on hda1.  If this is a suitable result for you then you should do it, but its not what Azz suggested.  His suggestion allowed you to retain your hda1 partition with the data intact.

After you 'apply' the changes, you will then have irrevocably changed hda1 to free space, and this will allow gparted to do the next step in the process, which would be to move the partition to the free space.

Think of it like a puzzle game, in which you have to move blocks around in a confined space, without losing any blocks.  Some blocks can be shrunk, but only so much.  The trick is to shrink the blocks sufficiently that it makes enough space for another block to moved to the free space. :)

---

### Post by S{yndrom}e on 2006-05-24
Ah I am Sorry, I see what you mean now. Just one more question, if i do resize hda1 (not delete) and paste my ext3 partition, how i will move my swap partition over, or does it not matter? And if i do decide to move it, will this have a major effect on my system? Once again thank and so sorry for taking your time.

---

### Post by Mustard on 2006-05-24
[QUOTE=S{yndrom}e]Ah I am Sorry, I see what you mean now. Just one more question, if i do resize hda1 (not delete) and paste my ext3 partition, how i will move my swap partition over, or does it not matter? And if i do decide to move it, will this have a major effect on my system? Once again thank and so sorry for taking your time.[/QUOTE]

I'm curious what is on hda5 actually, your FAT partition.  Its inside the extended partition and would be a perfect candidate for removing if it contains no important data.  If you are going to remove hda5, then after you move hda4, to the free space created from hda1, then you could remove all partitions inside the extended partition, hda4, hda5 and swap.  After removing them, you could move the ext3 partion back into the extended partition, expand it to fill the free space, but leave enough room on the end of the partition for the creation of a swap parition, then create a new swap partition.  I hope this makes sense. :)

It's all going to have to be done from a live CD though, as the locks on all those partitions means they are currently mounted, and you can't change a mounted partition.

All these changes are going to create new partition names and this will need to be reflected in the configuration of your /etc/fstab file, so that linux knows which partitions to mount on which mount points before it will be a working system again.  That will require a live CD too.

---

### Post by S{yndrom}e on 2006-05-24
could i use the ubuntu live cd and use gparted from there?
And what should i put in the /etc/fstab file. This is all really new to me and i don't want to screw up.

---

### Post by Mustard on 2006-05-24
I'm out of time for answering the rest of these questions unfortunately.  Someone else is going to have to pick up from here.

You can try asking for advice on the IRC support channel at irc.freenode.net in channel #ubuntu.  Someone might volunteer to help you through the process.  I think you definitely need to do some study on it before you make the attempt.

---

### Post by S{yndrom}e on 2006-05-25
anyone else can help?

---

