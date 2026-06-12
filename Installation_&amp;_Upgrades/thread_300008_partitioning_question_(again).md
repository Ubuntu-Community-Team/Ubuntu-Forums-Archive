---
title: "partitioning question (again)"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Tanel on 2006-11-15
Hi 

I've fresh with ubuntu and until now I have only used ubuntu in live version, running it from CD drive. But yesterday i tried to install ubuntu 6.06 into harddisk. I got the error message that hard disk is running out of space.
I took a closer look and found that ubuntu can use only 1,9 Gb from 19Gb disk

I couldnt make the space bigger using partition tools included in package.

What should I do to increase the partition volume?

thanking in advance

---

### Post by louieb on 2006-11-15
Very interesting attachment. Looks like it is reporting that the hard drive is 1.9 gig total. What created it?
Open a terminal window and post the output of ```
sudo fdisk -l
``` 
Then maybe I can help.

---

### Post by Tanel on 2006-11-15
meanwhile i did some changes (from auto to large) in bios and now it shows the disk volume 2111MB


Edit: i also added another thumbnail, perhaps somebody can read something neccesary from that

---

### Post by bulldog on 2006-11-15
Well you can make nice pictures :D 

I don't think you want any help from us,because you don't respond on what louieb asked you.

So have a nice day.:D

---

### Post by Tanel on 2006-11-15
> **bulldog said:**
> Well you can make nice pictures :D 

I don't think you want any help from us,because you don't respond on what louieb asked you.

So have a nice day.:D


If i know what created this situation and how to overcome it i wouldnt ask help. 
The disk was empty, although I used it before with win98.

Edit: Or you mean that i should post the content of the terminal window instead of making screenshot?

---

### Post by Tanel on 2006-11-15
the content of terminal window:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 2111 MB, 2111864832 bytes
16 heads, 63 sectors/track, 4092 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

---

### Post by louieb on 2006-11-15
Well fdisk says your hard drive is 2.06 gig. (2111 mb). About the same as the screen shot sent earlier.

Also your fdisk output is not normal in that it does not have partition information following the drive info.
  
That means 1 of 2 things.
1. You have a two gig drive not a 20 gig drive.
or because of the abnormal fdisk output.
2. Bios is reporting the wrong drive size.

What I would try. Reboot the machine and go into the BIOS setup. Look for something called Auto Detect hard drives. If that is there then use it. If  not then I look for something that list the hard drives and make sure detection is set to [COLOR="Red"]auto[/COLOR] and that [COLOR="Red"]mode is set to LBA. [/COLOR]

Oh I just noticed that you changed detection from Auto to Large. That should be the screen where you would set the mode to LBA. 

Try it and let us know what happened.

---

### Post by Tanel on 2006-11-16
I did according to Your directions and after several restarts system finally found that the hard disk is really 20GB

So its up and running

Thank You Louieb

---

