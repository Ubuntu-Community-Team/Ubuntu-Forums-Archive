---
title: "Installed Ubuntu after Vista - now its all a mess"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Michael_svm on 2007-08-16
Hi
I have installed Ubuntu with really knowing what I'm doing (which I realize after reading other posts in similar matters). Now my computer is living its own life ie. 
A. When botting from HDD Grub halts before the Grub menu pops up. 
B. When I boot from Vista DVD it fails to read the DVD and halts.
C. When I boot from Ububtu CD - Ubuntu OS appears. Here I can se that one of the HDD:s cant be recognised. This HDD shoukl have two partitions (Win & Linux). Ubuntu OSD is not installed on this partion though.

I have 3 HDD:s: 
1. Vista system disk (one partition) (SATA)
2. Data disk with 2 partitions (Win and Linux) (SATA)
3. Win data disk & Linux OS disk. (SATA)

All the occurances (A-C) is not always what happends eg. sometimes Ubuntu will not start from the DVD.

The boot problems occurred after I tried to install another HDD (IDE). The problems remained after I removed the IDE disk.

I have no idea how to get out of this mess, but now I just want to erase everything and install Vista just to get the computer functional again. I just bought it and I am afraid that I cant get the computer to function.

I feel that the problem may be due to broken motherboard or broken Grub or briken Bios.

Can anyone help me?:confused:

/Michael_svm

---

### Post by yossir on 2007-08-16
this is really a stab in the dark, but maybe the new drive somehow messed with how your bios looks for places to boot from. try going into the bios and make sure that it looks in the optical drive(s) first or at least b/4 the harddrives. thats all i can think of now

---

### Post by dabl on 2007-08-16
Yep, that's a mess all right!  :mrgreen:

I'd say you have too many possible problems to deal with all at once -- why not first confirm that the hardware is NOT broken?  I don't have or use Vista, but if that's the Windows product you want, fdisk your first hard drive and install it and configure it and confirm that all your hardware is functioning as you want.  

A really effective hard drive viewing and partitioning tool is the GParted Live CD, which you can download from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) You can boot your GParted Live CD, and make sure your drives are partitioned as you wish, and that the "bootable" flag is set on the partition where you want to install Vista.

When you are reasonably comfortable that you have working hardware, then use the Vista disk partitioning utility to shrink the largest Vista partition so that you've got a nice amount of space for Ubuntu -- say 20GB total (make sure it is not less than 8GB or you're wasting your time).  Or, if you'd rather leave that first hard drive totally a Vista resource, then during the installation function in your Ubuntu Live CD, choose the second or third hard drive as the one on which to install Ubuntu.  

After freeing up the space for Ubuntu, install it on the empty space, using the installer on your Live CD, and accepting the defaults for configuration.  It will put Grub in the MBR and give you a boot menu, so you can choose to boot Ubuntu or Win Vista when powering up your computer.

A final suggestion, since you have lots of drive space, is to make a separate partition for your Ubuntu /home partition.  This is where your data and configuration settings will live, and they will be safe and secure if you need to reinstall the OS.  So, if you follow this suggestion, you'll need one 8GB partition for the OS, a smaller (0.5GB - 1GB) partition for swap, and the rest of the available space for /home.

That should get you started on a better experience.  :popcorn:

---

### Post by Gremlinzzz on 2007-08-16
If theres nothing to save
take out two drives leave original reset bios back to default then change boot order
blank the drive or not [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
then reinstall vista
then put the other drives in and screw it up all over again.

---

### Post by buntunub on 2007-08-16
Wow! Sounds like deja vu all over again for me, because that is exactly how I ended up getting into Linux. In my case it was Fedora 6 that decided to claim all my hardware and drive space for itself and so I was forced to learn Linux to fix my issue. Glad I am of that now, but in your case, its going to be scary and very frustrating at first, but fear not, you'll quickly find that your much better off in the end. Congratz on ditching Vista, even though it was an error on your part. 

My suggestion to you is to format your drive using Gparted from livecd. Allocate as much space as you need for Vista on SDA1. Allocate as much space as you want for Ubuntu on SDA2 or 3, or wherever you want it. Just make SURE you put Vista on sda1. Then go in and install Vista on sda1. Then install Ubuntu on whatever partition you designated before. After that, you ~may~ have to fix grub to ensure you can still boot into Vista but that is childs play to do, and usually does not happen as Ubuntu is very very good about auto detecting Vista installs and formatting grub for you. OR, just install Ubuntu using the default install options and wave farewell to Vista! Ahh well, in good time.

---

### Post by Michael_svm on 2007-08-17
Thank you all for your suggestions!

I actually managed to get the computer up and running again :-)  I hade listed all possible solutions, with the easiest task on top - setting the bios to deafult configuration. When this had been done I could boot the Ububto installation (but not Vista). 

Having booted Ububtu I could do some investigation and suspected that one of the HDD:s was broken or not properly connected. Hence I checked the connections a second time and voila - the computer got fixed.
:mrgreen:

The combinated bios - HDD error was confusing - I must say. Thanks once again for your help!

---

