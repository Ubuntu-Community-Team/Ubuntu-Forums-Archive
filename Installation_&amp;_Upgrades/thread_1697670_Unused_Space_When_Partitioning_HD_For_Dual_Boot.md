---
title: "Unused Space When Partitioning HD For Dual Boot"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by aktalap on 2011-03-01
First thing's first.  I am attempting to install the 64-bit version of Ubuntu 10.10 on my computer.  I'm intending to dual boot Win7 and Ubuntu with one hard drive that came factory partitioned into two drives.  Win7 was installed first.

Ok, onto the issue.  The Install is going well until I get to the Allocate Drive Space form (so almost right off the bat).  I first created a swap partition within my "second drive" (really just a partition of the larger drive).  This stalled out and I had to exit setup and restart the computer.  Booted into Win7 to be safe and Win only recognizes the First Drive and no longer the second drive. So, I boot up the Ubuntu Install CD and get back to the allocate drive space form and I see I have a (linux-swap) drive with the same gb space as before.

So, from here I create a partition within the "second drive" 20gb of ext4 type space.  This does not stall out and creates a partition of 20 gb.  But, now it says I have 175 gb of "Unusable" space.  This is very unsettling and using the "revert" button does nothing.

How do I fix this space so I can finish the install?


Note: I'm following this install guide just to be nice and safe. [ http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml ]("http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml")

---

### Post by ajgreeny on 2011-03-01
It is a bit difficult to understand exactly what has happened in your attempts to set up the partitions, so can you boot up to the live CD again, but this time choose to "Try ubuntu" and not "Install ubuntu".

When you get to the full gnome desktop, go to **System->Administration->Gparted** and tell us, or even better attach a screenshot of the window that appears showing the disk and partition setup.  Could you also run the command ```
sudo fdisk -l
```(lower case L at the end) in **Applications->Accessories->Terminal** and copy the output back here, along with the screenshot.

There are slightly better guides to installing ubuntu than that one from softpedia, in my opinion, and I suggest you go to [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) which although it is for installing with a separate /home partition, (very much recommended), does give lots of information about manual partitioning during the install, which for 10.10 is also highly recommended, as 10.10 can easily wipe out your windows partition if you choose to install alongside windows as a result of a bug in ubiquity, the installer software.

---

### Post by aktalap on 2011-03-01
Having some trouble installing GIMP easily to take that screenshot for you (something about access).  However, this is the response from fdisk in terminal:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x190c8c06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            1306        1319      102400   27  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1319       37009   286677920    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           37009       39498    20000000   83  Linux


Sorry, if the OP was confusing.  I re-read it this morning and it definitely sounds convoluted.  However, I am trying to partition one of two "drives" (which are really just partitions of one big hard drive) to be used with Ubuntu exclusively.  I want to be able to partition /dev/sda4 further to install Ubuntu solely on this "drive".  Just FYI, the /dev/sda3 "drive" is running Windows and I would like to keep it that way, leaving /dev/sda4 to be used with Ubunut, and be able to dual boot both OS.

