---
title: "How do i install ubuntu on a partition made in windows?"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by cedavis8 on 2008-03-20
So i made a partition in windows with some program, i dont really think it matters, to put ubuntu on the partition. it is now called L:. I then boot ubuntu up from the live CD and double clicked install but when i got to the partitioning page there was no place to choose which drive to install it on. If i say the entire drive windows will be gone...help?

---

### Post by louieb on 2008-03-20
Sometime the partitioning program matters. Should work but if you used Partition magic - well some people have reported problems. 

To get it to use the newly created partition you a going to have to use the manual option. Click on it and edit it. make its mount point / (root), check the format box - and your done. 

Note: before you begin the install you may want to make a swap partition too . Make it about double the size of your ram up to about 1GB in size. 
Click on it too and make its mount point swap.

Might help if you looked at the install page here: [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")
good site for someone new to Linux.

---

### Post by cedavis8 on 2008-03-20
> **louieb said:**
> 
To get it to use the newly created partition you a going to have to use the manual option. Click on it and edit it. make its mount point / (root), check the format box - and your done. 

What root do i put though?? i dont know what root it is..

---

### Post by geo909 on 2008-03-20
Hmm.. Don't want to make you worry, but before you go any further
backup any important files you have in your windows system.

---

### Post by geo909 on 2008-03-20
EDIT: Please ignore this post, that was made by accident

---

### Post by louieb on 2008-03-20
> **cedavis8 said:**
> What root do i put though?? i dont know what root it is..
  Windows confuses people by calling a partition a drive the ie.. the c drive.  Linux does not look at drives and partitions the same way windows does. In Linux the file system start with / (root, root is just the name given to the start of the directory structure and the forward slash (/) is how its marked). 

Buy telling the installer to mount / (root) on this partition your saying install Linux here. Its kind of confusing at first but one you get use to it you will find it makes since.

---

### Post by cedavis8 on 2008-03-20
> **geo909 said:**
> Hmm.. Don't want to make you worry, but before you go any further
backup any important files you have in your windows system.

dammit somehow i think you might have been right. i've been trying to boot up with the live CD and now windows thinks that thats the only way to boot. it wont boot from my hard drive into windows...

---

### Post by Touch.Code on 2008-03-20
Change the BIOS settings??

---

### Post by cedavis8 on 2008-03-20
tried it...i changed the boot order to my harddrive but the computer thinks that my C: drive is the CD ROM drive...i'm gonna try to repair my installation of XP through the XP disk...

---

### Post by Touch.Code on 2008-03-20
Good idea :)

I am not having much luck either at the moment.

---

### Post by cedavis8 on 2008-03-20
....nope hard drive is screwed up. i think accidentely partitioning the drive when it booted up in linux screwed it up.....omg i hate computers...

---

### Post by cedavis8 on 2008-03-20
i have decided to format the drive and ONLY install Gutsy on it...ok this shall now be a silent thread...

---

### Post by geo909 on 2008-03-21
Wait..
It might be another way!

Just say a bit more detailed what happened..

Did you do any ubuntu installation?
Did you change your bios settings and now you can't boot to windows?

Also, even if you want to do a format, you may want to save any 
data you had on your windows system?

And if in the end you decide to do the format I would say to consider leaving a small 
partition for WIndows, especially if you're new to Linux. Ok, you will find MANY people that will disagree with me in those here forums,..
 I have XP on another partition, never boot to them, but there have been times that
I needed to:
-Run a windows program (that wouldn't work in wine)
-Handle a USB device that wouldn't work very good in Ubuntu (or just I couldn't find out  how to do it)
-Handle a very complex .doc file that I couldn't manage to view right in OpenOffice

 Also once I was given a data-DVD that was made in a stupid format that could only be read in Windows..

Ok, so that makes as something like 10 boots a year..But you'll never know when you need it..

---

