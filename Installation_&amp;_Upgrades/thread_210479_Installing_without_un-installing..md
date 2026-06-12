---
title: "Installing without un-installing."
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by grahamroese on 2006-07-06
I will preface this by saying that I have been using Linux for quite a while, so we can assume I know some basic things.

So, let's just say I have Windows installed on my laptop, and I'm looking to create a dual-boot system. Now, is there any way that I can break apart my existing hard drive with the Windows already on it (currently occupying around 20 of the 80 GB space) so that I can install Ubuntu without uninstalling Windows? This would be good, if  indeed possible.

---

### Post by atoponce on 2006-07-06
Yeah.  There are a few things that you will need to do, however.

First, defrag your Windows.  Then do it again.  Then again.  And probably one more time.  I am serious.  Defrag the sucker 3 or 4 times to move all the data to the front of the drive.

Next, use GParted or Partiton Magic to partition your drive into two sections of your desired sizes.

Finally, install Ubuntu Dapper.  It will recognize your Windows intsallation, and write it to your bootloader giving you the ability to dual boot.

Enjoy!

---

### Post by orb9220 on 2006-07-06
I just did that with my desktop.

 1) Do a Scan disk and DeFrag on it first. 
If the disks is too fragmented Gpart will have problems
with the partitioning.

 2) In Windows in computer mangement>Disk mangement 
You need to resize the partion. 

And leave windows at 25 G for breathing room or more 
if you intend to install more win apps and such.

The Rest of the partition will become unallocated. 
You do not need to create a partition or format it because 
Gpart during the install of Ubuntu will take care of that for you.

3) Be sure to select custom manual when it prompts where to install.
4) Be very sure which partion you are working with.
5) Select the unallocated partion unless Gpart does it for you?
6) Create a /  partion that is the size of the disk minus 
the swap partion  Which will be twice the memory u have in yer system.

Example: 50 gig unallocated partion in a system with 512mb of ram we would 
set aside 1 gig for swap partion.

So create /  ext3 partion of 49G and then create a swap-linux partion 1gig
in size then when you click on next you shoud see the 49g 
with a /  for the mount point and a 1 gig with a linux-swap mount point.

Beware! that the right settings before proceeding, Check and be sure before hitting next.
Really no biggie unless u have the 25 g XP partion select by mistake.

That about it it will install and config the grub loader so you can dual boot.

Have fun I am cuz Ubuntu Dapper does rock!

"I am no longer a slave of the XP Dark Side :evil: !

---

