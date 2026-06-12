---
title: "Disk partitioning issues"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jeffbray on 2008-04-26
I'm currently trying to help a friend install Ubuntu on her computer, and I've encountered a problem that I didn't really expect (especially considering all of the other, more likely issues.) She's booting from the LiveCD right now, trying to install, and on the partitioning step, she's getting only two options. Guided partition using the full disk, and manual. I don't know how to run a manual partition without the looming fear of erasing everything. 

Another important note is that in the "Manual" option, "new partition" is grayed out, so any tutorials I've found that might have helped do a manual install are rendered useless by this obstacle.

If anyone has any thoughts as to why this might be happenening, I'd appreciate anything.

---

### Post by Pumalite on 2008-04-26
Xp or Vista?

---

### Post by obidose on 2008-04-26
First thing is to make sure the disk is not mounted.
Also how many partitions are on the disk allready, sometimes there can be too many main partitions on a disk.

post:
sudo fdisk -l

---

### Post by jeffbray on 2008-04-26
Alright, to answer both questions:
It's an HP Pavilion dv2000 running vista with an intel Centrino duo.

Also, there are only two existing partitions; she's got her windows C and D drives.

---

### Post by obidose on 2008-04-26
There may also be hidden partitions for windows restore or something simillar.

---

### Post by jeffbray on 2008-04-26
the command that I was given (sudo fdisk -l) only listed two devices.

---

### Post by eli_d on 2008-04-26
just to play it safe, you might want to make an image of her vista partitions using something like the command prompt program "partimage" ...  

also, i usually use the partition software (gparted) on the live booting, open source, SystemRescueCD ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) ), because the ubuntu installer partitioner has given me some trouble before.

---

### Post by jeffbray on 2008-04-26
> **eli_d said:**
> 
also, i usually use the partition software (gparted) on the live booting, open source, SystemRescueCD ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) ), because the ubuntu installer partitioner has given me some trouble before.

I dont think i understand. Can I remove the LiveCD while it's using it?

---

### Post by Pumalite on 2008-04-26
If you have 1 drive, you have to partition with the Vista partitioner and allocate space for Ubuntu. You cannot partition with the Ubuntu CD. The boot from your Ubuntu CD and go Manual. In the unallocated space, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Then press 'Forward'. The installer will take care of the rest.

---

### Post by eli_d on 2008-04-26
nope.  whether you are using the ubuntu liveCD or any other liveCD for partitioning or any other reason, you'll need to leave the disc in to keep the system running properly.  

the reason why i was recommending SystemRescueCD, is because it's independent of the ubuntu installer and anything else thats on your system, making it work smoother in many situations.  but it was probably poor advice, since you're still just as likely to "accidently" wipe out your friends vista partition using either one.

assuming you back up important files though, you'll be safe with either.

you said your friend had a C and a D.  does the D have any system files on it?  if not, you can probably delete the D (assuming you backup important files first!) so that the ubuntu partitioner will have some free space to work with.  this the reason why the "make new partition" was grayed out in the manual partitioning mode.  i'm pretty sure if you just make sure that there is some free space available (5-20 gigs preferred, independent of the C or D partitions) you should be able to use the auto partitioner in ubuntu without any worries.  of course, this will require either deleting or resizing her existing c or d (whichever one DOESN'T have vista system files).

---

### Post by jeffbray on 2008-04-26
You guys are amazing. Haha.

I guess I don't know why I didn't have to do that when I installed the same version on my laptop.

All I had to do was use windows to, basically, unallocate some of the disk for open use.

Thanks a lot!

---

### Post by Pumalite on 2008-04-26
You are welcome.

---

