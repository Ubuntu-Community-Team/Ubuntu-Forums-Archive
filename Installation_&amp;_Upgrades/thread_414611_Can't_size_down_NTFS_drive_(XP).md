---
title: "Can't size down NTFS drive (XP)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mjitkop on 2007-04-20
Hi everybody! This is my second post! I have been playing with the Live CD of Ubuntu 6.10 this week for the first time and I found out a couple of days ago that 7.04 was being released yesterday. I got it! In fact, it is running right now (Live CD) as I type this message. :popcorn:

I wanted to install it on my hard drive but I am having problems resizing it. I have 2 hard drives in my PC:  
1/ 120 GB drive that contains Windows XP and all my documents (NTFS) and 39 MB of this drive is FAT16 with stuff pre-installed by Dell
2/ 20 GB drive with music and videos (NTFS)

I wanted to resize my first drive to make room for Ubuntu but GParted fails. Please see the screen shots. I don't understand the error message. :confused:

Thank you in advance for your help. :)

---

### Post by heimo on 2007-04-20
Try running defrag and perhaps chkdsk on your NTFS partition couple times, backup all your valuable data and try again.

---

### Post by Gavigan280 on 2007-04-20
I had a similar problem to this on my laptop.  I ran a stand-alone version of GParted and it gave me a more descriptive error message telling me that there were damaged sectors on the hard disk.  May or may not be the same problem you're having though.

---

### Post by JT673 on 2007-04-20
> Please try to free up less space.

Now there's something you don't everyday XD...

My advice would be to use another partitioner...Try [PartitionLogic.]("http://partitionlogic.org.uk/download/index.html")

---

### Post by orb9220 on 2007-04-20
Yep gpart choked on my xp partition because it was not defraged.

---

### Post by mjitkop on 2007-04-20
Thank you all for your replies. 

Now that you have mentioned it, I think it could indeed be a defrag issue. I have been wanting to defrag my drive for a long time because of poor performance of my PC but never got to it.   

I will also run a chkdsk as suggested because I might also have bad sectors; this drive is getting old. :lolflag:

Thanks for the link to PartitionLogic. I will get it even if I don't end up using it right now for this specific issue if a defrag and/or chkdsk solve the problem.

Thank you all. Ubuntu is great! :popcorn:

---

### Post by mjitkop on 2007-04-20
I was reading the documentation provided on the Live CD and it is interesting to note that defragmentation should be done before installing Ubuntu for dual boot:

> **Setting up a dual-boot configuration**

                                  This section provides the procedure required to set up a dual-boot system with Ubuntu and **Windows XP**.[LIST=1]
[*]             From within Windows, run the Windows defragmentation tool on the C drive. This can be accessed by going to Start &#8594; Run, typing *defrag* in the box provided and then pressing **OK**.
[*]             Defragmentation may take a very long time, up to several hours. Once it has finished, insert your Ubuntu Desktop CD into your disc drive and reboot your PC.
[*]             Follow the instructions given in the [Installing Ubuntu]("file:///D:/disctree/extra/switching-guide/installing.html") chapter until the installer shows the screen titled *Prepare disk space*.[/LIST]
I know what I'll be doing tonight. :lolflag:

---

