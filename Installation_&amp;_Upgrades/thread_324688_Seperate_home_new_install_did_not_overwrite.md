---
title: "Seperate home: new install did not overwrite"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2006-12-24
Hi,

My version 5.10 was upgradet to 6.06 LTS on my Pentium IV
My home is seperate with a dual boot with XP.

Then I got the new CD's in the mail with the 6.06 LTS and my gool was to reinstall the 6.06 version over the old one. Because I have a seperate /home I thougt that was easy.

So I start from CD the 6.06 LTS and left all the already made seperate Sartitions like they were:

Partition 1              /dev/hda1 Windows NTFS     13.97 Gib

Partition 3              /dev/hda3                          42.84 Gib
                            extended 3
                           /home

Swap-partition         /dev/hda6                         1.3 Gib

Partition 2              /dev/hda 2                         2.44 Gib
                            windows virtual FAT (vfat)              
                            /media/windows   


When the installer asked th check ore uncheck the partitions to defragmentate I choose not to else my home content got lost.

After the new install I restarded my PC and Ubuntu made a totaly new install
of the 6.06. I thought he had overwrited the old instal but the old instal was now on ( dev/hda3) 

My intent was a new install over my old 6.06 so that i could use my home folder but now I've got a seperate instal with a new /home !

What did I do wrong ?


Thanks,

Paul.

---

### Post by bulldog on 2006-12-24
You should have formatted the old / partition,not the /home.
On / was your old install and you had to mount this one as / again and format it as ext3.
The swap you had to mount as swap and format it as swap.
Your /home had to be mounted as /home again but **NOT** to be formatted.

When you not format a partition, ubuntu will not overwrite it.

---

### Post by Dutch on 2006-12-24
> **bulldog said:**
> You should have formatted the old / partition,not the /home.
On / was your old install and you had to mount this one as / again and format it as ext3.
The swap you had to mount as swap and format it as swap.
Your /home had to be mounted as /home again but **NOT** to be formatted.

When you not format a partition, ubuntu will not overwrite it.


Ok, so I did have to format. I forgot, sorry !
After using Ubuntu for almost a year now,I want to get ride of the XP partition I can live without it.
So do U have for me a working how-to to reinstall Ubuntu on my HD.
And so that wen I want to update al my old seting stays the same and my /home is untouched ?

Do I have to make then an extra partition for the adjustments ? and how ?

Thanks,

Paul.

---

### Post by bulldog on 2006-12-24
Download the gparted live cd it's only 30MB and burn it to a disk.
Boot from it and follow the steps so you'll end up with your hdd listed and the partitions on it.
Create the partitions you want,I can make some suggestions,but it's up to what  you need.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I should make a /  of about 15GB format as ext3
A data partition for important stuff as big as you like format as ext3
You have a /home already so this can be skipped, don't format it. 
A swap of about 1GB formatted as swap

This should be sufficient but if you want to make more partitions,you'll have to create an extended partition,so there only can be three primary's and one extended partition.
Make the swap at the end of the disk.

If you have more questions let me know,I'm Dutch too,so if you prefer your native language use msn or skype.

---

### Post by meng on 2006-12-24
If I recall correctly, you get a choice with each partition:

yes, format it
no, keep existing data

You want to make sure you "keep existing data". Also make sure that you match up each partition and mountpoint, e.g. /dev/hda3 gets mounted to /home.

The partitioning step of the install is where you have to concentrate very hard and avoid mistakes.

---

### Post by Bartender on 2006-12-31
If a person wanted to make a separate /home partition, does Linux care one bit if you make that home partition as logical inside the extended?

The easiest thing to do would be to place it in a primary partition.  If you had any left.  The average dual-boot will only have one primary left and it might be better to put /home somewhere else...

EDIT:  Never mind.  Plenty of posts saying you can put /home inside extended...

---

### Post by bulldog on 2006-12-31
> **Bartender said:**
> If a person wanted to make a separate /home partition, does Linux care one bit if you make that home partition as logical inside the extended?

The easiest thing to do would be to place it in a primary partition.  If you had any left.  The average dual-boot will only have one primary left and it might be better to put /home somewhere else...

EDIT:  Never mind.  Plenty of posts saying you can put /home inside extended...

FYI,an extended partition is just a box,so you can make more partitions.
The primary's and logical partitions are not so different from each other,you'll never noticed the difference when you use them.
The Big difference is that a windows OS will have big trouble to boot from a logical partitions,I have heard it should be possible under certain circumstances but it will be a pain to get it right.[somebody correct me if I'm wrong please]
The linux OS's seem to have no trouble booting from logical drives as far as I know.

---

