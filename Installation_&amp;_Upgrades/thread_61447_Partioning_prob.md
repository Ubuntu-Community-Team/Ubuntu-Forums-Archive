---
title: "Partioning prob"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by brk3 on 2005-08-31
Ive recently bought a laptop which i want to install ubuntu on.(hp pavilion but dont think its relavant to this problem)
However I am  having trouble partitioning my drive. I have an 80gig hardrive and just want to section off about 10 or 15 gigs for the installation. When i try to adjust the 'size' label on the installer and press enter, it just brings me back the main page with the list of partitions, makes no change. 
Here are some other methods I have tried:

Mandrake: what i used to install linux on my desktop, but the installer wont recognise my cdrom so cannot boot the partitioner.(i cant use a boot floppy because this laptop has no floppy drive.

Suse: Tells me that i need to defrag my hard disk so that the ntfs resize program can resize it. however it is a brand new laptop, and the disk is 0% fragmented!

Fedora Core: Cant even remember what error it gave but it was something unhelpfull..

Knoppix/qtparted: When it went to resize it said it couldnt check the disk for errors due to bad superblock.. or something like that.

cfdisk: doesnt seem to have an option to resize?

This seems like a newbie post and Im surprised I have to be posting it(ive been using linux on my desktop for ages), but of the troubles linux could be giving on a laptop, this shouldnt be one of them!
Any help please? Are there any free partition resizers for windows or what can I do

---

### Post by nad on 2005-08-31
Does this describe your computer and issue?

[http://www.ubuntuforums.org/showthread.php?t=56937&highlight=drivelock](http://www.ubuntuforums.org/showthread.php?t=56937&highlight=drivelock)

---

### Post by brk3 on 2005-08-31
I very sincerly hope not. Drivelock seems to just protect the drive if its removed or something like that I dont think it would affect partitioning.. Not sure though. Why me :-(

Thanks for the feedback though. Any other ideas I can try?

---

### Post by [pl]ice on 2005-09-01
so u got new laptop w/o any partitions on it?? can't you just boot live cd then create cfdisk partitions? (then mkfs )maybe you have mocked up primary/logical somehow, then you can't put other partitions on it. cfdisk got move partitions somwhere else, maybe you can create a temp one?? otherwise don't know :/

---

### Post by brk3 on 2005-10-07
got it with partiton magic. needed to run chkdsk

---

