---
title: "Dual boot Ubuntu / Windows 2000 Prof"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by Arjan1970 on 2005-03-02
Please forgive me when this question has already been posted but I could not find anything relating to this question. I am new to Ubuntu but I was very impressed how it looked and what it could do, so I would like to install it as an extra OS on my laptop.

I have an older Compaq Armada E500, I already found out that this would not be a problem. However I would like to keep using Windows 2000 Prof and use Ubuntu as a second OS. 

I there a ' how to'  regarding setting up a dual boot system fot these OS's or could anyone help me setting up this system for the start?

Thanks in advance for the help.

---

### Post by Gary Powers on 2005-03-02
Arjan, it (Ubuntu) really should do all the work for you.  I am dual booting W2K and Warty and it set up the GRUB bootloader with no problems.  In my case, I used Partition Magic to set up my partitions, but Ubuntu will do it for you as well.  

Interestingly, most of the dual boot probems listed here in the forums seem to deal with WinXP.  Perhaps there is simply more of those installations .....!?

Go for it!  Ubuntu Linux is fun.

Gary

---

### Post by bored2k on 2005-03-02
[QUOTE=Gary Powers]Arjan, it (Ubuntu) really should do all the work for you.  I am dual booting W2K and Warty and it set up the GRUB bootloader with no problems.  In my case, I used Partition Magic to set up my partitions, but Ubuntu will do it for you as well.[/QUOTE]

Being new to Linux/Ubuntu , i would NOT recommend Ubuntu's disk partitioner. . . it may be confusing to some and should the user emulate XP's i accept>next>next>finish  u will find urself with one partition, on OS.


Partition magic can do the right job for XP's .
Make sure ur ubuntu partition is at least 2.5 and create a smaller, maybe 400mb partition for swap area [or virtual memory...+0-]

At the partition screen [ubuntu] select custom partitioning , select ur made partition, select format partition and pick a filesystem [preferably XFS, ReiserFS or ext3], select "/" as mount point . Do the same for the swap area, only format it as swap .

Done setup , thazzit .

---

### Post by zcox on 2005-03-03
Installing Ubuntu for dual-boot with Windows is easy.  I put [this tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) together for newbies (like you and me) that gives details for installing Ubuntu alongside Windows ME (fat32) and Windows XP (ntfs).  I'm assuming Windows 2000 would be similar to XP.  You can also read [this thread](http://www.ubuntuforums.org/showthread.php?t=16287) that prompted me to write the tutorial.

---

### Post by Arjan1970 on 2005-03-09
Thank you all for the help. it worked and Ubuntu is working perfectly!!!
Thanks again.

---

