---
title: "Installing 9.10"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by stuart_g on 2009-11-13
Hello,
I'm new to this OS and I'm trying to install it on the only disk in my system. I choose to install Ubuntu then the screen changes to the Ubuntu symbol and the hard disc light is on permanantly, been like it for ages.
Is it formatting the hard drive? doesn't say it is doing anything on the screen.
I haven't got windows installed anywhere in the system, should I have?

System hard drive is a 80Gb SATA.

Any help would be appreciated

Cheers
Stu.

---

### Post by presence1960 on 2009-11-13
> **stuart_g said:**
> Hello,
I'm new to this OS and I'm trying to install it on the only disk in my system. I choose to install Ubuntu then the screen changes to the Ubuntu symbol and the hard disc light is on permanantly, been like it for ages.
Is it formatting the hard drive? doesn't say it is doing anything on the screen.
I haven't got windows installed anywhere in the system, should I have?

System hard drive is a 80Gb SATA.

Any help would be appreciated

Cheers
Stu.
You may have a bad burn or bad iso. Let's start at the beginning and go forward.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it to disk as an image?

Did you burn the iso as an image to CD at no more than 4x-8x speed? If your burning software will not allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for Infrarecorder.

If all this checks out boot the Live CD or USB if you made a bootable Live USB and choose "check disk for errors" when the menu comes up.

If all this is OK then try to install again. If it fails again boot the CD/USB again and this time choose "try ubuntu without any changes". When the desktop loads use the install icon on the desktop to install Ubuntu.

---

### Post by stuart_g on 2009-11-13
I did burn the image correctly and when I explore the disk I have various folders and files not the iso image.
I have tried to do a disk check and install without changing anything and it does the same everytime.
I'll download Ubuntu again and make another disk and see what happens.

---

### Post by presence1960 on 2009-11-13
> **stuart_g said:**
> I did burn the image correctly and when I explore the disk I have various folders and files not the iso image.
I have tried to do a disk check and install without changing anything and it does the same everytime.
I'll download Ubuntu again and make another disk and see what happens.

did you MD5SUM the iso? If you are downloading again try a torrent.

---

### Post by stuart_g on 2009-11-13
No I didn't MD5Sum it. I have installed from this disc before so sure the disc is ok.
I've just tried to do an install with my hard disc disconnected as a test and I got the exact same thing so it looks like Ubuntu can not see my SATA hard disc to install the OS to. I have this problem when installing XP and have to install a third party RAID driver as part of the windows install process.
Anyone know how I get around this to install Ubuntu?

---

### Post by Tholley on 2009-11-13
When you are installing, are having Ubuntu set up the partitions automatically or are you choosing to do the manual method? 
 
I would recommend the manual way.
 
Let me know if you need instructions on that.

---

### Post by audiomick on 2009-11-13
In this thread:
[http://ubuntuforums.org/showthread.php?t=1324518](http://ubuntuforums.org/showthread.php?t=1324518)
there is a suggestion to use the alternate CD instead of the live CD. It apparently has a different ( better? ) partition manager.

---

### Post by stuart_g on 2009-11-13
> **Tholley said:**
> When you are installing, are having Ubuntu set up the partitions automatically or are you choosing to do the manual method? 
 
I would recommend the manual way.
 
Let me know if you need instructions on that.

I don't get that far.
I boot up using the cd then choose English language, this then takes me to the options screen, if I choose install or install without making changes I get the Ubuntu screen and the HD light on permanat and that's it.

---

### Post by audiomick on 2009-11-13
You could try booting from a Gparted live CD. Then you will know that your CD drive is / is not broken, and while you're in there you can look at your HD and  set up your Linux partitions while your at it.

The suggestion to look at that other thread was because the guy in that thread was having similar problems to yours

---

### Post by stuart_g on 2009-11-13
> **audiomick said:**
> You could try booting from a Gparted live CD. Then you will know that your CD drive is / is not broken, and while you're in there you can look at your HD and  set up your Linux partitions while your at it.

The suggestion to look at that other thread was because the guy in that thread was having similar problems to yours

Yes I looked at the other thread, thanks.
I don't understand how to boot from a Gparted live CD. How do I do this?

---

### Post by audiomick on 2009-11-13
Get an .iso and instructions here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It is a bootable CD with the partitioning tool that Ubuntu uses on it.

If it boots and runs, then you know that your CD drive is working right.
When it is running, it will find your drive, and show you a graphic depicting how the drive is partitioned. You can then, if you wish, prepare in advance the partitions you need for your install.

If it doesn't find your disc, you might have a hardware problem.

By the way, I was having trouble with my Samsung discs not showing up at bootup. Part of the solution was to make sure that the cables were plugged in properly

---

