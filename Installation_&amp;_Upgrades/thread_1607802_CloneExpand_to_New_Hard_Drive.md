---
title: "Clone/Expand to New Hard Drive"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by amj on 2010-10-28
Greetings, 

I've been looking through the Ubuntu, Clonezilla and PartedMagic forums and docs, but I haven't quite found the answer.  If it's out there and I've missed it, please help me with a pointer to the appropriate post(s).

I'm looking to move my 10.04 installation from an 80 GB HD to a 250 GB HD.  

Last week, I successfully moved a Windows system from an 80 GB HD to a 320 GB HD using Clonezilla.  However, I must have missed a command option, as I wound up with only 80 GB used on the new drive, and the remaining space unused.  I used PartedMagic to resize the partition to use the full space, and all is now well. 

Back to my Ubuntu move, on the second machine, I currently have three partitions - /, /swap, and /home.  I'd like to expand / just a small amount, leave /swap sized as it is, and give most of the drive space to /home (as that is where I am running out of space).  I think I have two options:

Option 1: Use Clonezilla to clone the drive (3 partitions), and then use PartedMagic to move/resize the partitions as desired.

Option 2: Use PartedMagic to set up 3 partitions to the sizes I want, then use Clonezilla to copy to the new partitions.

Option 1 seems to be the easier way.  But, is there another option, a better way?  Perhaps there's a command option in CloneZilla that I'm just not seeing, which would allow me to do the move in one step?

Many Thanks, 
AJ

---

### Post by amj on 2010-10-28
I just had another look on the Clonezilla instructions here:
[http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone](http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone)
and I now see what I missed:
	

[INDENT]"If you choose "Expert" mode, you will have some chances to choose advanced parameters, e.g. tune the CHS values of target disk, how to create partition table on the target disk, etc.. You can see more details here.

///NOTE/// By deafult, Clonezilla will clone the "same" size of source disk to target disk. i.e. in this example, only 8 GB will be cloned to target disk, so 4 GB of disk size on the target disk will be unallocated. If you want to make use all of the target disk size, remember to enter "Expert" mode and choose option "-k1"."[/INDENT]

Looks like I need to read up on Expert mode. 

Still, if anyone has any other tips, they'd be appreciated. 

Cheers, 
AJ

---

### Post by linux-hack on 2010-10-28
Well you could try remastersys to make a live CD/DVD of your install and install it where ever you want with the same things.

---

### Post by amj on 2010-10-29
Hi L-H, 

Thank you for the reply.  I'm not sure how I would use remastersys to copy my system to a DVD, unless remastersys can span across DVDs?  I'm using 40+ GB on my /home partition. Or does remastersys only cover the system installation, and the user space would be done by simple file transfer?

Cheers, 
AJ

---

### Post by darkhelmetchris on 2010-10-29
> **amj said:**
> Back to my Ubuntu move, on the second machine, I currently have three partitions - /, /swap, and /home.  I'd like to expand / just a small amount, leave /swap sized as it is, and give most of the drive space to /home (as that is where I am running out of space).

Here is what I would try.  Use your PartedMagic LiveCD and GParted for it all.
1.  Create a new partition table on the destination (250GB) drive
2.  Copy your "/" partition from the source and paste to the destination drive.
3.  Set the new "/" partition to bootable on the destination drive.
4.  Resize the new "/" partition as you like.
5.  Create a new swap partition on the destination drive as you like.
6.  Copy your "/home" partition to the destination drive.
7.  Resize your "/home" partition as you like.

The only gotcha here is the UUID, as your fstab probably identifies your partitions by UUID.  You can either set them when you're done or you can edit your original fstab to identify your partitions by device path (like /dev/sda1 instead of UUID) but.. perhaps GParted handles this already?  If it does not, then, clone the drive and use GParted to move things around.

---

### Post by linux-hack on 2010-10-29
> **darkhelmetchris said:**
> Here is what I would try.  Use your PartedMagic LiveCD and GParted for it all.
1.  Create a new partition table on the destination (250GB) drive
2.  Copy your "/" partition from the source and paste to the destination drive.
3.  Set the new "/" partition to bootable on the destination drive.
4.  Resize the new "/" partition as you like.
5.  Create a new swap partition on the destination drive as you like.
6.  Copy your "/home" partition to the destination drive.
7.  Resize your "/home" partition as you like.

The only gotcha here is the UUID, as your fstab probably identifies your partitions by UUID.  You can either set them when you're done or you can edit your original fstab to identify your partitions by device path (like /dev/sda1 instead of UUID) but.. perhaps GParted handles this already?  If it does not, then, clone the drive and use GParted to move things around.

This is a good way of doing it yes. And for remastersys, it makes a live installation from your existing system, and after you just transfer the files to the new install.

---

### Post by amj on 2010-10-29
Thank you for your further replies.   

I had another look at my current drive, and I had misread the info.  I have more available space in / than I originally thought, so I don't need to expand it at all.  Therefore, it looks like my easiest option is to use Clonezilla to copy the drive, followed by GParted to extend /home to the end of the drive. 

Cheers, 
AJ

---

### Post by amj on 2010-10-29
I'm pleased to report that the cloning went smoothly.
 - Clonezilla to copy the drive
 - Gparted to resize /home to use the extended space

Thanks again for your support. 

Cheers, 
AJ

PS - Installed 10.10 over 10.04, and that went smoothly as well.

---

