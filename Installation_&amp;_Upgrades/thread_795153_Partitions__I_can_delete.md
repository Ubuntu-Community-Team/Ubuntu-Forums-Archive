---
title: "Partitions  I can delete"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by jbullfrog on 2008-05-15
Hi all, I am a newbie to Ubuntu, and really want to switch over from Vista (which I have grown to dislike even more and more).

I have a Dell vostro 1400, and am trying to install ubuntu using the Wubi installer.

I want create a new partition, and then install ubuntu solely on that new drive.  

When I loaded a Gparted live disk, I saw that I had multiple partitions.

Which ones can I delete?  My partitions are as follows:


/dev/sda 1			fat 16

/dev/sda 2			ntfs			recovery

/dev/sda 3			ntfs			OS

/dev/sda 4			extended	

unallocated
/dev/sda 5

BTW, I have all the backup disks from DELL.

---

### Post by ssican on 2008-05-15
See this information on Ubuntu8.04 Release Notes;

Wubi

When Wubi is run from an up-to-date Windows Vista system it will eject the Ubuntu CD when it is done preparing the installation environment, however this will cause Wubi to crash ([https://bugs.launchpad.net/wubi/+bug/204128](https://bugs.launchpad.net/wubi/+bug/204128)). To avoid this problem, please press Start and click on Computer then right click on the CD drive in the window that opens. Select explore and look for a file named "wubi" or "wubi.exe". Copy and paste this file to your desktop and run it from there. Alternatively, you can download Wubi from [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi) and run it from the location you saved it to.
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

---

### Post by jbullfrog on 2008-05-15
[IMG]http://jeremiahstonybrook.googlepages.com/2008-05-15_071924.jpg/2008-05-15_071924-full;init:.jpg[/IMG]

---

### Post by jbullfrog on 2008-05-15
> **ssican said:**
> See this information on Ubuntu8.04 Release Notes;

Wubi

When Wubi is run from an up-to-date Windows Vista system it will eject the Ubuntu CD when it is done preparing the installation environment, however this will cause Wubi to crash ([https://bugs.launchpad.net/wubi/+bug/204128](https://bugs.launchpad.net/wubi/+bug/204128)). To avoid this problem, please press Start and click on Computer then right click on the CD drive in the window that opens. Select explore and look for a file named "wubi" or "wubi.exe". Copy and paste this file to your desktop and run it from there. Alternatively, you can download Wubi from [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi) and run it from the location you saved it to.
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

Thanks for the info, but this is not relevant to my problem.

---

### Post by Sef on 2008-05-15
> /dev/sda 1 fat 16

/dev/sda 2 ntfs recovery

/dev/sda 3 ntfs OS

/dev/sda 4 extended

unallocated
/dev/sda 5


1) What do you have fat 16 for?  

2) I would put Vista on sda1.  Windows like to be on the first partition.

---

### Post by logos34 on 2008-05-15
The easiest thing to do would be to delete the last partition, 2.50 gb (primary? extended?), then shrink vista partition down a few gigs (be sure to use vista's built0in tool for this), create an extended partition out of the new space and install ubuntu there.

---

