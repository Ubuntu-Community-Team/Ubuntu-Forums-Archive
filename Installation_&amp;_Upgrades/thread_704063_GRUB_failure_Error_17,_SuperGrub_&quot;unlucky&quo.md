---
title: "GRUB failure Error 17, SuperGrub &quot;unlucky&quot;"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by the_phoenix on 2008-02-22
Hi:

This Newbie needs your help.

In Xubuntu, earlier this week,  mycomputer just would not boot.
Kept getting 

GRUB loading...
Error 17

Someone on here recommended SuperGrub. I tried it, and got 

"unlucky" loading report
and Error 15

What do I need to do?
I have photo and work files that I need really badly, on that machine, and the Live disc won't let me reach them.

Is there a way to reload the entire boot file (if there is such a thing) without my computer being formatted, in the process?

Please help me, Linux Geeks and Gods.

---

### Post by toa on 2008-02-22
The files you trying to reach are they in the same partition or with other NTFS for windows, do you have dual boot with windows.? 

Once the live CD is booted you may have chances of recovering yor data, just need to know where is the data located.

---

### Post by Partyboi2 on 2008-02-22
[here]("http://users.bigpond.net.au/hermanzone/p15.htm#15") some  info on grub error 15

---

### Post by dstew on 2008-02-22
The original error is from grub stage 1.5, and means that the partition structure was changed since grub was originally installed. Since you are running xubuntu, I assume you do not have enough capability to run the Live CD. That's OK, we can work on this using the supergrub disk.

First, we need a list of your partitions. From the supergrub boot, get to the grub command line by pressing 'c'. You will get the grub> prompt. At the grub prompt type```
root (
```and then press the tab key. That should give you a list of the partitions that grub can find. Next, for each drive, enter the command```
geometry (hd0)
```and so forth. That will tell you which partitions are NTFS, which are ext3. Post the output of these commands, and maybe we can re-install grub and get it working again.

---

### Post by the_phoenix on 2008-02-23
Below is everything I could find out about my system. I employed methods suggested by all responders, (2 online, 1 local), and wanted to share what I found [and how I got it/to it], because some of it looked conflicting to me. 'Of course, I don't know Linux, so that's easy to do!
Anyway, one example is an additional sda (sda2) shows up by way of the 'sudo fdisk -l' method that doesn't in the others.

Also, when trying to load the GRUB directly, even after identifying the drives, SuperGrub failed. I don't know if that's useful information or not, but I thought I'd share it.

Here's the info:

[From trying &#8216;Advanced&#8217; &#8216;GNU/Linux&#8217; &#8216;Install&#8230;&#8217; while trying to run, then install SuperGrub]
Partition of GRUB
N	IDE	SCSI	GRUB		HURD		TYPE		OS
1	hda1	sda1	(hd0,0)		hd0s1		ext2fs		Ubuntu 7.10 \n\1
3	hda3	sda3	(hd0,2)		hd0s3		Linux
5	hda5	sda5	(hd0,4)		hd0s5		SWAP
6	hda6	sda6	(hd0,5)		hd0s6		SWAP


[From &#8216;root (0,0)&#8217; &#8216;root (0,2)&#8217; etc,  on SuperGrub&#8217;s command prompt]
0,0 Filesystem Type ext2fs, partition type 0x83
0,2 Filesystem Type unknown, partition type 0x83
0,4 Unrecognized device string
0,5 Unrecognized device string


[From 'root (' and TAB]
Possible disks are fd0 hd0 cd

[From 'geometry (fd0)]
Error 25: Disk read error

[ From &#8216;geometry (hd0)&#8217;]
Drive 0x80: C/H/S = 1022/240/63, The number of sectors = 19541088, LBA
Partition num: 0, Filesystem type is ext2fs, partition type 0x83
Partition num: 2, Filesystem type unknown, partition type 0x83
Partition num: 4, No BSD/SOLARIS sub-partition found, partition type 0x82
Partition num: 5, No BSD/SOLARIS sub-partition found, partition type 0x82



[From &#8216;sudo fdisk &#8211;lu&#8217;]
Device Boot	Start		End		Blocks		Id	System
/dev/sda1	63		9092789	4546363+	83	Linux
/dev/sda2	18073125	1953039	730957+	5	Extended
/dev/sda3   *	9092790	18073124	4490167+	83	Linux
/dev/sda5	18603333	19535039	465853+	82	Linux swap / Solaris
/dev/sda6	18073251	18603269	265009+	82	Linux swap / Solaris


Thank you.
the_phoenix

---

