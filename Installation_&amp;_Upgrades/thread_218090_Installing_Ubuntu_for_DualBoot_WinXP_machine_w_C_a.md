---
title: "Installing Ubuntu for DualBoot WinXP machine w/ C: and D: Drives"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by mejohnsn on 2006-07-18
I would like to install Ubuntu (from the latest LiveCD) on
my laptop, making it a dual-boot system. But I am
hesitating, because of the following dire predictions based
on the Windows Partitioning.

Under WinXP, Administrative Tools>Computer Management shows:

Volume	     Layout	    Type	   F. Sys.    Status
(blank)	     Partition	    Basic	   NTFS	      Healthy
						      (EISA conf.)

C:	     Partition      Basic	   NTFS	      Healthy
						      (system)

D:	     Partition      Basic	   NTFS	      Healthy

Below that display, there is:

"Disk0 Basic 37.52G Online" foll. by three boxes, for each
of the above partitions. Only the box for D: is in green,
which I assume means it is the sole extended partition.

I believe this shows that all the partitions are on Disk 0,
the one and only basic disk.

Now D: has a lot of room on it, so what I want to do is
split it up into two partitions, one for the existing
Windows stuff on D:, the remainder for Linux.

Now the WinXP Help File (under Partitions and Volumes) says:

   You can only create basic volumes on basic disks.

And:

   You can create up to four primary partitions, or you can
   create up to three primary partitions and one extended
   partition.

So according to this, I should be able to make one more
partition. But the first problem is that the Help File
describes the ability to run the New Partition Wizard only
on an _unallocated_ region: not how to resize a
partition. It also shows how to make a new logical drive in
an already-existing partition. But neither of these is what
I want.

The second problem is that D: _is_ the extended
partition. So what I would need to do is split up D: into a
primary partition, and a new extended partition. This sounds
questionable, and I am not sure how to do it. I am less sure
that Ubuntu's install would guess this right.

Finally, it does not add to clarity that the Windows tool
talks about "primary" vs. "extended" partitions in the Help
file, but in the display mentioned above, lists the
partitions as 'basic volumes'.

So I had hoped to use one of the Linux tools to do this.

But I don't _see_ this same distinction between basic, primary and extended partitions in QTParted etc. So I have no way of
knowing whether I am still keeping to the above-mentioned
limits while using the Linux tool. For the same reason, nor
can I be sure that whatever changes the Linux tool makes are
legitimate under Windows.

GNU's 'parted', for example (Version 1.6.25.1) shows:

#	Start	    End	     Size      Type	FS	Flags
1	32k	    5001M    5001M     prim	ntfs	
2	5001M	    21G	     16G       prim	ntfs	boot
3	21G	    50G	     19G       extd		lba
5	21G	    40G	     19G       log	ntfs

Now I know it sound weird that it skips #4, but "ls
dev/hda*" does the same.

Gparted (which failed from the System Menu, but works when
run via a terminal using sudo) shows "Resize/Move" enabled
on both hda3 and hda5. But it does not show 'New" enabled.

This appears to imply that I cannot install LINUX on my hard
drive without giving up on on one of the partitions I
already have. Is this true?

I already looked at the documentation at
[https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning)
and at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) and
I see no answer there. On the contrary: these docs seems
unaware of the limit (mentioned above) from the WinXP Help
file.

I am running liveCD for 2006.06 on a Sony VAIO PCG-FRV26
running WinXP Home Edition with SP2.

TIA!

---

### Post by mejohnsn on 2006-07-20
Still no answers? Surely there are others who have dual-boot machines with C: and D: drives. So someone should have solved this identical problem before.

From reading done since my post, I have decided that I was probably misled to be so converned about the limit of 4 partitions, since one can make an arbitrary number of extended partitions. But Since /dev/hda3 seems to be the containing partition for /dev/hda5, I am wondering if I have to resize them separately or not.

Anybody got any ideas?

Finally, yes, I realize the formatting for thetables in my previous post is screwed up, making it hard to read. But I have yet to figure out a solution to this. Again: any ideas? Do I need to turn on HTML and make the table in HTML?

---

### Post by sonnywise on 2006-07-20
You can create four primary partitions or three primary partitions and an extended partition that contains logical units.

In my 100 GB hard drive I have 3 primary partition:
- hp system partition
- Win XP C:\ drive
- Win XP D:\ drive

...and an extended partition containing 3 logical units:
- Win XP E:\ drive
- Ubuntu linux \
- Ubuntu linux swap