When I began partitioning /sda4, I hit the "Change" button (the add button was not highlighted/unavailable).  However, when I changed the partition to set up 20 gb of space within /sda4 - it created a 20gb partition and then left the 170gb so left as "unusable" space which I could not do anything with (the only option highlighted was the "revert" option and this did nothing to that space.

I would hope that that 170gb of space can be reclaimed and put to good use.

How do I proceed from here?  Should I do all the partitioning with the GParted program?

Thanks for the help ajgreeny!

---

### Post by ajgreeny on 2011-03-01
You don't need GIMP to take a screenshot!

Just press the Print Screen key and it will be done, and probably save the screenshot.png file to Desktop or live CD's home.  Attach that and it will help a lot.

You have the added problem at the moment of 4 partitions, which is the maximum possible, and there is no way to know what the first two actually are, though I suspect one of the first two is a recovery and the other some windows system partition.  I know very little about Win7 so can not help more on that score.

I think you will need to delete the final sda4, make a new extended partition in its place and then make new partitions sda5 as ubuntu root, and sda6 as swap, within that extended sda4.  However, a screenshot would definitely help a lot and show much better what is going on, and I would rather wait for that before telling you further where to go next.

---

### Post by Hakunka-Matata on 2011-03-01
GParted is an excellent way to prepare the drive before installing.  Look at the Thumbnail included and you'll see a typical partition scheme.  You could also let the installer partition the drive for you, but BEWARE, as stated above the 10.10 Desktop installer is dangerous if you do the wrong thing after selecting 'side by side' partitioning.  If you do find yourself in that position, once you've selected 'install operating systems side by side', do NOT select Entire Disc, or Entire Partition, simply continue.  Selecting Entire Disc, or Partition, will wipe out any existing partitions = Data Loss.
It's for that reason that it would be wise to partition your disk ahead of time with GParted, and then install to the correct partition.  The new EXT4 position you've made.

---

### Post by Hakunka-Matata on 2011-03-01
To send a screenshot, use Applications > Accessorries > Take Screenshot.  Save the .png file and upload it using the paperclick icon, attachments.

---

### Post by Hakunka-Matata on 2011-03-01
@ajgreeny, I just noticed you're back, I'll step aside, didn't see your reply before sending mine.

---

### Post by aktalap on 2011-03-01
ajgreeny - here's that screen capture. hope it clarifies the situation.

---

### Post by aktalap on 2011-03-02
Alright, a little update.  So, I have repartitioned my drive, /dev/sda4 includes a swap partition, ext4 root partition, and ext4 (/home) partition.  All seems well.

However, I'm a little concerned that if I choose the root partition within the extended partition, that it will negatively affect the entire hard drive including the Win7 partitions.  That would be unfortunate.

Is it safe to install to the extended partition or will it wipe out my Windows partitions?

---

### Post by Hakunka-Matata on 2011-03-02
> **aktalap said:**
> Alright, a little update.  So, I have repartitioned my drive, /dev/sda4 includes a swap partition, ext4 root partition, and ext4 (/home) partition.  All seems well.

However, I'm a little concerned that if I choose the root partition within the extended partition, that it will negatively affect the entire hard drive including the Win7 partitions.  That would be unfortunate.

Is it safe to install to the extended partition or will it wipe out my Windows partitions?

Please use ```
sudo fdisk -l
``` and take a screenshot of the output.

You'll notice in the attached Thumbnail that each partition has a unique/separate identifier.  Your description of your partitioning scheme doesn't make sense, sorry.

A snapshot of GParted showing /dev/sda would also be good.

You must also have a Swap partition for a Ubuntu install.

---

### Post by ajgreeny on 2011-03-03
Like Hakunka-Matata I am also confused!

Your screenshot shows four partitions and a large unallocated space of 163GB.  sad4 is already a partition but not used at the moment, other than the reserved area of ~480GB, which is normal for ext4.

You will, however, need to delete that partition using gparted, to make a larger unallocated area of 182.26GB, which is your current sda4 plus unallocated area.

Now make a new sda4 as an extended partition using all 182.26GB, and within that extended partition make logical partitions for your Ubuntu needs.  I suggest either
sda5, ext4 of about 10 -15 GB mounted as root (/), 
sda6 of 2 -4 GB swap, 
the rest as sda7, ext4 mounted as /home.

Or within that space you could make a separate /data partition formatted as ntfs, rather than a separate ext4 /home partition, and in this situation probably leave the home folder as part of the root partition.  This will mean that your win& OS will be able to see and work with files you make with ubuntu; that would be almost impossible if you kept all data files from ubuntu in a separate ext4 /home.

There is always the easier way to do this, simply using just two partitions for ubuntu, ie root and swap, but if you want to share files with windows the ntfs data partition is probably the best choice.

---

