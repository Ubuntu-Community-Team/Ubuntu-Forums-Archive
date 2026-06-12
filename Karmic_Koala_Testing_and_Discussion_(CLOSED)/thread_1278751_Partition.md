---
title: "Partition"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by orc_dragoon on 2009-09-29
For some reason Im not able to edit my Ubuntu Karmic Partition. Is this like that for a reason and is anyone else having this problem?

---

### Post by lindsay7 on 2009-09-29
Have you unmounted the partition or drive.  Right click on it and unmount it. You may also have "swapoff the swap partition too.  You need to use the install cd to use Gparted or download Gparted from their web site.

---

### Post by Bucky Ball on 2009-09-29
> **lindsay7 said:**
> Have you unmounted the partition or drive.  Right click on it and unmount it. 

You can not unmount the partition your OS is running on. If you need to resize you Ubuntu partition you need to do it using either the Gparted Live CD or the Ubuntu Live CD. This way NO partitions are mounted.

---

### Post by ranch hand on 2009-09-30
> **Bucky Ball said:**
> You can not unmount the partition your OS is running on. If you need to resize you Ubuntu partition you need to do it using either the Gparted Live CD or the Ubuntu Live CD. This way NO partitions are mounted.
Or use gparted on an OS on a different drive.

---

### Post by LKjell on 2009-09-30
I am wondering how Windows do it.

---

### Post by howefield on 2009-09-30
> **LKjell said:**
> I am wondering how Windows do it.

"Windows" can't, so wonder no more.

Unless you want to be more specific than using such an all encompassing term such as "Windows".

---

### Post by LKjell on 2009-09-30
We have Partition Magic and Vista that can resize a partition. In Vista you can check disk manager to resize it.

---

### Post by howefield on 2009-09-30
Thank you, that is a more accurate reflection, and less like an attempt to troll ;)

Unless you have Vista (or the soon to be released Windows 7), you require a third party application.

---

### Post by Bucky Ball on 2009-09-30
Windows won't read ext3 or ext4 partitions so you were right the first time. Wonder know more. If you are wanting to fiddle with your Karmic partition, Windows will probably report the partition type as 'unknown'. That's that.

---

### Post by bluenova on 2009-09-30
Calm down ladies, people are quite bitchy in here today.


@orc_dragoon, how exactly are you trying to partition it?

---

### Post by VMC on 2009-09-30
I have rarely used MS Windows disk manager. And when I did it is only for MS file systems.

What I used for a long time was Acronis Disk Director for partitions and Acronis True Image for backups. Since inode greater than 128, True Image no longer works. Now its either Clonzilla or partclone.ext4 for backups.

 In the past gparted either took way to long to finish or failed. Not any more.

  Gparted is by far the best partitioning program. The GUI makes it easy to see what your doing, and even see what you can do and back out if it looks wrong. the newest gparted has **not** failed in the past year! I would never use MS Windows disk manager again.

---

### Post by LKjell on 2009-09-30
> **Bucky Ball said:**
> Windows won't read ext3 or ext4 partitions so you were right the first time. Wonder know more. If you are wanting to fiddle with your Karmic partition, Windows will probably report the partition type as 'unknown'. That's that.

The point is that Windows can resize its partitions without a live cd, less hazzle, than Ubuntu. So there must be a flaw somewhere.

---

### Post by ezsit on 2009-09-30
> The point is that Windows can resize its partitions without a live cd, less hazzle, than Ubuntu. So there must be a flaw somewhere.

That's pretty cool. However, I am old school and for me, any resizing of partitions means repartitioning the entire drive. I would not trust Windows to resize partitions on the fly on a live system. 

I only use partitioning tools running from a live CD where I can work on the drive to be partitioned without mounting any of the volumes and turn swap off before doing any work. I use cfdisk from a live CD. I then use mkfs to format the partitions. I have never had problems with either program.

---

### Post by TunaCanTommy on 2009-09-30
I would highly recommend getting a copy of SystemRescueCd (Linux) and put it on a thumb-drive, 512Mb is big enough.  It has all the tools you need to working on partitions, it incorporates networking, and you can load it in RAM. I've used it to help my friends still running Windows to save files and fix hard--drive problems. I wouldn't be without it.

---

### Post by Seventh Reign on 2009-09-30
> **LKjell said:**
> The point is that Windows can resize its partitions without a live cd, less hazzle, than Ubuntu. So there must be a flaw somewhere.

That is completely 100% NOT True.  Partitioning a Disc with Windows is DEFINITELY one of the most gut wrenching tasks you can perform.  9 times out of 10 your discs end up completely wiped.  I've used Gparted to resize around 35-45 HDD's with Windows NTFS, Fat32, and Unix ext2, ext3, ext4, & Reiserfs, without a single issue

