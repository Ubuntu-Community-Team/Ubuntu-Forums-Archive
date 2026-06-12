---
title: "No guided resize option"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by rlboyce0 on 2008-10-21
Hello. I am trying to install Ubuntu for the first time, and I have run into trouble.

I am using the 8.04 LiveCD in the hope of dual-booting xp and hardy, and I have no difficulty at all until I get to the prepare disk space section (step 4 of 7). I have three options to choose from: "use entire disk," "use the largest continuous free space," or "manual." Isn't there supposed to be a fourth option, "resize and use freed space?"

I don't want to erase windows by choosing "use entire disk," and when I choose "use the largest continuous free space" I am told that the free space on my disk is too small. This does not make sense as I own a 60GB hard drive with almost 30GB of free space (according to windows). 

I've defragmented multiple times and have restarted my computer with no change. The last option (manual) says that I only have 8 MB of free space along with something that says /dev/sda1 ntfs 60003 MB unknown.

I would really like to be able to use Ubuntu but will be unable to do so until I get past this step.

Do I have to use some type of partitioning program separate from the Ubuntu installation?

I thank you for your time, I'm sorry if there is a similar post, and I hope you can help me.

---

### Post by Partyboi2 on 2008-10-21
Open up Partition Editor (System>Admin>Partition Editor) on the ubuntu live cd. Then right click on your windows partitions and unmount then resize your windows partition with the resize tool so that you have enough space for ubuntu. (unallocated space)  Then run the installer again and choose "use the largest continuous free space"
Its also a good practice to backup important stuff before working on partitions.

---

### Post by rlboyce0 on 2008-10-23
Unfortunately, I am unable to chose unmount from the right click menu. There is an accompanying exclamation point inside of a yellow triangle (never a good sign). When I pull up the information about /dev/sda1, I get a huge warning message, which is as follows (I really don't look forward to typing all this):


ntfsresize v2.0.0 (libntfs 10:0:0)
Device name: /dev/sda1
NTFS volume version: 3.1
Cluster size: 4096 bytes
Current volume size: (60004 MB)
Current device size: (60004 MB)
Checking filesystem consistency...
Accounting clusters...
Cluster accounting failed at 2622607 (0x28048f): extra cluster
in $Bitmap
Filesystem check failed! Totally 1 cluster accounting
mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then
reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No
modification was
and will be made to NTFS by this software until it gets repaired.

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable


well, I guess I'll try to do the chkdsk /f thing, and I'll reply on whether or not I had success.

---

### Post by rlboyce0 on 2008-10-30
Using the suggestion from the error message resolved my problem...it allowed the resize option. Thanks again for pointing me in the right direction.

---

