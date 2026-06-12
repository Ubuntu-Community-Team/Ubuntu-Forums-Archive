---
title: "pvcreate problem"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2006-08-10
This is my first attempt to setup LVM.

I am attempting to group 4 drives /dev/hde thru /dev/hdh.  Each drive was formatted as a single reiserfs partition using Gpartd.

When I try the pvcreate command I get the following error:
  "Device /dev/hde not found (or ignored by filtering)."

I reread the man for pvcreate and found the following statement that relates to using the whole disk:
  "For whole disk devices only the partition table must be erased, which will effectively destroy all data on that disk.  This can be done by zeroing the first sector with:
         dd if=/dev/zero of=PhysicalVolume bs=512 count=1"

After doing this, an attempt to pvcreate the volume results in this error:
 "Can't open /dev/hde exclusively.  Mounted filesystem?"

Any ideas?

---

### Post by mlind on 2006-08-10
Can you see any filesystems mounted from that device on /etc/mtab ?
Have you marked drive(s) as Linux LVM (8e) using fdisk or other partition management tool ?


Have you tried doing this while on runlevel 1 ?
```

sudo init 1

```

---

### Post by Panhead Bill on 2006-08-12
Being new to Linux, your response made no sense to me.  (That was then) 

After use of Google, I now have a basic understanding of level 1 and how to get there.  I will explore this and also research the meanings of your other questions and then respond with the results. 

The book I am using as a guide is Linux toys II, which was written for fedora core.  It made no mention of needing to use runlevel 1.

Thanks for the direction;

Panhead Bill

---

### Post by mlind on 2006-08-12
> **Panhead Bill said:**
> Being new to Linux, your response made no sense to me.  (That was then) 

After use of Google, I now have a basic understanding of level 1 and how to get there.  I will explore this and also research the meanings of your other questions and then respond with the results. 

The book I am using as a guide is Linux toys II, which was written for fedora core.  It made no mention of needing to use runlevel 1.

Thanks for the direction;

Panhead Bill

/etc/mtab contains information about mounted filesystems. According to error message you posted, lvcreate wants exclusive lock for the device. This means that no filesystem from that device must be mounted.

If you're not familiar with fdisk, install qtparted (or gparted) and try to setup LVM using graphical tools.

Dropping to runlevel 1 mean going to single user mode, and also terminates most of the processes that may cause trouble for pvcreate to succeed. Problem here is that Xserver is shutdown as well, so you need to perform everything from command line interface.

---

### Post by Panhead Bill on 2006-08-17
Okay using init 1 I was able to mark the physical volumes using pvcreate; but only after writing over the initial 512 bites using dd if=/dev/zero of=/dev/hd(e through h) bs=512 count=1.  

Then I had to restart to be able to use pvcreate successfully.

Now the problem is with vgcreate. 

 I was able to use lvcreate on one drive, but even after reformatting it as rieserfs with gparted, writing over the first 512 bites with the dd command, I cant pvcreate it: can't initialize physical volume "/dev/hdf" of volume group "vg0" without -ff

I'm obviously doing something basic incorrectly.  

Where do I find more info on lvcreate than the man page?  My initial search of the web found a better display of pretty much the same info as the man page.  

I think I need to eliminate the volume group "vg0" associated with the drive, and also learn how to properly create the volume group and include or add the 4 drives.

Where can I find more info on LVM and how to add drives to a volume group?
Or do I create (in my case) 4 different volume groups and combine them using lvcreate?

The book I'm using (Linux toys 2) isn't clear, and so far my searched of the ubuntu site and googleing have given me too many paths to explore without seeming to be anywhere near what I need to learn.

TIA

---

