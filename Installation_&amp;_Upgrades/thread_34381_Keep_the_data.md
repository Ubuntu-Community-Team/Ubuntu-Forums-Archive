---
title: "Keep the data"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by daniminas on 2005-05-14
Hi

On my computer i have a lot of data saved on the harddisk. On the expert mode of the installation i want to install ubuntu keeping the old data. (no delete all) . I don't have problems with que sapace, but i don't know how.
So, a read the disc partitioner on the install menu, but i don't understand that. So somebody can help me with that?

Thanks so much


PD->Sory my english. I'm from Uruguay

---

### Post by nad on 2005-05-14
Your English is fine. What is confusing is the partitioning menu. I find it easier to first partition a disk the way I wish it from a diagnostic cd (any live linux cd will usually do), then do the ubuntu install. This way I have already done the partitioning from a familiar interface with less chance of error.

---

### Post by daniminas on 2005-05-15
okey, i gonna try it  :)

---

### Post by daniminas on 2005-05-16
Hello again

My problem to keep the data have me very confused at this point.
This is what i do:

On 'Partition disks' this two options are what i see on the screen:

>Partitioning disk: IDE1 master (hda) - 20.0 GB WDC WD200EB-34BHF0
>Manually edit partition table


So, i enter to the 'manual edit': (This is what i have to do, no?)

And this is what i see:

>IDE1 master (hda) - 20.0GB WDC WD200EB-34BHF0
>        #1 primary 20.0GB (down arrow) fat32


I enter to '#1' and this is the partition setting:

>Use as: do not use
>Bootable flag: on
>Size: 20.0GB

If i enter to the 'Size' option, a lot of Dialogues with the text '???' and <Go back> and <Continue> and i have to reboot he computer.
 

That's it. I'm really don't know HOW can i do, or WHAT i have to do to keep the old data of the disk. (20Gb disk in total - 13GB used).
I verry like all this, Ubuntu, etc.., but this installation problem have me very disappointed. 

Thanks you. And any little help is welcome. :)

Danielle

---

### Post by az on 2005-05-16
So you have only one partitionnow, right?  It is 20 gigs in size and has about 13 gigs of data that you want to keep.

When you select it and enter size, put 15G and hit enter.  It will ask you if you really want to do it.  Say yes.  If it is unable to do it because there is too much data (more than 15 gig) or some other problem, it will refuse to do it.  It should just decrease the size of that partition to 15 Gigs.

The next time you are shown the partition table, you should see yout 15Gig partition and then some free space after it.  Tell the partitionner to use it and use the guided partitioning option.  It will do all the calculations (root partition and swap)  for you and ask you if what it suggests is okay.  If you are happy with it, tell it yes and the install will continue.

You do not need to be running in expert mode.  Actually, you will have a greater chance of creating problems if you use the expert mode.  The regular (default) mode is very safe and will ask you before doing anything that can put your disk in danger.  Do not worry.

---

### Post by DutchLau on 2005-05-16
There's a good chance that you'll have to defragment your HDD in winblows in order to partition it without the loss of any files. I think NTFS purposefully puts files at the end of the partition, because I * always * have problems with this. 

Good luck though,

Dutchlau

---

### Post by daniminas on 2005-05-17
Thanks again. azz your help  was great and i have now Ubutu installed. (without problems) :smile:  :smile:  :smile: 

Danielle

---

### Post by daniminas on 2005-05-17
and DutchLau, thanks for you 'defragment ' help..  :)

---

