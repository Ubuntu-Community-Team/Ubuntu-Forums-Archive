---
title: "No devices detected (GParted)"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by timbounceback on 2007-03-04
My father has watched me use Ubuntu for about a year now, and is finally interested in giving it a try. Unfortunately, when installing, I get to the partitioning stage, and it gives me only the option to partition manually. This is fine, so I select this step, but when GParted starts, I let it search for devices, but it doesn't find any ("No devices detected." on the bottom). Has anyone had this problem before, and found any solutions?

Thanks, Tim

---

### Post by wpshooter on 2007-03-04
First, do you absolutely know that you have a good burn of the Ubuntu CD ?

Have you checked the integrity of the CD by running the verification function found on the initial Ubuntu boot screen menu ?
 
What type of hard drive is it ?  IDE, SATA, SATAII or SCSI ?

---

### Post by timbounceback on 2007-03-04
> **wpshooter said:**
> First, do you absolutely know that you have a good burn of the Ubuntu CD ?

Have you checked the integrity of the CD by running the verification function found on the initial Ubuntu boot screen menu ?
 
What type of hard drive is it ?  IDE, SATA, SATAII or SCSI ?
1. I'm pretty sure, as I've tried 2 differenct ubuntu cds.
2. no, but i will, and will post the results when it is done
3. after some quick googling, it looks like a sata (the notebook is a dell inspiron 1501)

---

### Post by timbounceback on 2007-03-04
0 checksums failed

---

### Post by konungursvia on 2007-03-04
Do you have an external or removable drive connected via USB? If so, unplug it and try again with the installer only needing to detect your internal hard drive.

---

### Post by timbounceback on 2007-03-04
No, I don't.

---

### Post by timbounceback on 2007-03-04
OK, I burnt the alternate install cd and that doesnt work either..

---

### Post by mronkko on 2007-03-05
I have exactly the same problem,  /dev/hda is not detected at all. This happens with Feisty Herd 5.  No problems with Edgy.  This is a SATA drive. 

mikko

---

### Post by pela020 on 2007-03-07
I have the exact same problem. Finally convinced my wife that "going ubuntu" is a good idea and then it doesn't work. So frustrating. Tried both the live and the alternate disc. The disc is SATA II.

---

### Post by mountielad on 2007-03-07
I have the exact same problem (Dell Inspiron) posted in Absolute Beginners Talk.

It seems there's a programme about to solve this but no one has specified where?

---

### Post by mountielad on 2007-03-07
Check out a thread I started and a cool guy has provided a few excellent links:

[http://www.ubuntuforums.org/showthread.php?t=378379](http://www.ubuntuforums.org/showthread.php?t=378379)

and

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

Seems many other 1501 users have had the same problem.
I'm not technically minded so I'm going to let a friend help me out.

---

### Post by pela020 on 2007-03-08
Have you tried this?
[http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html)

---

### Post by pacnwguy on 2007-12-19
I had this same problem on my HP8510w laptop. I couldn't find a solution posted anywhere but in exploring the ROM-based setup options I did find a device configuration setting in the system configuration area called 'SATA native mode'. I disabled it and the hard drive started showing up in GParted.

---

### Post by cafferj on 2007-12-29
I have the same problem. The live CD for Feisty did not recognize my SATA drive. I tried Open Suse and it was able to recognize the drive. Strangely, I was able to install Edubuntu from the install disk. To see if it was a gparted problem, I booted up Puppy Linux and the gparted program failed to detect the drive. Ubuntu should consider using a backup partitioner.:confused::confused:

---

