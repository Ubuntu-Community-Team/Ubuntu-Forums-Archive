---
title: "need help w/ grub and multiple instances of Ubuntu"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Triple Crown on 2007-11-19
I was running Ubuntu 7.10 and my single hard drive started to act like it was about to crash. So, I installed a second hard drive. I asked in the Yelp forum whether it would be better to try to move my current install to the new drive or reinstall Ubuntu on the new drive and then move my data from the old to the new drive. The advice was to reinstall and move date. So, I installed a second instance of Ubuntu from a 7.04 boot CD. I anticipated that the boot loader (which I understand is called GRUB) would automatically add another choice to the start up menu and allow me to boot from either my old or new instance of Ubuntu. Wrong. Selecting "Start Ubuntu from first hard disk" only booted the new instance, leaving my data on the original instance unaccessible. At the same time, I bit the bullet and bought Windows XP on which to runs some Windows only apps I have running on an older PC running Windows 2000 Professional. I attempted to install XP onto an empty partition on the 2nd drive, but it complained that the drive already had the max number of partitions, so I deleted one of the two linux-swap partitions on drive 2. I haven't had time to attempt to reinstall XP again. I've tried so many things, that I'm not sure if deleting this swap partition was the problem, but now I can't boot from the new instance of Ubuntu, either. I am able to load a temporary instance of Ubuntu into RAM from the CD, but do not know how to fix the problem(s) preventing access to my original instance of Ubuntu. When I choose the boot from 1st hard disk option now, I get the follow error text only error message: "booting from local disk. Error loading operating system". What I read about Grub implies that it is a powerful boot loader, but it also seems complicated. Isn't there a way for Grub to scan all drives and find operating systems and automatically create a menu of choices? 

Assistance would be much appreciated. I'll soon be having cancer surgery and I need to get my PC stable for the family before I'll be out of action for a while.

Here is info on my system:

Primary Master disk= 30GB original drive
Primary Slave= 160GB new drive
Seconday Master= CD drive

boot order= floppy, CD, Primary Master

Gnome Partition Manager reports:

dev/hda
hda1; 14GB ext3
hda2; 14GB ext3 (boot)
hda3: 730MB linux-swap

/dev/hdb
hbd1; 8GB ext3 (boot)
hdb2; 50GB ext3
hdb3; linux-swap (deleted- 90GB total unallocated)
hdb4; 730 MB extended
hdb5; 730 linux-swap

---

### Post by monktbd on 2007-11-19
first about windows:
the eaiest is always to install windows first and then linux. windows also needs a primary partition to boot from (i think) so i guess that is the error you got. 
another option would be to install windows in a virtual environment once you have your linux up and running given that you have quite a bit of RAM (1GB+) and power in your comp. 

you also would need only one swap for all linux distribution you have although swaps usually do not take much place anyway. you just need to point each distribution to the one swap partition.

recipe now for installing: 
if there is no important data on the new disk, delete all partitions there, make a primary partition (choose the size for your liking) for windows and install it there (if you want a seperate windows install and not in a virtual box). 
then install ubuntu in an extended partition (and make as many more partitions as you would seem useful, i would always recommend an extra partition for /home). 
then boot into your new linux and manually mount the first harddrive to copy your data over. 
so basically get your setup working and then ask how to mount the first harddrive if it wont work from the partition manager.

---

### Post by meierfra on 2007-11-19
Check out this link:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")


At least  it should allow  you to boot back into your old Ubuntu  (As long as your old hard drive is still alive) . Make sure your bios are set to boot from the old hard drive,


To get into your new ubuntu, I suggest to install grub also onto  the MBR of the newer hard drive via


sudo grub
root (hd1,0)
setup (hd1)
quit

(Do  this from in a terminal of the  LiveCD  or  your old ubuntu)

Booting from the new hard drive should now get you to the grub-menu of the new ubuntu. (You might have to press "Esc" during the count down).  But you might fail to boot into the new ubuntu since the file "/boot/grub/menu.lst" needs editing. Come back here if that happens.


If none of this worked get Super Grub:  [Hermanzone Info on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

