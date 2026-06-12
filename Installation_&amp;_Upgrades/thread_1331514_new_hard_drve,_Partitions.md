---
title: "new hard drve, Partitions"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by dennisofnewport on 2009-11-19
I just bought a SATA 500GB hard drive and am wondering how I should partition it before I install Ubuntu 9.10? I am not sure if I will ever share it will another OS. Does splitting it up into small partitions speed it up in any way?

Thanks

---

### Post by ricardo.gloe on 2009-11-19
I don't think having more than one partition actually speeds anything up, but the order of your partitions may affect speed. At least having a separate /home partition allows you to do a clean install without losing your /home. 

I suggest you have a look at some ubuntu partitioning schemes to help you decide.

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html)

[http://ubuntuforums.org/showthread.php?t=172347](http://ubuntuforums.org/showthread.php?t=172347)

[http://ubuntuforums.org/showthread.php?t=195800](http://ubuntuforums.org/showthread.php?t=195800)

---

### Post by florus on 2009-11-19
I would suggest:
a 10GB ext4 partition mounted as root
a 4 GB swap partition
the remainder as an ext4 partition mounted as /home

Dead simple using gparted and you can shrink the home partition at any time if you need to make an extra partition for any reason.

---

### Post by dennisofnewport on 2009-11-19
Thank you for your help.I really wanted the ability to have a reinstall without losing my /home.  I will read the suggestion before I proceed.

---

### Post by florus on 2009-11-19
Shrinking your /home partition with gparted is *very* unlikely to affect the data in the partition. When doing a reinstall just make sure that your /home partition is not set to format.

---

### Post by cascade9 on 2009-11-20
> **dennisofnewport said:**
> I just bought a SATA 500GB hard drive and am wondering how I should partition it before I install Ubuntu 9.10? I am not sure if I will ever share it will another OS. Does splitting it up into small partitions speed it up in any way?

Thanks

Yes, and no. It wont make the drive itself any faster, but dont forget that the 1st sector is the fastest, and the last sector is the slowest. So you you arrange things so that the partition that needs the most speed is the 1st partition, you might/should/will notice a difference compared to if it was the last partition. 

I wouldnt advise chopping up your hdd into lots of smal partitions though. Its just a PITA.

---

### Post by raymondh on 2009-11-20
Try Karmic in live session first (live CD > try ubuntu withou any changes).  See if it works well with your hardware and check if all keys work as well as wifi, ethernet, cd-drive, usb, etc., etc.

When happy and Ok, install.  My reco is

15GB for root
2GB for swap
The rest for /home

I don't think it'll matter (speed-wise).  

Have fun.

---

### Post by dennisofnewport on 2009-11-20
OK I have read all of the suggestions and believe I would like to also use mythtv with this hard drive. Should I consider setting aside a partition for movies?

After reading the posts, and beginning the installation, I am not sure just how I assign each partition a name, do I type /root, /home. /swap ???? or does Ubuntu do that?  I have the Book “The official UBUNTU BOOK” and even they are not clear on what I need to do after clicking “NEW PARTITION”  sorry to take up so much of you time but there does seam to be a step missing in the instructions.

---

### Post by raymondh on 2009-11-21
> **dennisofnewport said:**
> OK I have read all of the suggestions and believe I would like to also use mythtv with this hard drive. Should I consider setting aside a partition for movies?

After reading the posts, and beginning the installation, I am not sure just how I assign each partition a name, do I type /root, /home. /swap ???? or does Ubuntu do that?  I have the Book “The official UBUNTU BOOK” and even they are not clear on what I need to do after clicking “NEW PARTITION”  sorry to take up so much of you time but there does seam to be a step missing in the instructions.

*  I am going to suggest installing Ubuntu as a logical partition inside an EXTENDED partition.  That will give you the chance to create 3  more primary partitions later for say, windows (which require a primary) or a storage partition.

**  Sizing is for example.  Your choice actually

CREATE PARTITIONS BEFOREHAND (before installing)

-  Boot into the liveCD and in live session (try ubuntu without changes) access gparted (system > admin > partition editor)
-  make sure the appropriate HD is identified (upper right box)
-  We are now going to make an extended partition of about 100GB.  Click on the empty space to highlight > select NEW > select EXTENDED > Review and APPLY
-  We will now make 3 logical partitions to contain /, /home and swap.  Clk. on the newly-created Extended partition > select NEW > LOGICAL > 2gb > format linux swap file > Review and apply.
-  Ckl on the extended and > NEW > LOGICAL > 25GB > format ext3 or ext4 > review and Apply (this will be for root or known as / )
-  Clk on the extended > NEW > LOGICAL > Use all remaining space > format ext 3 or ext4 > review and apply (this will be for /home)
-  Exit gparted and begin the install.

MANUAL INSTALL

-  Again, make sure the proper HD is identified at all times
-  In step 4, select MANUAL
-  clk to Select the 2GB > EDIT > USE AS > LINUX SWAP
-  Clk to select the 25GB > EDIT > USE AS select mountpoint / > format ext3 or ext4.  You can also label this as ROOT for ID purposes.
-  Clk to select the remaining logical (about 70GB) > EDIT > USE as mountpoint /home > format ext3 or ext4.  label as /home.
-  Continue with the install.  
-  Step 7 is important if you are using 2HD's.  You need to know which HD is set to boot first in BIOS as you are going to install GRUB to its' MBR..  Let's assume it's HD no. 1.  In step 7, choose advanced and select hd1 as the GRUB destination.  If you are just using 1 HD, there's no need to do this.


Some notes:

You will have remaining about 380-400GB.  This could be your storage partition for your movies or whatever.  You have to decide whether you see yourself installing windows and wanting windows to access this partition as well.  If so, you have to format it as NTFS which can be read by Ubuntu.  You'll also have to get space from here to install windows or whatever OS you wish.

At all times during the install, you can quit until you agree to step 7.  

Post back if you need clarifications.  Happy ubuntu-ing.

---

### Post by dennisofnewport on 2009-11-21
Thank you Thank you espicially raymondhenson

I can now install UBUNTU and get ride of windows for good, thanks to the help of the forum. I am not sure how helpful I can be in the future but I too will do what I can.

---

