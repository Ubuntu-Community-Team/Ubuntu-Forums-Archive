---
title: "What the heck is LVM and do I need it for RAID?"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by pebkac on 2007-02-17
Hi everyone

I am trying to do a server install of Ubuntu-edgy.

I was unsuccessful at downloading a ISO of ubuntu-server, which I really wanted, and the Ubuntu-alternate, which I believed to have the RAID configuration stuff on.

What I was able to finally get, was a DVD-ISO for ubuntu. 6.10.  Now, I'm going to need some help getting ubuntu up and running! I have some Linux install experience, but only with Mandrake and not on a server set up this way. 

I have an IBM System X 3400. It has 2 36 GB drives & a ServeRAID controller that I have set up with RAID1 using the IBM ServerGuide, before I put in the Operating System CD. Now, I will confess straight out that I have never setup RAID before and have no idea what I am doing.

I have the Ubuntu DVD in there. I am at the screen that says
1. Erase entire disk - SCSI1 (0,0,0) (sda) - 36.3 GB ServeRA Drive1
2. Erase entire disk and use LVM - SCSI1 (0,0,0) (sda) - 36.3 GB Se
3. Manually edit partition tables

Which option do I want? (And what the heck is LVM?) I don't know if I have already set up RAID - does the OS software now think I have just the one drive, or do I still need to set up RAID for the OS?!?!

TIA.

---

### Post by FryerFox on 2007-02-17
LVM is logical volume management:

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

It allows you to add additional drives to current partitions, i.e. increase partition size on the fly without using JBOD RAID, and breaking it every time you want to add a drive. 

If you have 2-36GB drives, then go into Manually Edit Paritions and see if the other one appears. If not, then RAID1 seems to be working.

---

### Post by pebkac on 2007-02-17
> **FryerFox said:**
> LVM is logical volume management:

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

It allows you to add additional drives to current partitions, i.e. increase partition size on the fly without using JBOD RAID, and breaking it every time you want to add a drive. 

If you have 2-36GB drives, then go into Manually Edit Paritions and see if the other one appears. If not, then RAID1 seems to be working.


Thanks for the reply! I have read up and this is definitely what I want, as I can't tell what size the partitions are on my current server so I have to guess the sizes I will need.

The good news: RAID1 *is working*, as I only seem to see one drive.

The bad news: I can't seem to configure any partitions inside my LVM. I hit "Erase Entire Disk and Use LVM" and it makes one /boot partition (255 MB), one swap partition (3.1 GB), and one LVM partition (32.9 GB). I would like to have a /home, /usr,  /var, and /tmp partition but I can't seem to get that working. If I go to "manual configure partitions" I have to erase the LVM partition to add my own, and then the drives won't format (gives errors and such).

In the Ubuntu documentation, it cleary states that "AFTER you choose guided partitioning (either classic or LVM) you will be able to choose from the schemes listed in the table below" But i do NOT get to choose any partitioning scheme, it just does it on its own without asking. How can I get LVM working with multiple smaller partitions?

Sorry for all the questions, and thanks for the help.

---

### Post by FryerFox on 2007-02-17
As far as I remember, last time I set up an LVM system, I had to use the special install CD, not the LiveCD. But after that, I was able to create an LVM system (I don't remeber the exact nomencalture), on each physical volume and then tie them in together into one big-fat volume. At that point, I was able to create as many partitions as I wanted.

If you are starting on a new system, I suggest poking around and trying all sorts of things out, as I did, until you hit on the right combination.

Anyone else know anything about LVM?

---

### Post by grakhul on 2007-02-27
i finally got this working.  Its a bit weird but once you understand the thought process....

so here is what I have: 3 36GB scsi discs(this will not matter as the raid type nor the number of disc should matter)


Configure your raid in BIOS or BIOS Controller or etc...(Just dont use the UBuntu CD - put the cd somewhere far far away)  Get your RAID working in bios


Once you have it working - then put the cd in and go through the install.  When you get to the partition part - stop and take deep breath.

you have to create a /boot partition first
then create a swap partition
Decide how big the TOTAL space that your linux will fit into(/ /var /etc /tmp /etc...)
go into the create a partition once more(you know, the one that you used to create /boot and your swap)
Choose create LVM something or other(it will be the only one with LVM(i am not at the install so I cant remember))
Once you have created the LVM you will be dumped to the same old screen that has your /boot and your swap and some new funky stuff.
Above the "manually edit partition table and that other option you should see a new option.
Pick that one(it will have to do with LVM)
In here you will have to create a volume and something else.  Just use the max size for both.
Once you do that you will be dumped right back where it says /boot swap lvm such and such.  You know the main screen that shows you your partitions.
Select the lvm thingy underneath the lvm thingy.   You will create the remainder of your partitions here.  continue the install reboot and wonder in the goodness.

---

### Post by kerry_s on 2007-02-27
Here's the link to the net installer-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
with this 1 disk you can install any of the ubuntu's available from server to any desktop system.

---

