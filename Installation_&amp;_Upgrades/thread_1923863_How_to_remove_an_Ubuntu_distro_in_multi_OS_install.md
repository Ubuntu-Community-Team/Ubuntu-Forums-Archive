---
title: "How to remove an Ubuntu distro in multi OS installation"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by zuheyr on 2012-02-11
Hello, 

Currently I am using Windows Vista, Ubuntu 11.04 and Ubuntu 9.10.
I want to cleanly remove the Ubuntu 9.10 and reclaim the space.
Can you please help me with that?

Many thanks for reading, regards Zuheyr

---

### Post by josephmills on 2012-02-11
for this I suggest googling how to use gparted. Here is the 1st thing that I seen 
[http://www.addictivetips.com/ubuntu-linux-tips/use-gparted-to-manage-your-disk-partitions-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/use-gparted-to-manage-your-disk-partitions-in-ubuntu-linux/)

there are many many many more but gparted should do the trick. Just MAKE SURE that it is the partition that  you would like to delete because after it is gone it is  gone'. let us know how it works out or if you run into any more questions

---

### Post by jayshomebrew on 2012-02-11
before you do anything, just realize that with any mistake you could lose important files.  Always backup your important files b4 you do any partitioning/resizing/etc. 

-boot into your 11.04 ubuntu. Run disk utility
-delete the partition of 9.04.
-open a term, run
```
sudo update-grub
```
-reboot your computer, make sure that everything is working as it should.  This means, boot into each of your OSs checking that it works properly. 
-I agree with joseph, you should use gparted to resize your partitions.  You'll have to download gparted, burn it to an dvd/cd, and boot into it. Other choices would be windows itself, under cntrl panel/administrative tools/disk manager and Acronis Disk manager (to resize partitions).  AFAIK, not all partitions can easily be resized.  For instance, if you have [encrypted partitions]("https://help.ubuntu.com/community/ResizeEncryptedPartitions"), you may have more work to do.
see: [GParted supports the following actions on file systems]("http://gparted.sourceforge.net/features.php")
see: [Acronis supported file systems]("http://kb.acronis.com/content/11342")

---

### Post by zuheyr on 2012-02-12
Thank you. 

Ubuntu and Gparted are really "foolproof".

I figured out the partition of the 9.10, 
just installed and ran the gparted, deleted the partition and resized the one at its right to reclaim the deleted space.
 
And, I did your
> **jayshomebrew said:**
> 
```
sudo update-grub
``` without which I do not know if it would work. 

Shuffling 300 GB took about 6hr on Core 2 duo desktop.

Many thanks and regards, Zuheyr

---

### Post by zuheyr on 2012-02-12
Thank you for the quick reply. 

I knew the tool was Gparted but it was very assuring to have your quick response. 

Once again my admiration and thanks go to Gparted developers. It worked like a charm but I studied it for some hours :-)

Thank you. +1 is done.

Zuheyr

---

### Post by deepak115 on 2012-02-12
I think u could just repair with the WIN cd/DVD . Then with system tools and partition manager of windows, formatting of the other OSs can also be done

---

### Post by zuheyr on 2012-02-12
I am not very familiar with the WIN cd/dvd... 
Thank you. Regards
Zuheyr

---

