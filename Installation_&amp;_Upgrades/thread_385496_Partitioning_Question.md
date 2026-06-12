---
title: "Partitioning Question"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Sontra on 2007-03-15
'Ello,

I'm a first timer on Ubuntu and, as determined as I was to make it through the install without asking for help, here I am. :D Then again, I'm okay with that. 

My problem comes from a nervousness about having to go through the install process again and again (I'm not sure why, though... I've already backed up everything. Who cares?).

This PC is going to be strictly for my own use, so I don't need to worry about multiple users or anything. And I'm wanting to blow away my old Windows partition due to my growing frustration with it (long story. It's unimportant).

I've got three hard-drives. Two 80 gigs and a 320 gig. I understand the idea of having a swap, a root, and a home. Some of my reading tells me I should have more, just because I can. I'm not sure why this would be helpful or good.

Anyway, my point is: I don't know how much to be putting what where (other than have double my RAM for swap). Generally, I kind of understand, but with three hard drives and so much space, I'm hoping to go into this with a bit more of a specific answer.

Anyways, enough rambling from me. Thanks for the time!

---

### Post by peabody on 2007-03-15
I partition like this: 8gigs to root, swap = twice ram, rest to /home.  I've found 8gigs to be a somewhat magic number for root.  Just about every distro I've had has rarely surpassed 7 gigs for root, at least in my usage patterns.  If you're going to be using both KDE and Gnome, you might want to add 2-3 gigs to that size.

As for partitioning even more, I'd say don't bother, it's more hassle than it's worth.  Religious partitioning is an artifact of the early unix sysadmin days when it really helped fight fragmentation  and made it easier to swap out and put in new drives for heirarchies such as /var.  The only thing you might want to consider is to /boot on it's own partion of 70 megs or so.  That should be it though.

---

### Post by zvacet on 2007-03-15
during installation you will come to partition step.Choose manualy way and you will see all of yours HDD and partitions.If you wanr to erase win do it.Select on witch HDD you want to install Ubuntu,and you can begin with partitioning.
1.root =10-15GB(put more if you like) and this is good
2.home=rest of HDD exept
3.swap
Home saving your settings(sounds familyare) and you can put all your data,music... in it and they will be safe.Meaning,you can reinstall,freshinstall,upgrade...and your home directory willl be intact.Allmost forget.All partitions have to be in ext3 format.

---

### Post by Sontra on 2007-03-15
Perfect! That's exactly what I'll do then (I'll go for a bit extra on the root, just because I have the extra space).

Another quick question I've got now:

Since I'm planning on using all three hard drives, how do I connect them to other one. Hmm. Wording is weird. Lemmie explain my problem.

I've got 5 total partitions on the "Prepare mount points" menu: 

swap - 3 gig
root - 15 gig
home - 280 gig
home - 75ish gig
home 75 ish gig

I get a lovely message saying, "You have 2 or more partitions on the same mount" or something phrased slightly better. I know I'm doing something wrong. I can even understand, kind of, why. But I don't know how else I would go about what I'm trying to do.

-Thanks again!

---

### Post by Kateikyoushi on 2007-03-15
Why do you want to have 2 /home ?
That's the problem.

---

### Post by Sontra on 2007-03-15
It's not that I want multiple homes. It's that I want to be able to use the other two hard drives with my /home directory.

Does that make sense?

---

### Post by Kateikyoushi on 2007-03-15
Mount them as /media/
You can change the mount points in the fstab file after installanion, but it is not possible during the install to mount them to /home

---

### Post by Sontra on 2007-03-15
Perfect! Solved all my problems. [Initial problems].

Thanks everyone! Mucho appreciated

---

### Post by Kalyan Manchikanti on 2007-03-15
If you are really interested in learning further as to how to use those two remaining drives and have a single /home partition, you can do it using  LVM-Logical Volume Manager. Ubuntu has a lvm2 package that can help you do that.

---

### Post by Kateikyoushi on 2007-03-15
Thanks for the advice I look into it.

---

### Post by kanna1620 on 2007-03-30
> **Kalyan Manchikanti said:**
> If you are really interested in learning further as to how to use those two remaining drives and have a single /home partition, you can do it using  LVM-Logical Volume Manager. Ubuntu has a lvm2 package that can help you do that.
Hello there.I installed lvm2 but I dont know where is it. Plz help me. Actually I am running out of my disk space. I have space available on my windows partition and I want to add some of the disk space from windows partition to my Ubuntu partition. I dont know how to do that. Plz help me.
Thanks in advance.

---

### Post by kittyhawk63 on 2007-03-30
> **kanna1620 said:**
> Hello there.I installed lvm2 but I dont know where is it. Plz help me. Actually I am running out of my disk space. I have space available on my windows partition and I want to add some of the disk space from windows partition to my Ubuntu partition. I dont know how to do that. Plz help me.
Thanks in advance.

kanna1620

I recommend that you start your own thread regarding your question. You may get faster response.
kh

---

### Post by jiminid on 2007-03-30
> **peabody said:**
> I partition like this: 8gigs to root, swap = twice ram, rest to /home.  I've found 8gigs to be a somewhat magic number for root.  Just about every distro I've had has rarely surpassed 7 gigs for root, at least in my usage patterns.  If you're going to be using both KDE and Gnome, you might want to add 2-3 gigs to that size.

As for partitioning even more, I'd say don't bother, it's more hassle than it's worth.  Religious partitioning is an artifact of the early unix sysadmin days when it really helped fight fragmentation  and made it easier to swap out and put in new drives for heirarchies such as /var.  The only thing you might want to consider is to /boot on it's own partion of 70 megs or so.  That should be it though.

Hi, I've got a similiar question-
Are there rule of thumb percentages to partition with? i.e. I've got 2 80 gig drives, master has XP on it and I installed Dapper onto the slave...at least until I figure out how to do everything I do in windows in linux, then its bye bye winnie. Since I have very little installed on the dapper installation I was going to install edgy over it but repartition the drive so its more efficient, add boot, home maybe a temp partition. With percentages it doesn't matter the size of the drive, you just make the calculation and you're shiny. So what would you suggest?

Thanks for the help

Jiminid

---

