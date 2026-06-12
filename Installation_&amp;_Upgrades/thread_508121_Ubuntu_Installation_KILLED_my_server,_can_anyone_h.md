---
title: "Ubuntu Installation KILLED my server, can anyone help?"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by Bensign on 2007-07-23
I've seen some other posts regarding the same problem as mine, but none specifically.  Heres' what happened.  I have two hard drives(/dev/hda, /dev/hdb)  I went through the Ubuntu installation normally, however, when it was working on partitions, it died, gave me some bug to report to Ubuntu and left my server a pile of metal.

So, I did a little research, got a copy of a knoppix CD to boot with (since I was unable to get to a terminal when using the same ubuntu CD).  Once on Knoppix, I went ahead and just destroyed the partitions on both hard drives using fdisk then made file systems for each as well.  The plan being that I just use the Ubuntu CD to go ahead and partition futher(Linux, Swap, etc).  This all worked great--I used the Ubuntu CD to install Ubuntu again on my system--error free this time.

Once the installation finished, I took out the CD and tried to reboot the system.  I got the error "Grub loading, please wait... Error 15"  I went ahead and looked up what this meant.   Apparently, something went went wrong with grub.  So I popped back in the Knoppix CD (I guess I could have used ubuntu, but felt safer going with knoppix) and tried to check out the .conf file for grub.  When I did a "ls /boot/grub" the only file there is device.map.  I'm relatively stupid in this portion of knowledge.  I never mounted the file system I created--don't know if that has anything whatsoever to do with this though.  I don't know as much as I should and was wondering if anyone can help me out.

I'll be willing to give you printouts of commands or whatever you need to help me work through this problem.  If anyone could help, I would appreciate it more than you would ever know.

---

### Post by Pumalite on 2007-07-23
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or follow these directions: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dfreer on 2007-07-23
Try making sure that the Ubuntu CD was burned correctly, you can get a md5 sum from wherever you downloaded the CD from, and the CD itself has a self-test on it. This could be a possible issue.

---

