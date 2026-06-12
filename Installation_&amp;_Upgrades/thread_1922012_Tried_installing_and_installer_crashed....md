---
title: "Tried installing and installer crashed..."
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by kylec123 on 2012-02-07
I've tried installing ubuntu through wubi a few times and i never got it to work(would always boot to grub prompt and never actually boot the OS).  I tried to install the OS from a USB stick and while doing so i got an installer crash and left me with two new partitions i can see in my windows disk management window.  This may be more of a windows question....but how can i get these two partitions the installer made back to my C drive. They are both listed as  "healthy" and are called "primary dives".   Really hoping this didn't leave me with no way of getting these back.  I never thought trying to install ubuntu alongside windows would be this trivial.    Probably about to give up. :confused:

---

### Post by Quackers on 2012-02-07
Is your system booting directly into Windows? Not through a grub menu?
If so, you can delete the new partitions in Windows disk management screen.
Take care to delete the correct partitions though!

---

### Post by kylec123 on 2012-02-07
If i "delete" these two partitions..does that make the space unusable or does it then become unallocated space?  I haven't messed with partitioning much so i don't want to mess anything up.  

A third party partitioning software i downloaded says these two partitions are logical.

---

### Post by kylec123 on 2012-02-07
Also...yes directly to windows.  Once wubi failed me for the 4-5th? time i uninstalled it and it was back to windows with no grub prompt.  The installation using the USB method did not get far enough to where it actually installed it enough to get the grub.  I guess.  

Should i try again and not choose to install updates while installing the OS?  It seemed to crash right after it finished downloading packages during the install process.

---

### Post by Quackers on 2012-02-07
I would boot from the Ubuntu cd/usb and select "try Ubuntu".
When loaded I would suggest that you open gparted.
In gparted right-click on the swap partition and select "swapoff".
You can then delete the necessary partition(s) (including the swap partition). Make sure you don't delete a NTFS partition! That's a Windows partition.
If they are logical partitions you can also delete the partition that contains them - which would be labelled as an extended partition.

You can then try to re-install Ubuntu (without any updates or drivers) and see how that goes.

---

### Post by kylec123 on 2012-02-07
Alright i got the partitions settled.  Thanks btw.  I tried to install again....ended up trying with downloads again....crashed.  

Here is the error report.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961)

I might just try and get an older version of ubuntu.

---

### Post by kylec123 on 2012-02-08
Alright so i did it again with no updates.  I finished and when i first rebooted it gave 

error hd0 out of disk

grub rescue>


rebooted again and i get

error no such partition

press any key...


then when i press a key it eventually boots ubuntu.  Which seems to be not working properly at all.  And my partition its alot smaller than i specify when i go to the system directory and view size.  I chose 11 gb from the slider during the installation....it made the same like last time..(2.38 gb partition and 7.91 partition).  Now these partitions are created...but completely unused.  

Also....windows only sometimes boots now.  It gives me this sometimes...
error no such partition

press any key...



I guess....now i should just uninstall it.  Which....i dont think i know how to do.

---

