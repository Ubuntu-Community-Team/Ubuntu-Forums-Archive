---
title: "partitions"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by alphaamanitin on 2012-12-08
Just got a new System76.  Going to get rid of the Ubuntu Unity crap and go to Xubuntu.  I want to have a separate /home partition and actually start backing me data up regularly.  Kind of have to for work now.  Anyway, do I need to do more that to create a / /home and swap partitions?  I just want to make sure.  I have looked through the some pages and help, but I just want to get some advice before moving on the procedure.  

Very excited for my near removal of Windows in my life.  Sadly, I will have to run Windows 7 in a virtual machine to get Adobe CS5 collection that I have to use to produce publishable quality figures for my work.  I know, inscape, but I have learned Illustrator and Photoshop and I already have enough new software to learn with the switch to linux completely.  And these are not simple pieces of software; I am a molecular biologist so it is software for manipulating sequences and the like.

Thanks,

AlphaA

---

### Post by darkod on 2012-12-09
If you want to have separate /home, you have to use manual partitioning when installing and you can create all the partitions that you want.

As for the desktop environment, I think you can install Ubuntu and add the XFCE desktop environment. When logging in you can select which one you want to use. That mght be a better option than installing Xubuntu since the software between them is not equal.

If you want Ubuntu software but another desktop environment, you can do that.

---

### Post by alphaamanitin on 2012-12-09
> **darkod said:**
> If you want to have separate /home, you have to use manual partitioning when installing and you can create all the partitions that you want.


Yes, doing the manual partitions is nothing hard, but as I asked, is it enough to make  / /home and a swap partition, or do I need to also make a /root /usr and all the other partitions.

> 
As for the desktop environment, I think you can install Ubuntu and add  the XFCE desktop environment. When logging in you can select which one  you want to use. That mght be a better option than installing Xubuntu  since the software between them is not equal.

I would advise against that method personally.  There will be bunch of bloat that you don't need and getting rid of the default desktop managers of the version you installed is a pain.  There is a website where a guy lists the full command you can just copy and paste, but I cannot remember it.  

AlphaA

---

### Post by NightsShadeQueen on 2012-12-09
I'm pretty sure /, /home, and swap are all the partitions you need.

