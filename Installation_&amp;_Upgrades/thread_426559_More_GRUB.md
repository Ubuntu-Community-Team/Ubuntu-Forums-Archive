---
title: "More GRUB"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by powpow on 2007-04-28
I was getting a GRUB 17 error, without being able to edit/exit grub.  The deails are all [here]("http://ubuntuforums.org/showthread.php?t=416969").

Anyway, now I have a CD ROM and can view/edit menu.lst and boot.ini, etc by using a live CD.  However, I don't know what to do.  I've changed menu.lst so that it doesn't reference any volumes (at all...).  I've also made sure there's only one partition on the drive with a "boot" folder.

Still getting the error when I try to boot from Hard Drive (there's a Windows installation there somewhere, as well as an old Ubuntu).  It says "searching for Boot Record from IDE-0...OK
Then goes straight to GRUB Loading stage 1.5

GRUB Loading, please wait...

Error 17, and dies.

Any ideas?  What info do you need?

Thank you!

---

### Post by bulldog on 2007-04-28
Hi again :) 
Can you boot the live cd and perforn the command```
sudo fdisk -l
``` it's a lowercase L not a one,and post the output to the forum please?
With this output we can see how the partitions are setup on the hdd.

---

### Post by powpow on 2007-04-28
Hello bulldog.  Thank you once again for checking in here!

Output:

[FONT="Courier New"]Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1775    14257656    c  W95 FAT32 (LBA)
/dev/hda2            1776        1778       24097+   e  W95 FAT16 (LBA)
/dev/hda3            1779        1858      642600    c  W95 FAT32 (LBA)
/dev/hda4            1859        2432     4610655    f  W95 Ext'd (LBA)
/dev/hda5            1859        1960      819283+   7  HPFS/NTFS

/dev/hda6            1961        2432     3791308+   7  HPFS/NTFS



Disk /dev/sda: 515 MB, 515899392 bytes

16 heads, 32 sectors/track, 1968 cylinders

Units = cylinders of 512 * 512 = 262144 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1968      503792    e  W95 FAT16 (LBA)[/FONT]

Hope this helps, let me know if you want to see anything else.

---

### Post by powpow on 2007-04-28
Hmmm.  Seems like I have 2 partitions called "c"?  Don't know if it matters or not....

FYI:  the computer came with 3 partitions.   

#1:   (I believe) is Windows 2k

#2:  There's a RECOVERY drive (E) with stuff like WINDOWS.BAT, RECOVER.BAT and a TOOLS folder.

#3:  There's also a DATABAK drive (D) with nothing in it...

Note that I wrote these descriptions long ago, before the thing broke.  If I'm understanding correctly, one of the drive names/IDs has changed perhaps.

---

### Post by bulldog on 2007-04-28
Hmmm,where is your ubuntu supposed to be?
Can't see a Linux install anywhere :confused:

EDIT;
this is how my hdd's are partitioned```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1568       20362   150970837+  83  Linux
/dev/sda2             132        1567    11534670   83  Linux
/dev/sda3               1         131     1052226   82  Linux swap / Solaris
/dev/sda4   *       20363       24321    31800667+  83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3649    29310561    7  HPFS/NTFS
/dev/hda2            3650       14593    87907680    f  W95 Ext'd (LBA)
/dev/hda5            3650        7261    29013358+   7  HPFS/NTFS
/dev/hda6            7262       14593    58894258+   7  HPFS/NTFS

```

---

### Post by powpow on 2007-04-28
This doesn't sound good...

Truth be told I used Puppy linux to run the command (tried again and the 'sudo' thing didn't make sense to Puppy).

So, I've got a Ubuntu live CD in there but it takes a while to boot up (to say the least).  Not sure if it would give a different output....

I guess the most important thing would be to keep Windows (because it's an embedded version and it runs pretty well) but have the ability to fool around with other stuff -- and be able to boot Windows.

I'll let you know if I can find anything else.

---

### Post by bulldog on 2007-04-28
If you download the gparted live cd,which is only a 55MB download,and burn it to a disk.
Boot from this disk and you'll have a nice graphical partitioner like Partition Magic.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can see your partitions much clearer whith this tool.

If you can create a 5-10GB free space,you can install ubuntu for a try out.
Use 1GB to create a swap partition and make the rest ext3 file system for the /  [root]

---

### Post by powpow on 2007-04-28
Interesting.  I used gparted to reformat the last 2 partitions (hda4 and hda5) to ext3.   Just wanted to do things one step at a time (funny how caution doesn't enter until after the problems start).

I didn't intuitively see how to resize anything but the 1st 3 partitions, and I don't want to mess with those anymore -- yet. 

After doing that, I reboot and get Grub error 15.

Call me an optimist but that's progress in my book...

---

### Post by bulldog on 2007-04-28
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

If you have two partitions for ubuntu [at least 10GB for a decent try out] delete them both with gparted so you get unused space available.
Create a 1GB swap partition [similar as the windows page file] and format it as swap.
Create a partition from the rest of the space and format it ext3.
If you're satisfied,apply the settings and if done,exit the gparted live cd.

Boot the ubuntu install cd and hit the install button.
Follow the steps till you get to the partition part,choose manual partition,and mount swap as swap and set it to format as swap :) 
Mount the ext3 partition as  /  [root] and set it to format ext3,set the bootflag to yes,look carefully if your windows partitions aren't set to format,and apply your settings.

The rest of the install should be smooth.

EDIT;
Off to get some sleep for now,be back tomorrow to see if all is well.
If you still have problems or questions,just send me a PM with a link to this topic.

---

### Post by powpow on 2007-04-29
Well, something happened.  I've got Windows running again which gets me back to where I started.  That's a good thing...

I tried installing xubuntu on the partitions we talked about, no luck.  Then I threw Puppy in and tried to install to the partitions.  This worked, and I got to (re)install GRUB....  I never even booted Puppy....

Once I got the option to get into the recovery partition on the hard drive I went there and it restored everything to a disk image that came with the computer.  Now I can start over a little bit wiser.

I think I'll stick with Puppy as it seems to run faster and be easier for me.  I may take another crack at Xubuntu just because I imagine it has more built-in, but we'll see.

Anyway, thanks bulldog for your help.  You helped me understand what was missing/wrong, and that got me back here where I needed to be.  Thanks again, you rock :guitar:

---