For resizing purposes I used partition magic.

I hope this can help you.

---

### Post by mejohnsn on 2006-07-22
Thanks! It does sound like your setup is very similar to what I want to do. So please bear with me and explain how you added that E: partition. Did you start out by resizing the partition Windows called your D: drive into something smaller, and then making a new partition? And did you include the new partition in the same extended partition as your D: drive? I ask this because it is my understanding (which could be somewhat confused, I know) that the extended partition contains other partitions inside it. Is that right? Is that why GParted displays /dev/hda5 as indented beneath /dev/hda3?

Could you run GParted or Gnu's parted on your drives and attach the output to this thread? That would help me understand what you did, vs. what I should do. I _think_ they are similar.

So, for example, if you choose 'parted' (certainly easier to attach output as text), you might execute "sudo parted /dev/hda print".

In fact, I am going to try to attach the output from that command on my system, hoping that this time it will show up in a more readable format:

ubuntu@ubuntu:~$ sudo parted /dev/hda print
Disk geometry for /dev/hda: 0kB - 40GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    5001MB  5001MB  primary   ntfs
2       5001MB  21GB    16GB    primary   ntfs         boot
3       21GB    40GB    19GB    extended               lba
5       21GB    40GB    19GB    logical   ntfs


Again, thanks for your answer, and please keep up the good work;)

---

### Post by ahallubuntu on 2006-07-23
Yes, an Extended Partition contains one or more Logical Partitions.

Ijust installed Ubuntu Dapper Drake last night as a multi-boot system (on my laptop, with only one hard disk).  Although I manually partitioned everything myself, during the partitioning process there was an option somewhere to try to shrink the Windows partition to free up space for Ubuntu.  Then it would make new partitions for you (you need one for the Linux file system, another for swap).  I don't know how effective the partition resizer is, but as long as you have backed up your Windows data on that 2nd hard drive first, you might as well try it.

You could also consider using a program like Partition Magic (Windows, not free) to resize the partition yourself or a freeware program (there are a few).  I've resized partitions before and it has worked, but again, sometimes this stuff messed up and your data gets hosed.  Just make sure you've got a backup of your data.