(Haven't actually done it myself, but helped a friend move his /home from one hd to another in a 2-hd computer)

---

### Post by critin on 2012-12-09
Why not take a look at gparted or disk utility and use the partitions as they are set up now?   In other words, don't wipe the hdd, reuse the partitions.  That should answer your question of which partitions are needed.

I agree with darkrod, just add the XFCE desktop environment.

---

### Post by darkod on 2012-12-09
Linux works in mount points, so it doesn't make a difference whether /something is a separate partition or just a folder named 'something' inside /. The path would be the same in both cases.

The main system partition is called root but the mount point is /, not /root.

So, you can set many separate partitions like /usr, /tmp, /var, etc or you can leave them as folders inside /.

The minimum setup including a separate /home partition is /, /home and swap.

---

### Post by cybrsaylr on 2012-12-09
> **NightsShadeQueen said:**
> I'm pretty sure /, /home, and swap are all the partitions you need.

(Haven't actually done it myself, but helped a friend move his /home from one hd to another in a 2-hd computer)

Heard this is a good idea but have never done it as yet. How exactly do you do this and does it have to be done on your initial install? Can I modify my present setup to do this?

My PC has 2 drives: a 128GB SSD with just a 12.04 partition and a 8GB swap partition.
The other drive is a 2TB HDD split into two partitions with 1TB NTFS for Windows 7 and 1TB Ext4 for Ubuntu storage. 

Does it matter which drive has the /home partition installed on? 
And is it better installing /home on the SSD or the HDD?

Also just curious if you can you simply 'drag & drop' the 'home' folder into the 1TB Ext4 Ubuntu partition and will that work?

---

### Post by darkod on 2012-12-09
> **cybrsaylr said:**
> Heard this is a good idea but have never done it as yet. How exactly do you do this and does it have to be done on your initial install? Can I modify my present setup to do this?

My PC has 2 drives: a 128GB SSD with just a 12.04 partition and a 8GB swap partition.
The other drive is a 2TB HDD split into two partitions with 1TB NTFS for Windows 7 and 1TB Ext4 for Ubuntu storage. 

Does it matter which drive has the /home partition installed on? 
And is it better installing /home on the SSD or the HDD?

Also just curious if you can you simply 'drag & drop' the 'home' folder into the 1TB Ext4 Ubuntu partition and will that work?

You can change the existing setup. But it would be slightly better if you put the /home also on the SSD since all program settings will load much faster. On the other hand, if you keep big amount of data inside your Home, then it won't fit on the ssd. You will have to keep the large files on the hdd and get used to it.
Even if you put /home on the hdd it's not the end of the world, but you are aware the ssd is faster.

There are plenty tutorials for moving your home on google, but if you are unsure about anything, ask first.

PS. This is one link with instructions. They could have made it a bit simpler, but the procedure is correct and should work:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by NightsShadeQueen on 2012-12-09
This seems to be about right:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

(copying and pasting won't work).

My friend wanted to put home on his hdd; I don't know what's more optimal.

---

### Post by Herman on 2012-12-09
> do I need to do more that to create a / /home and swap partitions? 
Not so long ago, hard disks were relatively much more expensive that they are today and a 'large' hard disks were miniscule by today's standards. It must have been a great advantage to have been able to spread parts of a Gnu/Linux or other Unix-like operating system out over several hard disks. The sum of the space on a number of hard disks would have provided enough room to use the operating system comfortably. 'Large' in those days might have been up to 1 GB.

Then there were the days when hard disks were getting larger than most computer's BIOSes could support, and there was the 8 GB hard disk bios addressing limit, where the Gnu/Linux operating systems were able to use 'large' hard disks by having a separate /boot at the beginning of the hard disk. The idea was to fence the kernel into the first 8 GB area where the BIOS could find it at boot time, and once the kernel booted and took over the running of the computer, it had the drivers to address the rest of the operating system  spread out over the remaining disk area.

There were big old mainframe servers with hundreds of users whose cranky administrators laid awake at night worrying whether the /var would get filled up with mail and swell to such a size that it would fill up / and bring the server down. So /var had to be in a separate partition.

It's great to be able to restrict certian parts of the operating from growing too much in size if you want that, and to be able to force parts of the operating system into certain areas of a hard disk. The problem with having too many partitions is, you're fencing yourself in, and creating a potential time bomb for yourself. If you fail to plan ahead at installation time and you don't make all your partitions sufficiently larger than needed, then as you add more software and files and your operating system grows, maybe your needs change, the operating system will reach limits in some partitions while others contain unused superfluous space. You can resize partitions but it can be time consuming and inconvenient.
The use of LVM would allow the many partition sizes to be adjusted easily when needed, as opposed to conventional partitions.
 
The idea of having a separate /, /home and swap is popular these days and quite sensible. I personally prefer as few partitions as I can get away with. I don't want to waste any space in my 64 GB SSD by having too many partitions with bits of wasted space so I just have / and that's all. No swap area, my swap is in swap files dynamically created /on the fly' by swap space manager. I never need to worry about resizing partitions. I keep backups, so no need to have a separate /home. Having a separate /home does not excuse one from the need for making backups, (contrary to popular beliefs).

Recently hard disks have become larger again and 1 and 2 TB disks are now in use.  Hard disk drives are said to be the slowest part of the computer now.  In the case where a person might have a number of 1 or 2 TB disks, there may be an argument for reverting back to the old style Linux multiple partitioning schemes in order to make use of the principle of 'stroking', where the outer tracks of each hard disk is used for the partitions which will be read and written to the most. Having the operating system spread over several disk working simultaneously and using only the outer circumferences of the disk spinning at whatever rpm, where more sectors pass the hard disks read and write heads per second  is supposed to eck a bit more speed out of modern hard disks. 
I don't know if a stroked partition setup would be as fast as using the same number of hard disks in a RAID0 though.

A separate /, /home and swap are all the partitions most of us need. :)

---

### Post by Pjotr123 on 2012-12-09
> **Herman said:**
>  I just have / and that's all. (...) I keep backups, so no need to have a separate /home. Having a separate /home does not excuse one from the need for making backups, (contrary to popular beliefs).
Absolutely right. A separate /home is, in my opinion, a useless feature.... A separate swap partition is no real waste of disk space, however, as it's sufficient to allocate it the same size as your RAM (+ 100 MB or so, just to make sure).

---

### Post by alphaamanitin on 2012-12-10
> **Pjotr123 said:**
> Absolutely right. A separate /home is, in my opinion, a useless feature.... A separate swap partition is no real waste of disk space, however, as it's sufficient to allocate it the same size as your RAM (+ 100 MB or so, just to make sure).

What about for encryption?

AlphaA

---

### Post by Herman on 2012-12-10
> What about for encryption?Yes, you're right, another reason for creating extra partitions is so that the operating system can have different file systems.

Before ext4 came into widespread use, a few  Arch Linux users who were  trying to out do each other for performance used to have separate  partitions with reiserfs instead of ext3 in some partitions which the  operating system writes to often because they believed it gave a speed increase.
I  have often seen ext2 recommended as the best file system for a /boot  partition without any explanation as to the reason why. I guess it might  be to save a little disk space, as the file system itself (file system  overhead) does occupy some disk space.

An encrypted file system can be a good idea for /home.  Most of the users personal files will normally be in /home. When / and swap are not encrypted it can be slightly easier for new users to perform maintenance and repairs to their operating systems, such as file system checking and mounting to edit an important file with settings to fix a perhaps unbootable system.   

It's also possible to have a fully encrypted LUKS file system for the entire operating system including the swap, but excluding /boot. It's only a matter of learning how to use another operating system, say in a USB flash memory stick, to mount the LUKS volume and perform maintenance tasks. From a security standpoint, the fully encrypted operating system is supposed to be slightly better than just an encrypted /home.

Obviously, creating an encrypted file or file system of any kind implies that one must learn how to unencrypt the file or file system again before storing data in it. or the person risks losing access to their data. To me it makes more sense if one is going to use file system encryption, to have the entire operating system encrypted including swap. :)

---

### Post by rrnbtter on 2012-12-10
Greetings,
Without getting into the pro's and con's here is the partition formula that I use.

#1 Swap 2Gig
#2 Boot 400Meg
#3 / root 5Gig
#4 Extended /usr 15Gig
#5 Extended /Home [Remainder of drive][Encrypted]

Currently running RR 13.04 on two computers.

Good luck what ever you do.
rrnbtter

---

