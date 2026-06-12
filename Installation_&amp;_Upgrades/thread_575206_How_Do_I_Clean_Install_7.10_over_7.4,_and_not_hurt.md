---
title: "How Do I Clean Install 7.10 over 7.4, and not hurt WinXP?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by sooke on 2007-10-13
I'm sure this is a moronic question.  Sorry for that.  I guess I need some hand holding.

I have one HD (120 MB) with 3 partitions:

1) WinXP
2) Ubuntu 7.4
3) Ubuntu swap

I want to:

A) Reformat Ubuntu 7.4 partition
B) Install Ubuntu 7.10 over it.
C) Not screw up my WinXP.

Please don't suggest that I just update Ubuntu.  I managed to hose my Ubuntu 7.4 a while back.  Besides, it had no data I care about anyway.  So instead, I want to just format and install over it with Gutsy.

Sounds simple, but I'm not very bright.

So I have downloaded and burned a Ubuntu 7.10 CD.  I get as far as the "Prepare Disk Space" dialog box.  It has 3 options:

1. Guided - resize SCSI1 (0,0,0), partition #2 (sda) and use freed space
2. Guided - use entire disk
3. Manual

Now, it seems to me I don't need to repartition/resize anything.  I did that 6 months ago when I installed 7.4.  So I should choose 3. Manual, right?

Manual option says my partition table looks like this:

/dev/sda
  /dev/sda1  ntfs   62,915 MB (12,400 MB used)
  /dev/sda2  ext3  54,739 MB (3,200 MB used)
  /dev/sda5  swap   2,377 MB

So, I think I want to format sda2 and make it bootable, and somehow tell the intaller to use sda5 for swap.

My biggest concern is to not screw up my WinXP partition (which looks like sda1).

Can someone take pity and walk me through how to do this?

Thanks,

Sooke

---

### Post by rsambuca on 2007-10-13
Actually, it looks like you have everything covered.  When you do the manual partitioning, just direct it to mount /sda2 as your '/' (root), and sda5 as your swap.  It will automatically format both of them during the installation process.  Grub will be installed as usual, and should auto-detect your Windows partition.  Even if it doesn't automatically detect Windows (which a few people have found), we can give you very easy and quick instructions on how to add XP to the grub menu.

---

### Post by sooke on 2007-10-13
Thanks for the quick reply rsambuca.  Unfortunatley I am not sure how to tell the installer to mount sda2 as root.  I see that by doing "edit partition" I can change the "mount point".  So should I change the sda2 mount point to '/'?

The reason I hesitate, is because sda2 mount point is already listed as /media/sda2.  And that works for Ubuntu 7.4.  So it seemed wrong to change it to /.  

And to specify sda5 as swap, how do I do that?  The partition table already lists it as swap.  Does that mean I don't have to do anything more?

Thanks again,

Sooke

---

### Post by rsambuca on 2007-10-13
> **sooke said:**
> Thanks for the quick reply rsambuca.  Unfortunatley I am not sure how to tell the installer to mount sda2 as root.  I see that by doing "edit partition" I can change the "mount point".  So should I change the sda2 mount point to '/'?
Yes, that is what you want.
> **sooke said:**
> 
The reason I hesitate, is because sda2 mount point is already listed as /media/sda2.  And that works for Ubuntu 7.4.  So it seemed wrong to change it to /.  
The partitioner is basically just trying to guess where to put things when looking at pre-existing partitions.  In this case, it guessed wrong and you have to tell it specifically where to mount your '/' directory.
> **sooke said:**
> And to specify sda5 as swap, how do I do that?  The partition table already lists it as swap.  Does that mean I don't have to do anything more?If it already shows sda5 as your new /swap, then you don't have to do anything.

Because you want to save your XP partition, the most important thing for you is to make sure that you **do not format the /sda1 partition**.

---

### Post by sooke on 2007-10-13
Thanks again for the help rsambuca.  Everything worked fine.  Both Ubuntu and WinXP are working.

I realize now the installer defaulted to showing the mount point of my sda2 partition from the perspective of the install CD.  Which would be /media/sda2.

This is great.  In 7.4 I could never get my screen resolution above 1024x768.  Tried a lot of suggestions I saw on this forum, but nothing worked.  7.10 fixes the issue out of the box.  Finally my Ubuntu makes use of the whole screen.

Sooke :)

---

### Post by rsambuca on 2007-10-14
Good stuff!  Happy Ubuntuing. :)

---

### Post by willi-schlunz on 2007-10-17
Hello,

this sounds like a problem got too.  I am a bit afraid of installing Ubuntu 7.10 with my laptop. Well the difference is that I would like to install it onto an external drive (which is connected via usb).

Can I select the USB-drive when I choose 'Manual' in the "Prepare Disk Space" dialog box?

I would like to use the USB-Drive only partly for linux but else as data storage to go.

How can I perform that safely for my WINXP kept running on the laptop?

Thanks for the well documented manual!

willi-schlunz

---

