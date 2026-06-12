---
title: "Partitioning may have screwed my computer"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2007-02-22
I just realized I'm a newbie.  I think (I know) I made an error partitioning my harddrive while trying to install a dual boot system.  I know because my computer will not not boot.

I wanted to add Ubuntu 6.06.1 LTS (X86 version) as an alternate operating system to use surfing the internet and reading e-mail.  My computer had Windows XP x64 on it as the only operating system.  My hardware included an AMD 1.8 Ghz CPU, 2 GB RAM and a 250 Sata harddrive.  The harddrive had been partitioned into a 200 GB partition and a 50 GB partition.  The 200 GB partition contained my Windows operating system while the 50 GB partition contained some backup files.  The 200 GB partition had about 46GB of data on it while the 50 GB had about 5 GB of data.

My attempted dual boot installation was as follows:  I booted from a Ubuntu live CD.  I then clicked on the install button on the desktop and followed the instructions to the partitioning part.  I tried to use information on installing and partitioning as outlined on psychocats.net.  At the site, a favorite partitioning format was (1) Windows XP (NTFS), (2) Ubuntu /home (Ext3), (3) Ubuntu / (Ext3) and (4) swap.

Using this guide, my intention was to partition my 200 GB partition into four parts using the suggested format and allocating as (1) 96 GB, (2) 80 GB, (3) 20 GB and (4) 4 GB.  Forgetting I was trying to partition a partition.

I highlighted the unallocated line of what I thought was unused space on my 200 GB partition.  I then attempted to setup partitions of (1) 80 GB for my Ubuntu /home, (2) 20 GB for ubuntu / and (3) 4 GB for swap.  My intention was to leave the NTFS part with Windows on it alone and then create the three Ubuntu partitions at the end.  I thought I was not effecting the original 50 GB partition.

I began the partitioning and immediately got 3 error messages for the 3 partions.  I delicately tried to abort the installation by quitting the installation program and shutting down the live CD.  I then attempted to reboot without the  live CD and got an error message saying the boot had failed.

My questions:
(1) How can I fix this?
(2) Could I retrieve the files on the 50 GB partition if I can't fix it?

---

### Post by mikewhatever on 2007-02-22
Hi,
I do not understand the following part 
> Using this guide, my intention was to partition my 200 GB partition into four parts using the suggested format and allocating as (1) 96 GB, (2) 80 GB, (3) 20 GB and (4) 4 GB. Forgetting I was trying to partition a partition.

What do you mean by 'forgetting to partition'. Have you resized the 200gb partition?

You should be able to access the files on the 50 GB partitions running a live cd session. If you haven't tried to change that partition, the files should be there and intact. You'll have to mount the partition:

Open the terminal (Applications->Accessories->Terminal)
Make a mount point > sudo mkdir /media/documents
Mount the partition if the HDD is PATA> sudo mount -t ntfs /dev/hda2 /media/documents
or SATA > sudo mount -t ntfs /dev/sda2 /media/documents
then you should be able to access it though Places in the menu.

---

### Post by raj727 on 2007-02-23
Thanks for the reply.  I was starting to feel really down.

What I meant was:  I may be wrong but, I think the entire 250 GB harddrive can only be partitioned into 4 parts.  What I was doing was partitioning the 200 GB partition into 4 parts for a total of 5 parts including the 50 GB partition.

I ventured into the install again and took a look at the partition part of the install program.  It now shows:

partition----------file system---------size---------used----unused-----flags

/dev/sda1          unknown        185.55 GB       -0-             -0-            boot
/dev/sda2          extended         47.33 GB       -0-             -0-            lba
   /dev/sda5       ntfs                 47.33 GB      8.59 GB   38.74 GB
/dev/sda3          unknown           7.84 GB       -0-             -0-
/dev/sda4          unknown           0.00 GB       -0-             -0-


Could I still fix the install?

---

### Post by mikewhatever on 2007-02-23
You can only have 4 primary partitions per HDD. Redo the partitions, and make all of the Ubuntu related ones extended/logical. I still do not understand whether or not you've done the resize part.

---

### Post by raj727 on 2007-02-23
Sorry for not being clear.

I was trying to resize the 200 GB partition into the 4 suggested parts format.  I'm not sure what I actually did.  When I now go to the "Prepare partitions" part of the install, I get the above screen.

To redo the partitions, would I highlight all of the lines with "unknown" in them and then use one of the right mouse click options?  Would it be the "unmount" selection?  This would be while in the "Prepare partitions" screen.

---