---

### Post by Longinus00 on 2009-09-30
> **LKjell said:**
> The point is that Windows can resize its partitions without a live cd, less hazzle, than Ubuntu. So there must be a flaw somewhere.

Ubuntu can resize partitions without a live cd as well. I don't understand where all the confusion is coming from in this thread. Neither ubuntu or windows can do online resizing so maybe people are confusing the two terms?

---

### Post by LKjell on 2009-10-01
> **Longinus00 said:**
> Ubuntu can resize partitions without a live cd as well. I don't understand where all the confusion is coming from in this thread. Neither ubuntu or windows can do online resizing so maybe people are confusing the two terms?
Would you shed some light on how?

---

### Post by Bucky Ball on 2009-10-01
> **LKjell said:**
> Would you shed some light on how?

+1. I'm fascinated ...

We're talking about resizing the partition Ubuntu is on you need Live CD. Yes?

---

### Post by Longinus00 on 2009-10-01
> **LKjell said:**
> Would you shed some light on how?

Just install this. 

You may need these supplemental packages depending on what type of filesystem you're interested in.

xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs, dosfstools

---

### Post by Bucky Ball on 2009-10-01
Yea, we know what gparted is. But you need to use gparted from the Live CD to resize the partition with the Ubuntu OS on it because that is the only way you can unmount it. That is what we are talking about. 

All other partitions, fine. But you can't unmount a partition when you have got the OS running on it. That is not possible. You can of course try and get back to us ...

---

### Post by Longinus00 on 2009-10-01
> **Bucky Ball said:**
> Yea, we know what gparted is. But you need to use gparted from the Live CD to resize the partition with the Ubuntu OS on it because that is the only way you can unmount it. That is what we are talking about. 

All other partitions, fine. But you can't unmount a partition when you have got the OS running on it. That is not possible. You can of course try and get back to us ...

Where did I say you could resize a mounted partition? You can grow ext3/2 partitions that are mounted with resize2fs but since ext4 is the default now I don't think that counts.

I was responding to this quote.

> **LKjell said:**
> The point is that Windows can resize its partitions without a live cd, less hazzle, than Ubuntu. So there must be a flaw somewhere.

---

### Post by LKjell on 2009-10-02
> **Longinus00 said:**
> Ubuntu **can** resize partitions **without** a live cd as well. I don't understand where all the confusion is coming from in this thread. Neither ubuntu or windows can do online resizing so maybe people are confusing the two terms?

Then please tell me how with ext4.

---

### Post by ranch hand on 2009-10-02
> **LKjell said:**
> Then please tell me how with ext4.
If you have another drive with an OS with gparted you can do the job from there.

The easiest, and safest, way to do it is with a live CD for 9.04 or 9.10 and use gparted from there.

It is located at System>Administration>Gparted (I have seen it as Partition Editor too, but I think that was in Mandriva-gnome)

---

### Post by Longinus00 on 2009-10-02
> **LKjell said:**
> Then please tell me how with ext4.

Ubuntu can resize an ext4 partition. I don't know why you keep denying that. Just use gparted.

---

### Post by LKjell on 2009-10-02
This is making me annoying since we are going into a circle. Let me clarify once and for all. 

In Windows Vista I **can** resize my partitions(NTFS) **without** a live cd, other OS to help me, put in a floppy disk or any external storage. But in Linux with kernel 2.6.31-11 x86_64 I **cannot** resize my partitions(EXT4) **without** a live cd, other OS to help me, put in a floppy disk or any external storage; because the filesystem is mounted and online resize is limited.

---

### Post by ranch hand on 2009-10-02
So what is the problem here?  Use the friggin LiveCD.

---

### Post by Longinus00 on 2009-10-02
> **LKjell said:**
> This is making me annoying since we are going into a circle. Let me clarify once and for all. 

In Windows Vista I **can** resize my partitions(NTFS) **without** a live cd, other OS to help me, put in a floppy disk or any external storage. But in Linux with kernel 2.6.31-11 x86_64 I **cannot** resize my partitions(EXT4) **without** a live cd, other OS to help me, put in a floppy disk or any external storage; because the filesystem is mounted and online resize is limited.

You can only resize the partition in windows up until it hits a pagefile or something else, not very useful. Let me give you an example, a laptop of mine has 254 GB C: drive and I wanted to shrink it with disk manager. There is 175 GB free space but disk manage will only let me shrink 7GB because there is a file that's open (probably the page file) preventing shrinking further.

If you want to do any real re-partitioning you're going to need to reboot one way or another.

---

### Post by ezsit on 2009-10-05
Ranch Hand wrote:
> So what is the problem here? Use the friggin LiveCD.

+1!
+1!
+1!

---

