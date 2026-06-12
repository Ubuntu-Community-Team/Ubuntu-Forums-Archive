---
title: "Gparted question adding space to a partition"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by dandixon on 2008-03-15
I new to Lunix so bare with me.
My deal is, I did a duel boot before I found out about VMware and how it works.
I have a 20 gig Ubuntu partition and a 26 gig XP partition. Also have 100 gig of storage.
I want to cut my 100 gig storage partition down to like 60 and add the 40 gigs to my
20 gig Ubuntu partition.  Can I do this? or should I just start over and reinstall?

I know you can cut down a partition but not sure you can add space to a drive with a os on it.

thanks

---

### Post by forestpixie on 2008-03-15
it depends on what order the partitions are in as to how you do this. It could be that newer versions of gparted allow you to move partitions easier.

Previously I had to shrink the 100 Gb first, then  move the buntu so that the free space is right of it - then expand into the space

post this if not sure

```
sudo fdisk -l
```

ot open gparted in buntu and post a scnshot - you know you have to either do it from the buntu livecd or a livecd gparted

---

### Post by Twotoes on 2008-03-15
Goto [https://help.ubuntu.com/community/HowtoPartition?highlight=%28how%29%7C%28to%29%7C%28partition%29](https://help.ubuntu.com/community/HowtoPartition?highlight=%28how%29%7C%28to%29%7C%28partition%29)
and the How To will tell you what you want to know

---

### Post by dandixon on 2008-03-15
Hey guy
I have done the resize where i have cut my storage drive down from 100 gig to 70gig. 
But now I want to add the 30 of unallocated space to my  partition where lunix is installed (ext3 20 gig).

Need more room to run vmware. But when i try to add it to my Lunix partition it dose not see the free space.

Help dan

---

### Post by logos34 on 2008-03-15
You still haven't said what order the partitions are in.

if it's

XP---------|storage------------------|freed space------|ubuntu------------

then you can grow ubuntu root partition to the LEFT to take up the free space--you need to work frm the Live CD (root cannot be mounted).

It will take a long time, however. (hours)

---

### Post by dandixon on 2008-03-15
sorry
ubuntu is ext3   20 gig
xp is ntfc            70 gig

unallocated 30 gig (want it to go to the ubuntu 20 gig)

---

### Post by Pumalite on 2008-03-15
Where is the screenshot?. It's essential for people to give you intelligent instructions.

---

### Post by dandixon on 2008-03-15
got a screen shot

My question is can I add my unallocated drive space to my partition where Ubuntu is installed? 
My Ubuntu is partition as ext3 as it filesystem.

If I try to resize/move on the Ubuntu ext3 partition it dose not let me to use the free space.

---

### Post by dandixon on 2008-03-15
screenshot
[IMG]http://mg182.imageshack.us/my.php?image=screenshoteu5.png[/IMG]

[http://img338.imageshack.us/my.php?image=screenshotpt7hb0.jpg](http://img338.imageshack.us/my.php?image=screenshotpt7hb0.jpg)

---

### Post by dandixon on 2008-03-15
[IMG]http://img338.imageshack.us/my.php?image=screenshotpt7hb0.jpg[/IMG]

---

### Post by forestpixie on 2008-03-16
The unallocated space is inside the extended partition, which is not ideal. 

Try to shrink the extended partition - then you will have unallocated space outside.
Move the extended partition to the right which should place it next to sda3 - then you can expand sda3.

But I've never actually done that so not sure if it can be achieved. Do each step seperately and click apply. This could take some time as well so don't turn it off, of course you need to make sure that you have good backups before you start.

Edit - it can be done with gparted - [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm) - it's toward the bottom

---

### Post by housam on 2008-03-16
Looking at your screen shot of Gparted, you can not add the unallocated space to the ext3 ubuntu partition because of the partition order ( the xp  and the starage partitions are situated between them)
But you can do another thing. 
- delete the ext3 ubuntu partition and use it as a storage partition part 1
- reinstall ubuntu on the 70 Gb storage partition after reformat to ext3
- use the unallocated space as a storage partition part 2

---

### Post by dandixon on 2008-03-16
Thanks guy.
I think I'll re install Ubuntu .
Starting to get the hang of run lunix at home.

---

