---
title: "After Ubuntu installation can't access Windows"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by mikemn84 on 2006-08-09
Hello all, Ive been using ubuntu for awhile, since Hoary, and I like it so much that I decided I'd install an Ubuntu partition on my parent's machine.  They've had trouble with viruses in the past so I wanted to give them a more secure partition, essentially as a back up (and perhaps to slowly switch them to Ubuntu).  

I wanted to have 5 partitions: Windows, Ubuntu /home, Ubuntu /, linux swap, and a fat32 partition for data transfer.  I tried to make an extended partition that would hold the three parts of the ubuntu partition (/home, root, and swap), then have a partition for windows and one as the transfer partition.  Long story short, the partition editor on the live CD ran into an error and I had to quit installation.  I went back to gparted after reboot to find that the file system for the Windows partition is listed as unknown and now I can't boot into Windows.

Using the live CD, I tried using testdisk to recover the partitions but I couldn't get it to detect any partitions.  I am wondering if my Windows partition and its data is recoverable and what steps I should take.  I'm afraid that by trying to give my parents a more reliable system, I may have completely erased everything they had.  Any help would be appreciated.


I am including a screenshot of gparted and testdisk if that helps.  Notice that the partition listed for gparted is /dev/sda and testdisk is trying to use /dev/hda.

[IMG]http://imageigloo.com/images/678Img.png[/IMG]

---

### Post by randell6564 on 2006-08-10
> **mikemn84 said:**
> Hello all, Ive been using ubuntu for awhile, since Hoary, and I like it so much that I decided I'd install an Ubuntu partition on my parent's machine.  They've had trouble with viruses in the past so I wanted to give them a more secure partition, essentially as a back up (and perhaps to slowly switch them to Ubuntu).  

I wanted to have 5 partitions: Windows, Ubuntu /home, Ubuntu /, linux swap, and a fat32 partition for data transfer.  I tried to make an extended partition that would hold the three parts of the ubuntu partition (/home, root, and swap), then have a partition for windows and one as the transfer partition.  Long story short, the partition editor on the live CD ran into an error and I had to quit installation.  I went back to gparted after reboot to find that the file system for the Windows partition is listed as unknown and now I can't boot into Windows.

Using the live CD, I tried using testdisk to recover the partitions but I couldn't get it to detect any partitions.  I am wondering if my Windows partition and its data is recoverable and what steps I should take.  I'm afraid that by trying to give my parents a more reliable system, I may have completely erased everything they had.  Any help would be appreciated.


I am including a screenshot of gparted and testdisk if that helps.  Notice that the partition listed for gparted is /dev/sda and testdisk is trying to use /dev/hda.

[IMG]http://imageigloo.com/images/678Img.png[/IMG]

Can ya maybe get a hold of a DOS boot disk? Do an 'fdisk MBR' that might get you back into Windows.

---

### Post by mikemn84 on 2006-08-10
I found that boot disk but there wasnt an fdisk mbr option.  I chose fix mbr which i assume is what you meant.  It said it worked, but Windows still isnt recognized.  :confused:

Any other ideas?

---

### Post by confused57 on 2006-08-10
What about the *fdisk /mbr* command?

---

### Post by randell6564 on 2006-08-10
> **confused57 said:**
> What about the *fdisk /mbr* command?

Right, thats what I meant.

---

### Post by mikemn84 on 2006-08-10
hmm, I dont see that option either.  Maybe I have the wrong CD?  Im using the windows reinstallation CD and I went to the recovery console  to enter these commands.  I used help to list all the commands and the closest is FIXMBR or FIXBOOT.  

Also, I tried the DISKPART command and it recognizes 4 partitions:
partition 1 - 76mb ; partition 2 - 0mb ; partition 3 - 8mb ; partition 4 - 0mb.  So they are still there, but the partition type for each is unknown.

---

### Post by randell6564 on 2006-08-11
> **mikemn84 said:**
> hmm, I dont see that option either.  Maybe I have the wrong CD?  Im using the windows reinstallation CD and I went to the recovery console  to enter these commands.  I used help to list all the commands and the closest is FIXMBR or FIXBOOT.  

Also, I tried the DISKPART command and it recognizes 4 partitions:
partition 1 - 76mb ; partition 2 - 0mb ; partition 3 - 8mb ; partition 4 - 0mb.  So they are still there, but the partition type for each is unknown.

When I suggested that you get a boot disk, I didnt mean use the XP CD. I meant an old DOS boot disk.

---

### Post by confused57 on 2006-08-11
You could download the bootdisk(98SE OEM) described in this link:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Then you could use the **fdisk /mbr** command to repair your mbr.

From the Windows install cd(not a recovery cd), you'd enter **fixmbr**

---

