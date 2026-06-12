---
title: "Windows not recognised by Ubuntu 9.1"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Jeyaprakash on 2010-04-28
In my system, I had installed windows XP first and had deleted one of the partitions (made free space.I am not a techy. I dont know the exact term). In that space, I have installed PC Linux OS (Linux). Now, I want to use that free space to Install Ubuntu by removing the PC Linux OS. When I boot with the live CD of Ubuntu 9.1 to install, in one of the steps, it says the system does not have any OS. It neither recognises windows nor the other linux. Kindly help me. What should I do now. Could I manage to install Ubuntu without completely formatting the system all again.

---

### Post by oldfred on 2010-04-28
Welcome to the forums.

Since you want to use the same partition(s), you should use manual install. You must know which partition is the old install.

Shows mostly the standard install, not the manual version:
Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

With manual install you choose the partition, specific what it is - / (root) and what format. If you have an existing separate /home you select it but then select do not format. It seems to find your existing swap without any help.

---

### Post by Gbeattie on 2010-04-29
you say that ubuntu does not see any other operating system already installed. Is it the case that ubuntu doesnt see any hard drive?. If thats the case, Boot from the live cd. Use the try without changing anything on your pc. open a terminal...start/accessories/terminal and type in sudo apt-get remove dmraid and hit enter. Hit Y to agree and enter. When it finishes... close the terminal. then use the install icon on the desktop. when you get to the option of where to install it on your hard drive, choose manual and install ubuntu on the pclinux partition

Hope thats clear and usefull

---

### Post by P4man on 2010-04-29
Ive seen several reports of people where the installer did not detect windows, but it does recognize the partitions, and after installing, it dual boots just fine.

I concur with oldfred, just do manual partitioning. You have to understand that an ubuntu install requires:
- one "/" partition formatted as ext3 or 4. this is where the OS goes
- one swap partition (doesnt require formatting)

you probably have those partitions already from pclinuxos. Just select the pclinux one  and change the mountpoint to "/" and check the format toggle.  If you dont have them, create them in unpartitioned space.

optionality, but a good idea, make one /home partition (formatted as ext3 or 4). Home partition will contain all user settings and documents. If you dont make it, it will become a folder on your root partition

---

### Post by Jeyaprakash on 2010-05-03
I thank everyone for their kind replies. Sorry for a very late response. I was off for a few days. 

My problem is not yet solved. Kindly help. I shall try to describe the situation.

Once I boot the live CD and run the Linux and open installation, in the fourth step, it gives only two options, Use the 80 (my entire hard disk capacity) by deleting all the content and the second option is the specify partitions manually. But, in that, it shows only a single stretch (same color) and does not recognise any data with different colours. Kindly have a look at the screen shot. If fear losing data if I continue with the  manual installation. I have also attached the screen shot of the next step (5) after selecting manual partitioning. 

Kindly have a look and guide me on how I should proceed.

