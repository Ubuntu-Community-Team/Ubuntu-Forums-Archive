---
title: "Xubuntu Alternate install problems"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Bohlio on 2007-06-09
Ok guys, Im trying to install Xubuntu on a pretty old Win98 computer with 88MB of RAM (thats still enough right?) . I go throught the text installer and all is well, untill i get to the partitioning part. According to a guide i found [Here]("http://users.bigpond.net.au/hermanzone/p2.htm"), I should get something similar to this at the partition menu 
```
[!!] Partition Disks

This installer can guide you through partitioning a disk for use by Ubuntu, or if you prefer, you can do it manually. If you choose to use the guided partitioning tool, you will still have a chance later to review and customize the results.

Partitioning method:

 Guided - resize SCSI1 (0,0,0), partition #1 (hda1) and use freed s
 Guided - use entire disk
 Guided - use entire disk and set up LVM
 Manual
<Go Back>    
```
All i get is ```
 Parition Disks
??? ??? 
<Go Back>  <Continue>
```
When i hit continue, I just get a fully blue screen with a small black bar at the bottom. I can type in the bar, but no commands seem to work at all. Any help would be great :-)

---

### Post by merlinus on 2007-06-09
Did you select one of the partitioning options before pressing Continue?

-merlin

---

### Post by Bohlio on 2007-06-09
I didnt have any options at all. All it showed was what i posted above, ```
 Parition Disks
??? ??? 
<Go Back>  <Continue>
```

---

### Post by merlinus on 2007-06-09
> 
!!] Partition Disks

This installer can guide you through partitioning a disk for use by Ubuntu, or if you prefer, you can do it manually. If you choose to use the guided partitioning tool, you will still have a chance later to review and customize the results.

Partitioning method:

 Guided - resize SCSI1 (0,0,0), partition #1 (hda1) and use freed s
 Guided - use entire disk
 Guided - use entire disk and set up LVM
 Manual
<Go Back>


I see four choices.  Use the arrow keys (up and down) to move the cursor to the scheme you want to use, and then press Enter.

-merlin

---

### Post by Bohlio on 2007-06-09
Im sorry but I dont think you read my post thouroghly. That is what i ***should*** get according to the guide that i was following. All that I ***am*** getting is just the Header, Then two sets of three question marks (??? ???) and the options to go back or continue.

---

### Post by merlinus on 2007-06-09
OK -- got it.  You may indeed not have enough RAM for xubuntu.  I believe it needs 128MB.

There are other distros (e.g. damn small linux) that should run on your machine.

Good luck!

-merlin

---

### Post by Bohlio on 2007-06-09
thanks merlinus, Ill check it out.

---

### Post by louis_nichols on 2007-06-13
> **Bohlio said:**
> thanks merlinus, Ill check it out.

Do you use lvm? If yes, then I think the first point in known issues under the [release notes ]("http://www.ubuntu.com/getubuntu/releasenotes/704")applies to you.

---

