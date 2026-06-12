---
title: "Mounting Partitioned Hardrive"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by Goober on 2005-04-28
Hello,

Ok, let me explain my situation.  I have 2 hardrives, C and F.  My Windows died, and I am using Linux to save my Data on those 2, to reformat the drives, and reinstall Windows.  Linux is installed in a patition of drive F, which is the slave, or, more politically correct, secondary hardrive, C being the primary.  I have successfully mounted the C drive using [This](http://ubuntuguide.org/4.10/index.html#mountunmountntfs)

Now, i want to mount the other Partition of my F drive, which I used for extra storage for my Windows.  How do I do that?  I assume I change the "hda1" bit of the code in the link above.

Also, I suspect that Linux might have reformatted that Drive.  How do I find out if that happened?

Thanks,

Goober.

---

### Post by nad on 2005-04-28
The command: dmesg | grep -i hd  will list your detected ide devices and their designations.

The device /dev/hdd2 describes the second partition on your fourth ide device.

As far as detecting partitions and filesystems. The command: parted /dev/hdd print > hdd.txt  will create a text file, hdd.txt, with information about this drive.

---