### Post by mlind on 2006-08-17
I've created LVM setup using Ubuntu "alternate cd" installer.
This HOWTO should help though [http://www.tldp.org/HOWTO/LVM-HOWTO/commontask.html](http://www.tldp.org/HOWTO/LVM-HOWTO/commontask.html)

I think you're doing something essentially wrong here.. Why are you using dd? LV's are the last thing you should be doing with LVM tools, then just create filesystem inside LV using mkfs.

---

### Post by Panhead Bill on 2006-08-21
Let's see if I can distill the steps from the book:

"Mark your device as a Physical Volume"
  # pvcreate /dev/hde

"use this to verify that you have successfully  marked your device as a Physical Volume"
  # pvdisplay

"Create a volume group, chop up into 32MB PE chunks and name vg0"
  #vgcreate -s 32M vg0 /dev/hde

"allocate all free PE's for use in the volume group"
  #lvcreate -l 3516 vg0 -n videoLVM

 - - - - - - - - - - - - - - - - - -
 
My first problem was with pvcreate. When I tried the pvcreate command I got the following error:
"Device /dev/hde not found (or ignored by filtering)."  

Checking the man page indicated that when using the entire disk as one partition, the first blocks had to be cleared using the dd command.

After clearing the blocks with dd, pvcreate worked.

I tried to use vgcreate as directed, and after the first drive was successfully created, the remaining drives gave an error (I'll have to re-create the actions to get the wording but it seemed to indicate that the name vg0 was already in use)

Hitting that roadblock, I figured that I should start from scratch.  I reformatted the 4 drives, used dd, restarted and tried pvcreate again. This time one drive errors out with:

cant initialize physical volume "/dev/hdf" of volume group "vg0" without -ff 

Tomorrow I'll read the lvm howto and see what I can learn.

---

### Post by mlind on 2006-08-21
I'm not sure where LVM writes all of it's information, but vg0 probably still exists, that's why it wants you to use -force

From pvcreate manual page
> 
-f, --force
      Force  the creation without any confirmation.  You can not recreate (reinitialize) a physical volume belonging to an existing volume group.  In an emergency you can override this behaviour with -ff.


If this starts to be too confusing, I suggest you to download Ubuntu "Alternative" install cd, and boot using it like you would be doing an install. Intaller contains simple text-based interface for setting up partitions and LVM volumes. You quit the installer after you've confirmed changes to partition table.

---

### Post by Panhead Bill on 2006-08-22
Well, I'm trying to learn the commands and use of the terminal.  But that is because I ran into problems using the install CD.

(This is from my foggy memory of a couple of months ago):  I believe that when I tried to use the disk to set up the LVM I couldn't see the disks that were on the PCI controller.

  This is a 5 hard drive PC one 80 gig for the system and applications, 4 on a PCI Rocketraid controller board (used only as drive controller - not raid)

---

### Post by Panhead Bill on 2006-08-25
vgcreate is now the problem command.  All 4 drives (hde, hdf, hdg, hdh) completed pv create and show the correct info with pvdisplay.  when I try vgcreate;

#vgcreate -s 32M vg0 /dev/hde /dev/hdf /dev/hdg /dev/hdh
 
I get the following error:  

/dev/hdf not identified as an existing physical volume

unable to add physical volume "/dev/hdf" to volume group vg0

Note:  the error is always referring to the second drive in the vgcreate command, I have tried several combinations of drive orders my attempts.

This "should" work, as it seems to be the same command as the example in 13.1.2 of the LVM how to.

Any ideas?

---

### Post by mlind on 2006-08-25
> **Panhead Bill said:**
> vgcreate is now the problem command.  All 4 drives (hde, hdf, hdg, hdh) completed pv create and show the correct info with pvdisplay.  when I try vgcreate;

#vgcreate -s 32M vg0 /dev/hde /dev/hdf /dev/hdg /dev/hdh
 
I get the following error:  

/dev/hdf not identified as an existing physical volume

unable to add physical volume "/dev/hdf" to volume group vg0

Note:  the error is always referring to the second drive in the vgcreate command, I have tried several combinations of drive orders my attempts.

This "should" work, as it seems to be the same command as the example in 13.1.2 of the LVM how to.

Any ideas?

Have you tried creating volumegroup with only one drive, then use **vgextend** to add more drives to the group?

This *could* be a bug with Dapper's LVM tools, another user was reporting the same behaviour..

---

### Post by Panhead Bill on 2006-08-29
vgextend worked.  I created the vol group w/ vgcreate and one drive and then was able to add the remaining disks.

I checked out the bug list and two of the bugs seem to be related to my experiance with vgcrearte.

Thanks for the help!

---

