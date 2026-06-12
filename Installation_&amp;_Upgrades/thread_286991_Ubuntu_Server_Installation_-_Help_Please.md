---
title: "Ubuntu Server Installation - Help Please"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Beamerboy on 2006-10-28
Hello,

New territory for me here.  I currently run Dapper on my desktop machine, but I just rebuilt my dual Athlon system and I am in the process of installing Edgy Server Edition on it.

I am upto the partition manager and am not sure how to continue.  I have 2 drives (both 120GB each) hda1 and hda2, currently there are no partitions on either drive and I don't have a RAID card in this box so I decided to try LVM since I hear so many people praising it.

However, I have never setup ubuntu server before neither have I ever setup LVM and the documentation doesn't provide a walkthrough for the installation or any information on LVM.

So where do i go from here?  I want both drives to be in the LV Group I also would like 4GB SWAP (I have 2GB RAM in the box and old habits die hard, back when I started using linux many years ago it was recommended to use 2x RAM for swap).

So what do I need to do and what would people recommend for the partition structure?  The server is for httpd (including mysql and php)/postfix/dovecot/ircd and bind.

The first time I installed I must have done something wrong becuase it only added the first drive to the LV Group, so I need to know how to get both drives added to the LV Group as well.

Thanks

Beamerboy

---

### Post by jpdw on 2006-10-28
Timely question... I'm doing something very similar at the moment... Installing Edgy server & using LVM (but I'm adding RAID-1 to some of the storage which makes life more challenging!!!).

I, personally, have never tried installing with the /(root) partition (it was near impossible to achieve when I first used LVM for some years ago).  I always set up the machine so that I have a traditional /(root) partition and then put /home /usr & /var inside LVM.  It's a little more work but then I am guarenteed to be able to boot even if I've rebuilt the kernel & forgotten to include the LVM feature !!

/dev/hda1 /       2GB
/dev/vg00/usr    10GB  <---- LVM in volume group vg00
/dev/vg00/var     1GB  <---- LVM in volume group vg00
/dev/vg00/home   10GB  <---- LVM in volume group vg00

Here's how I have just done it...

Boot the install disk... 
Follow prompts through the install process to the partitioning tool.  
Select to manually partition

In the partitioning tool, you should see both of your hard disks.  

Work with your FIRST / Booting drive (ie the /dev/hda drive)
Create a real /(root) partition and select the filesystem time you prefer.  Make sure to mark this as Bootable and to set the mount point to / .

Now use the same process to create a swap partition -- set it to 4Gb as you want.  In the details page for the partition you need to select filesystem type "swap" and ignore the mountpoint.

Then select the FREE SPACE on the same drive and add another partition.  This time, for the filesystem type, select "Physical volume for LVM" (or something similar).

Next select your 2nd drive, create a partition table by selecting it.  Then select the Free space and create a maximum size partition.  Again, select the filesystem type as LVM physical volume (PV in LVM terminology).

Back on the main partitioner screen, scroll to the top and select "Configure Logical Volume manager".

Select to create a Volume Group (VG).
It will give you a list of all known PVs -- there should be the two that you have just created.  Select them both and confirm.

Back on the LVM manager screen, select Create Logical Volumes.  This is a bit like creating a new partition, as this is where you create LVM 'partitions'.  Enter the size you want and a name for the LV (usr for your /usr for instance!).  Note that you do not select filesystem or mount mount here.

Repeat this to create any other LV's you want (ie 'home' and 'var' in my suggestion above).

Then select Finish or Done (whichever!) in the LVM to return to the main partitioner screen.

Now you should see that the list includes your LVs as is they were partitions.  Select each in turn and select a mount point (ie /usr /var /home) and a filesystem.

You dont have to create LVs to use up all the space in the VG - so although you probably now have about 200 Gb in the Volume Group (across 2 Physcial VOlumes) you can leave a lot of it empty - the beauty of LVM is that you can extend your LVs into this space in the future, with minimum hassle.

Back to your installation.... 

Now you have your partitions & LVM setup, and the PVs are allocated their mount points you can finish the partitioner (Write changes I thnk the option is) and the installation will continue as normal.  The system will format the LVs and mount them in /usr /var /home etc and after that they will install in the same was as real partitions.

I hope that helps... If you need more info just reply or PM me.

---

### Post by Beamerboy on 2006-10-28
Thankyou very much, I was able to follow those instructions without any problems at all and now everything is setup :)

Much appreciated

Beamerboy

---