### Post by mikewhatever on 2007-02-23
I am sorry, but I really am not sure what to do. You should have resized the partition first by moving the slider and then create the new ones in the unallocated space. Look at the pictures in this guide [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I hope someone knows the way out of this. The good thing is that your files on the 50 GB partition should still be there.

---

### Post by raj727 on 2007-02-23
Man was I stupid.  The same thing hit me while I was trying to sleep last night.  I should have first resized the 200 GB partition and then added the three new partitions.  

I think what I did was:  

I highlighted the large partition, 
right clicked my mouse
Chose new and then added the three partitions.
That's how I think I now have three partitions of 185.55 GB, 7.84 GB and 0 GB on the 200 GB original partition.

Is there anyone who could offer any suggestions?

---

### Post by housam on 2007-02-23
Boot from the CD and open the terminal ( applications >> accessories >. terminal ) and type :```
fdisk -l
```
and post the outcome.

---

### Post by raj727 on 2007-02-23
Hi.

I'm not sure I used the terminal correctly.  This is what I got:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$

---

### Post by housam on 2007-02-23
Ok, do it like this.
```
sudo fdisk -l
```
 ( -l ) it is a small L .

---

### Post by raj727 on 2007-02-23
Okay.  This is what I got:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24222   194563183+  83  Linux
/dev/sda2           24223       30400    49624785    f  W95 Ext'd (LBA)
/dev/sda3           30401       30401        8032+  83  Linux
/dev/sda4           30402       30402           0+  83  Linux
/dev/sda5           24223       30400    49624753+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by floke on 2007-02-23
Which LiveCD are you using?
If its Dapper or Edgy can you do this...(in the terminal)

sudo mkdir /home/[whatveveryourusernameis]/Desktop/check
sudo mount -t etx3 /dev/sda5 /home/[whateveryourusernameis]/Desktop/check

This should create a folder called 'checl' on your desktop and put your windows stuff in it
Click on the folder 'check' and see what's there
If it has windows stuff in it, you can breathe a sigh of relief.

You really should not be trying this without backing up your date, defragging your HDD + running a scandisc!

Consider yourself told off! 

Did this work?

---

### Post by housam on 2007-02-23
> **raj727 said:**
> 
   Device Boot      Start         End        Blocks                 Id            System
/dev/sda1   *           1            24222   194563183+     83           Linux
/dev/sda2           24223       30400   49624785           f  W95    Ext'd (LBA)
/dev/sda3           30401       30401   8032+                 83           Linux
/dev/sda4           30402       30402   0+                        83           Linux
/dev/sda5           24223       30400   49624753+       7              HPFS/NTFS
ubuntu@ubuntu:~$

As you see , you've formated your 200 Gb (/dev/sda1 * ) to ext3 format ( it was ntfs for windows ) which means that you deleted windows. And you already have an extended partition ( sda2 ) which has your 50 Gb partition (sda5). and created a 2 new partitions ext3 format , one with zero Gb (sda4)and the other with about 8 Gb (sda3)cuted from the 200 Gb partition.
You have a mess in your HDD. Boot from the CD and go for Gparted ( system >> admin. >> gnome partition editor. then delete the partitions no. sda1,sda3 and sda4. you'll got an unallocated space which can be divided into 2 new partitions : 100 Gb ntfs format primary partition for the new windows , the rest will be created as an extended partition which will be divided into 3 new logical partitions: 20 Gb ext3 format for the root partition (/), 1 Gb swap format for the swap partition and the rest is ext3 format for the /home partition.

then install windows first in the ntfs partition and afterwards install ubuntu. and when it comes to the step 5 select the manual partition ( which you already created ) and assign the partitions in the mount log. and continue.
Good luck

---

### Post by raj727 on 2007-02-23
Thanks for your help.

I'm using Dapper.  I got the following:

ubuntu@ubuntu:~$ sudo mkdir /home/raj/Desktop/check
mkdir: cannot create directory `/home/raj/Desktop/check': No such file or directory
ubuntu@ubuntu:~$

I think I may have done something wrong.  

BTW.  Is there someway I can do a post of the screenprint?  I've been using copy and paste which seems to lose the formatting.

---

### Post by housam on 2007-02-23
you can take a screen shot using applications >> accessories >> take a screen shot , then insert it as an attachment to your post

---

### Post by floke on 2007-02-23
I have no idea why that doesn't work - although maybe Housam will know?
Is your username raj?

---

### Post by raj727 on 2007-02-23
Yes.  That was the login name I set during the install.

---

### Post by housam on 2007-02-23
> **Steve.K said:**
> I have no idea why that doesn't work - although maybe Housam will know?
Is your username raj?

I think he doesn't have a complete install of ubuntu. he has no swap partition ( look at his fdisk -l out come) also he wrote in his first post the following:> I began the partitioning and immediately got 3 error messages for the 3 partions. I delicately tried to abort the installation by quitting the installation program and shutting down the live CD. I then attempted to reboot without the live CD and got an error message saying the boot had failed.


---

### Post by floke on 2007-02-23
Ok so maybe the path is different for Dapper - maybe you have to use /usr/home - or something - basically wprkout the path to your home directory and add 'check' to it, and try to mount as stated. If this doesn't work, then you're buggered! Reinstall windows (if you have to) and then do it properly by shrinking the NTFS partition.

** EDIT ** Previous post must have been made at same time - looks like the best bet is to install Ubuntu from scratch (I wouldn't have thought the lack of a swap partition would have made any difference, though you're right of course, turning the PC off during the installation will have messed things up royally!).

---

