---
title: "Dual boot problem. Hardware failure?"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by the-loki on 2015-05-26
Hi there,

unfortunately my system is having some trouble lately.

It's a **dual boot** machine with an Intel i5 CPU
1st SSD is Ubuntu Gnome 64
2nd SSD is Windows 8.1 (Win 10 preview)
There are also two 250GB hard disks for data (one for each os).

The system ran without issues for quite some time.

Lately I installed the KDE desktop for the Ubuntu OS but I don't think this is related to the problem. It's just a coincidence.

_Now for the actual problem:_
When booting I receive an error message (even before GRUB) for the first SSD (Ubuntu): **SMART command failed**
The system continues to GRUB.

When I select Ubuntu I get the error messages **attempt to read or write outside of disk 'hd0'** and **You need to load the kernel first**.

When I select Windows, the system will boot without problems.

My assumption is that the first SSD may be broken. 
Is there a method to ensure that? Right now I am no longer able to boot Ubuntu.

Any ideas what to do next will be apreciated.

Thanks!

---

### Post by grahammechanical on 2015-05-26
You could try 2 things. Run a Ubuntu live session and load Disks utility and see what that says about your disks. It has a drop down menu option of Smart Data and Self-Tests that you could run. Or, you could use a similar utility in Windows. If it has one.

Regards.

---

### Post by corti-nico on 2015-05-26
You can also use **smartmontool**, a tool for reading SMART raw data,
Have a look at this wiki guide to know how to install and configure:

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by the-loki on 2015-05-27
Thank you guys for your support!
I booted via a live CD. 
Neither Gparted nor Disk utils found an error on the SSD. I even ran an extended self test. Well, there is one bad block but both tools claimed that the disk is good.
Next I did a fsck, looking for more bad blocks but found nothing.
Then I tried to repair GRUB using boot-repair but it didn't work for unknown reason.
Finally I decided to re-install Ubuntu.
Now the system is working again. Funny enough, the BIOS error mentioned in my first post seems to be gone.
As there is only the OS on that SSD and no data I am willing to risk a future failure. 

So thanks again for your support.

---

