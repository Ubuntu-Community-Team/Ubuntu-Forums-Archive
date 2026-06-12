---
title: "Problem with XubunTOS installer"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by spearfish on 2008-04-14
Hi,

I downloaded the XubunTOS disk image from the Toilers page:

[http://toilers.mines.edu/Public/XubunTOS](http://toilers.mines.edu/Public/XubunTOS)

The disk image starts up fine, but the Install program gets stuck in a loop on part 4 of 7, which is, "Prepare Disk Space."

It doesn't matter which option I choose, A) Guided-resize, B) Guided-use entire disk, or C) Manual.  It always comes up with the same error:

"Failed to Create a File System
The ext3 file system creation in partition #1 of SCSI3 (0,0,0) (sda) failed."

If I use the program defaults, it fails.  If I follow the instructions in the error messages and set up a root partition (which this installer doesn't do???) it also fails.  No matter what partitions I set up, the installer says:

"You need to specify a partition for the root file system
(mount point "/") with a minimum size of 2 GB, and a
swap partition of at least 256 MB. You may also set up
other partitions if you wish."

Has anyone else run into this problem?  I'm running a fairly new computer, it is a Dell Dimension 8300 with a p4 and 1 GB of RAM.  Ug!  I need to install TinyOS for a class.  I thought they were trying to make TinyOS easier to install!  At least, that's what they promised at their last conference.

Thanks for any help on this!

---

### Post by mikewhatever on 2008-04-14
Well, nothing is ever perfect and never will be, even if the devs promise to make it good and easy.
Now to the problem. The partition program may fail for many various reasons. Instead of trying to figure them out, try Gparted live CD to pass that stage and then go on with the installer. You'll still have to specify both / and swap. The installer is smart enough not to do it automatically since / gets formatted.

---

### Post by spearfish on 2008-04-14
Where do I get the Gparted XubunTOS CD?  Or... how to I run the XubunTOS Live CD and make it use the Gnu partitioning tool instead of the buggy partitioning program it comes with?

---

### Post by mikewhatever on 2008-04-14
> **spearfish said:**
> Where do I get the Gparted XubunTOS CD?  Or... how to I run the XubunTOS Live CD and make it use the Gnu partitioning tool instead of the buggy partitioning program it comes with?

The whole point is to run Gparted as a separate program before running the installer of whatever OS. That done, you can install your OS to the pre-partitioned HDD, using the partition previously created by Gparted. Here's the home page [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by filipedelgado on 2008-05-13
Hi. My XubunTOS doesn't install Grub. How can i solve the problem?

---