[http://ubuntuforums.org/picture.php?albumid=1805&pictureid=6049](http://ubuntuforums.org/picture.php?albumid=1805&pictureid=6049)

[http://ubuntuforums.org/picture.php?albumid=1805&pictureid=6050](http://ubuntuforums.org/picture.php?albumid=1805&pictureid=6050)

Regards and thanks
Jeyaprakash

---

### Post by P4man on 2010-05-03
That is .. most strange. Never saw that.  I think something is very wrong with your partition table, and I would recommend you try and fix it before doing anything else. You might want to start running chkdsk in windows or some other utility to repair corrupted partition tables.

Out of curiosity, if you open a terminal in the live session and you type in

```
sudo fdisk -l
```

(SUDO FDISK -L in lowercase)

what does it show?

---

### Post by Jeyaprakash on 2010-05-03
Thanks for your curiousity.. This is what it displays.. 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/sda2   *        5101        7012    15358140    7  HPFS/NTFS
/dev/sda5               1        2550    20482812    7  HPFS/NTFS
/dev/sda6            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda7            7013        8031     8185086   83  Linux
/dev/sda8            8032        8452     3381651   82  Linux swap / Solaris
/dev/sda9            8453        9729    10257471   83  Linux

---

### Post by P4man on 2010-05-03
Looks like a bug in either gparted or ubiquity, since fdisk seems to recognize the partitions just fine and isnt complaining about there being an issue. 

Perhaps you can try booting the cd, and rather than selecting the live session, select "install ubuntu" from the main menu. It will gave you pretty much the same wizard but no live session (andperhaps not this issue). See if then it recognizes your partitions correctly. Alternatively, try the.. alternate cd if you must have 9.10, or considering giving ubuntu 10.04 a spin.

---

### Post by dino99 on 2010-05-03
need grub on /dev/sda7

sudo grub-mkconfig && update-grub

---

### Post by P4man on 2010-05-03
Dino did you even read the thread? He hasnt even installed ubuntu yet and the ubiquity partitioner isnt seeing any partitions. Grub isnt his problem (yet).

---

### Post by Jeyaprakash on 2010-05-04
Hope there was some serious bug. In the windows, when I was checking the disks, there was an additional unallocated partition and when I added the size of the partitions individually, it was more than the size of my hard disk. In the command prompt, when I entered and typed 'dir', it was showing some symbols and no folders.
When I tried to remove that unallocated partition, the windows did not boot. So, I entered the system with live CD (Ubuntu 9.1), copied the necessary files to my pendrive and tried installing Ubuntu giving the option, use the entire hard disk. Then also it ended up in an error message saying there is some problem in the disk.
Then, I booted the system with an Win XP cd and made a complete format of the system and stopped the process immediately after formatting and booted again the system with Ubuntu live CD and used the entire hard disk for Ubuntu. Now, everything is over and I got my system working with Ubuntu 9.1.

Now, there is an icon near the clock showing the hard disk with an exclamatory mark (Ubuntu desktop). It says disk has many bad sectors. If I get into the details, the assessment is good for all the attributes except "Reallocated sector count". For this under the assessment coloumn, it says 'warning' and the value is shown as 'Normalised 100, worst 100, threshold 5 and value 131097 sectos' I dont understand this. Probably this is a problem related with the earlier disk problem. Is this a serious problem or the continuing problem of the same bug. Should I do anything on this? When I was working with Windows, I did not come across any errors related to this and was working fine.

---

### Post by P4man on 2010-05-04
Sounds like your harddisk is dying. I was actually gonna suggest that before you wrote the above post.

relocated sectors are parts of the drive that can no longer be reliably read or written to. The drive will automatically remap those whenever it can. A few bad ones can happen, especially if you ever drop it or bump it hard while its running, but that many and the fact you couldnt even format initially, Id say you are going to go from one problem to the next. Pick up a new drive is my advice.

---

### Post by oldfred on 2010-05-04
I thought early in 9.10 some had the disk error and it was not actually a disk problem. Have you updated everything?

---

### Post by P4man on 2010-05-04
Yes, there have been a few (rare) cases of false positives with palimpsest.

 But considering what occurred under windows to the OP, I highly doubt thats the case here. It would mean he has encountered a rather obscure bug in ubiquity, and coincidental at the same time some random filesystem corruption in windows and then a palimpsest bug reporting a false positive. 

Anything is possible, but with an old 80GB drive, Id say the odds are firmly against it.

---

### Post by Jeyaprakash on 2010-05-04
I updated the Ubuntu and the error is gone. Probably it was because of a bug. The windows chkdsk was reporting zero bad sectors. My hard disk is not very old. It is just two years old. In India, 80 GB hard disk was a great size two years back...

Thank you very much for all the valuable suggestions. Now everything is fine. Hope to explore Ubuntu and learn more.

---

### Post by P4man on 2010-05-04
chkdsk is meaningless, it only tests the filesystem it can not test the physical sectors. If your drive really is failing, the drive will remap the bad sectors and filesystem level utilities can not detect that. 

Try running another smart diagnostics utility like smartmontools:
[http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

runs no both windows and linux.

---

### Post by Jeyaprakash on 2010-05-05
Thank you for suggesting a good tool. I installed and ran the test. The system passed the test without any errors. Thanks again.

---