Also note that at the end of Ubuntu install, it will install the Grub boot loader on the Master Boot Record (MBR) of your FIRST hard drive.  This sometimes causes problems and could make your Windows partition unbootable (although it's usually not impossible to get that back).  For me now, Grub boots XP for me just fine, so it worked with no problems - but I'm careful nowadays before I install anything over my MBR to save a copy of it.  It's easy to do.  You can do it with Ubuntu after booting the CD but before you run the installation.  Here's what you do:

- open up a terminal window under "Applications -> Accessories"
- type this:

sudo dd if=/dev/hda of=/tmp/origmbr.sec bs=512 count=1

Then you need to copy the file /tmp/origmbr.sec somehow (because during live boot, all files are saved in a RAM disk).  If you have a floppy or a USB flash drive, that's an easy way to do it.  You can also try emailing a copy to yourself as an attachment, if you have webmail that's the best way to keep a copy of it.

---

### Post by mejohnsn on 2006-07-25
> **ahallubuntu said:**
> Yes, an Extended Partition contains one or more Logical Partitions.

Thanks for confirming this. As you might have noticed, that is how I was interpreting what I had read, but I was still unsure.

Also, thanks for confirming how to save a copy of the MBR. I have seen numerous warnings to backup not only this, but the partition table too, which is non-trivial for extended partitions: somewhere I saw an explanation of how to do this using the '-d' option of the 'sfdisk' command.

And yes, while waiting for answers to this post, I have been puzzling over figuring out how to access the USB drives (I have two USB flash drives I can use), High Speed USB (the 250G drive I plan to use for the backup) and NTFS in r/w mode using 'Captive-NTFS'. The former two problems are solved.

I suppose it would be easier to go ahead and use Partition Magic, but it seems strange to spend the money on a program like that, when I expect to use it SO rarely. Especially when both SystemRescueCD and Ubuntu offer several alternatives, all Linux based and usable on Intel/AMD/PPC architectures. So the main problem now left is deciding which alternative to use for backup: partimage, dar, or even Cygwin's more primitive tar or even cp commands.

Now if only the USB drive would not give "Delayed Write Failed" error messages during Cygwin tar!


Again, thanks for your help.

---

### Post by Herman on 2006-07-25
Hello, I mean to say all this in a freindly way, but I am afraid there is something I must point out here.

The first 446 bytes of your MBR contains the 'IPL' or first stage of your bootloader, which points the BIOS to wherever the main working part of your bootloader is installed.
The first 446 bytes is the only part of the MBR I would back up, personally.

The next 64 bytes are the four sixteen byte entries of your partition table, and the last 2 bytes are the 55aa signature.

446+64+2=512

Now, what do you think is likely to happen if you back up your entire MBR including your present partition table, and then go ahead and run disk partitioning software to edit the partition table and format filesystems on your hard disk according to the new partition table? What do you think will happen when you restore the *old* partition table again, all of a sudden, when you have *new *filesystems that won't match it?
I haven't tried it myself, so I am not speaking from experience, but I do not imagine the results will be desireable. 

Personally, I only make a backup of the first 446 bytes, which is just the bootloader section and that works fine for me.
```
 sudo dd if=/dev/hda of=/tmp/origmbr.sec bs=446 count=1
``` Including the partition table in it makes a time bomb.

I hope people don't take me as a troll here or anything, but I honestly mean to prevent harm. Please interpret this post in a freindly tone, I'm just trying to be helpful. :-D

Regards, Herman

---

### Post by mejohnsn on 2006-07-26
> **Herman said:**
> Hello, I mean to say all this in a freindly way, but I am afraid there is something I must point out here.

The first 446 bytes of your MBR contains the 'IPL' or first stage of your bootloader, which points the BIOS to wherever the main working part of your bootloader is installed.
The first 446 bytes is the only part of the MBR I would back up, personally.

The next 64 bytes are the four sixteen byte entries of your partition table, and the last 2 bytes are the 55aa signature.

446+64+2=512

Now, what do you think is likely to happen if you back up your entire MBR including your present partition table, and then go ahead and run disk partitioning software to edit the partition table and format filesystems on your hard disk according to the new partition table? What do you think will happen when you restore the *old* partition table again, all of a sudden, when you have *new *filesystems that won't match it?
I haven't tried it myself, so I am not speaking from experience, but I do not imagine the results will be desireable. 

Personally, I only make a backup of the first 446 bytes, which is just the bootloader section and that works fine for me.
```
 sudo dd if=/dev/hda of=/tmp/origmbr.sec bs=446 count=1
``` Including the partition table in it makes a time bomb.

I hope people don't take me as a troll here or anything, but I honestly mean to prevent harm. Please interpret this post in a freindly tone, I'm just trying to be helpful. :-D

Regards, Herman


Nobody should take this for 'trolling'. You have made a useful observation. I have seen dd command lines to do both (i.e. backup only IPL, or backup whole MBR) in various places on the web, often without adequate explanation of when to use which. It seems you heavily favor always backing up only the IPL.

Of course the partition table must be backed up also, but since I have an extended partition, copying the entire MBR does not accomplish that goal. I have to do something like:
 "sfdisk -d /dev/hda >/media/usbdisk/PartTableBkup"

anyway.

Now in my case, I could probably get away with the "time-bomb", but only because I planned to use this backup only if I want to restore the disk to what it was. But it is still a time-bomb. So thanks for the warning.

But before I worry about that problem, I have to solve the problem of proper backup. I managed to copy all the WinXP files from C: onto a USB disk (not my favored mode of backup), and have been _trying_ to get partimage to work. I need something like partimage to backup the _hidden_ partition Sony uses to store the backup used by System Restore (or their Media Recovery). But partimage, used with mount.captive-ntfs (from SystemRescueCd) craps out with "Unknown error 20".

I did verify that I can create a file and write to it on hda5 (where I
put the output file for partimage) before running partimage.

Or is it possible to install partimage under Ubuntu while still running Ubunto from the liveCD?

---

### Post by mejohnsn on 2006-07-26
I just found the answer to my question about partimage on liveCD. It is 'yes'. Details at [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html).

---

### Post by sonnywise on 2006-08-12
My partitions...

sudo parted /dev/sda print
Disk geometry for /dev/sda: 0kB - 100GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    21GB    21GB    primary   ntfs         boot
2       21GB    93GB    72GB    extended               lba
5       21GB    23GB    2147MB  logical   ntfs
6       23GB    93GB    70GB    logical   ntfs
7       93GB    93GB    280MB   logical   linux-swap
3       93GB    99GB    5610MB  primary   ext3
4       99GB    100GB   1078MB  primary   ntfs

---

