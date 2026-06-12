---
title: "Fresh start upgrade dual-boot Ubuntu Studio 13.10"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by skyemoor on 2014-01-10
Dell Inspiron 
Ubuntu Studio 13.04
Gnome 3.6.3
Kernel 3.8.0-33-lowlatency
i7-2720QM CPU @ 2.20GHz
4G RAM

I have been successfully running dual boot with Win7 for many months, until I tried to setup a Dell network printer that turned out to be a Samsung rebrand. I tried many, many, many suggestions, one of which was to change ownership and group of everything in /usr/lib to root.

I could no longer access the internet and a number of other capabilities. I cannot install components from Software Center, for example. I'd like to overwrite/load 13.10 and get a fresh start (not just an upgrade).

The dual boot instructions and my partition arrangement have me wondering two things;

1. Do I skip the install of grub? If so, will the 13.10 version be 'found' by the previous Grub installation?

2. My partitions look a tad confusing (see below). The first three are obviously Win7 based. The 4th (/dev/sda4) looks split into 2 other partitions, /dev/sda5 and /dev/sda6 (linux-swap).
**Do I install into /dev/sda5?**

I'm following this install method, and my case is a bit out of the norm, so I'd like to confirm before moving forward;
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

[IMG]http://i881.photobucket.com/albums/ac17/skyemoor/Screenshot-Gparted_zpsf9c4c963.png[/IMG]

---

### Post by egeezer on 2014-01-10
If you want a fresh install of 13.10, you'll need to download the .iso file and make a bootable DVD/USB.

You can use the GUI installation method for it, but when it comes to the Partitioning part, choose the "Something Else" option (custom partitioning).

In that, you will be able to delete the whole extended partition; then choose New to set up your 135GiB / (root) partition with file system ext4 and again New for the 4GiB swap partition.  After that, if you like what the setup looks like, you can let the system choose the default location for the grub.

I recommend you run through the LiveDVD/USB installation program at least once before you commit, so you can be sure what you're doing.  You can always go back to earlier steps or quit at any time before you do the Write Changes To Disk.

Good luck! :-)

---

### Post by fantab on 2014-01-10
> **skyemoor said:**
> 
The dual boot instructions and my partition arrangement have me wondering two things;

1. Do I skip the install of grub? If so, will the 13.10 version be 'found' by the previous Grub installation?

2. My partitions look a tad confusing (see below). The first three are obviously Win7 based. The 4th (/dev/sda4) looks split into 2 other partitions, /dev/sda5 and /dev/sda6 (linux-swap).
**Do I install into /dev/sda5?**



No. Your partitions look normal. There is no confusion. 'MBR' partitioned disks have a ONLY 4 Primary Partitions LIMIT. To overcome this limit you have an EXTENDED Partition, which is a Primary Partition and also a 'container' for further LOGICAL Partitions.
So:
/dev/sda4 is an Extended Partition/container
/dev/sda5 and /dev/sda6 are the Logical partitions 'contained' within the /dev/sda4 or the Extended Partition.

NO. You don't skip installing Grub. You can't as Ubuntu won't allow you that option. You have to re-install everything on that Ubuntu DVD/USB.

Yes, you have to re-install Ubuntu to /dev/sda5. However, you have choose '**Something Else**' option (during Ubuntu re-installation) from the '*Installation Type*' dialog.
Then select the partition you want to install Ubuntu to, ie, /dev/sda5 and hit the '**Change**' button.
Set up that partiiton as:
**Format** = yes, check the box
Mountpoint =** /**
Use as = **Ext4**

Make sure Grub is installed to the **/dev/sda**, the HDD and NOT /dev/sda5, the partition.

Apply the changes and continue the installation.

Good Luck.

---

### Post by skyemoor on 2014-01-12
Thank you fantab (and egeezer), this approach proved fruitful! I am now back up and successfully running in dual boot. 

Your information reduced the risk of a misstep immeasurably.

---

