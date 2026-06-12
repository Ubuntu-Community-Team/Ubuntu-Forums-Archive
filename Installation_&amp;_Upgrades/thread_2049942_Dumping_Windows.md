---
title: "Dumping Windows"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2012-08-29
I have a Dell Dimension 4100 with two drives. Windows XP and Ubuntu 11.10 (I think) live on the C: Drive and all my Windows files are on the larger G: drive.
What I want to do is get rid of XP altogether and run only Ubuntu. Then I want to keep all my documents on the larger drive and have only the OS on the C: drive.
Not quite sure how to do that. Assume I can just drag Home folder to the G: drive? But how to make Windows go away? It is pretty much useless; can't even recognize the wireless USB I have that Ubuntu handles easily.

---

### Post by drmrgd on 2012-08-29
You might have a look at this Community Documentation for changing the mount point of /home:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I think it should be as simple as:

1.  Back up anything you care about on C\: (not only in Windows but in Ubuntu too as we'll be playing with the partition table).

2.  Make sure everything is backed up!

3. Boot to either an Ubuntu Live CD / USB or make a GParted CD / USB and boot from that. 

4. Remove the Windows partition(s), and reallocate the space to Ubuntu.  Be careful to not move or overwrite the /boot partition, as this will render your system unbootable and we'll have to fix it.

5. Using the guide in the link I posted, change your /home mountpoint from its current location to the G:\ drive.  

Note:  I believe that the /home partition must be on a Linux formatted partition (i.e. ext3 / ext4).  So, if your data on G:\ is on an NTFS partition, I think you're going to have to repartition that as well.  Someone please correct me if I'm wrong here.

---

### Post by ChrisNZ on 2012-08-29
And just to add to that - Backup all - ALL programs that save passwords, including webrowers and email!! ;D

(been there done that)

---

