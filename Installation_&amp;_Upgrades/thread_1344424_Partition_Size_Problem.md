---
title: "Partition Size Problem"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by gamecraziness on 2009-12-02
Hi.
I'm a Linux noob, I'm just starting to use it, so please don't use any explanations that are too complicated.

I'm booting a Live USB for Ubuntu to partition my drive before installation, but there is a problem. I tried using GParted and the Ubuntu install but it shows the main partition as having no free space, and the only other space available is 8 MB of Unallocated Space. The problem is, that the partition actually has 42 GB of free space, and when I try to resize it it won't let me decrease it, only increase it by 8 MB. When I create a new partition it will not go above the 8 MB.

BTW, the OS installed on the partition is XP and it is NTFS.

Sorry if this isn't too clear.

Thanks in advance.

---

### Post by u.b.u.n.t.u on 2009-12-02
Welcome to the Ubuntu community!

Are you able to take a screenshot of gparted to illustration your description? Just would help an awful lot.

You can upload it here:
[http://imageshack.us/](http://imageshack.us/)

Also, what is the state of your HDD before, ie HDD size, partitions, operating system(s)?

What are you trying to achieve?

---

### Post by gamecraziness on 2009-12-02
Thanks.

I'll upload the screenshot tomorrow, I can't do it now, but basically it just won't let me reduce the size of the partition, although it has 42 GB of free space on it. The total HDD size is 80 GB and XP Professional is installed on it. That is the only partition I currently have on my hard drive, but I tried to split it to install Ubuntu.

So basically, I have one partition, 80 GB, 42 GB free, and I want to reduce its size to install Ubuntu on a new partition.

---

### Post by gamecraziness on 2009-12-02
Oh, forgot to mention-
I know I have to make 2 new partitions, one for / and the other for swap.

---

### Post by u.b.u.n.t.u on 2009-12-02
Perhaps try a live gparted CD?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by oldfred on 2009-12-03
Have you housecleaned your windows to delete old stuff and defragged at least twice?  You also have to make sure you have a clean total shutdown and not using hibernate or suspend. You may want to also run chkdsk which will required a reboot to run the file check that it does. After you create the new partitions, boot windows to make sure it still works ok before installing Ubuntu.

The 80GB drive is not really 80 GiB, different counting systems so you have a little less space than you thought. You have to leave about 20% free for Windows or else it will not work well. Ubuntu only needs about 10GB and probably 2GB for swap as minimums. So you should have room.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **oldfred said:**
> defragged at least twice?

At least twice? Wanna call this a typo or mis-speak?

---

### Post by gamecraziness on 2009-12-03
OK, thanks.
Why does the drive have to be defragmented though?
Also, you can't do two consecutive defragments, so I don't really know what you mean.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **gamecraziness said:**
> OK, thanks.
Why does the drive have to be defragmented though?
Also, you can't do two consecutive defragments, so I don't really know what you mean.

Best to read my comment and leave it at that.

---

### Post by oldfred on 2009-12-03
I always run two defrag twice as the first time it only does part of the movement to the left. The second moves more but usually not all the data. Defrag makes space at the end of the partition to the partitioner does not have to do as much work.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **oldfred said:**
> I always run two defrag twice as the first time it only does part of the movement to the left. The second moves more but usually not all the data. Defrag makes space at the end of the partition to the partitioner does not have to do as much work.

A second defrag is redundant.

This may interest you, free and portable.

[http://www.piriform.com/defraggler](http://www.piriform.com/defraggler)

---

### Post by gamecraziness on 2009-12-03
Yeah but the problem is that GParted won't let me reduce the size at all...
Some others on the forums have been reporting problems with 9.10 and NFTS drives. Maybe this is the reason?

---

### Post by gamecraziness on 2009-12-03
I'm just wondering,if I install Ubuntu on my Windows XP partition will it save the files? Because in the Windows 7 clean install it will save everything from your old install to a folder called Windows.old. Is there an equivalent in Linux?

---

### Post by u.b.u.n.t.u on 2009-12-03
> **gamecraziness said:**
> Some others on the forums have been reporting problems with 9.10 and NFTS drives.

A context is needed. For example, I use a single HDD with NTFS and ext4 and no problems, none.

> **gamecraziness said:**
> I'm just wondering,if I install Ubuntu on my Windows XP partition will it save the files? Because in the Windows 7 clean install it will save everything from your old install to a folder called Windows.old. Is there an equivalent in Linux?

Correct use of terminology avoids confusion.

Ubuntu 9.10 uses a file system called ext4. XP uses a file system called NTFS. Ubuntu 9.10 needs it's own ext4 partition and XP needs its own NTFS partition.

I am unsure what you are asking.

One may upgrade windows and save previous windows files and one may upgrade Ubuntu and save previous Ubuntu files.

It is essential to always have a verified backup of all important work regardless. If something important exists on a computer, it should also exist on a backup, and best practice means away from the actual computer, eg a CD, DVD, external HDD, Ubuntu One (Cloud) and the like.

[http://ubuntuforums.org/showthread.php?t=1171507](http://ubuntuforums.org/showthread.php?t=1171507)

---

### Post by gamecraziness on 2009-12-03
I see. That's unfortunate. I guess I'll try the GParted Live CD, though I don't see the difference.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **gamecraziness said:**
> I see. That's unfortunate.

What is unfortunate?

---

### Post by wilee-nilee on 2009-12-03
> **u.b.u.n.t.u said:**
> A second defrag is redundant.

This may interest you, free and portable.

[http://www.piriform.com/defraggler](http://www.piriform.com/defraggler)

Even piriform doesn't completely defarg every time check it out next time you use it.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **wilee-nilee said:**
> Even piriform doesn't completely defarg every time check it out next time you use it.

Why would I need to check it out? I use it and provided a link, you even quote me doing so ... funny lol!

Yeah, no defrag program is perfect and it doesn't need to be. It needs to be good and most are.

---

