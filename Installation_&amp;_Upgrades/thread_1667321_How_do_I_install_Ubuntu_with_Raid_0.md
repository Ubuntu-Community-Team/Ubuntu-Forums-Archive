---
title: "How do I install Ubuntu with Raid 0?"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by Luke oX on 2011-01-14
I have searched many places on how to install Ubuntu with RAID 0, and none have been successful. I then decided I was gonna disable raid so I can just have my to HD so I could finally install Ubuntu. Then I found out if I disable RAID, it will erase all my data, and I don't have a external HD to back up my data so I'm screwed there. Please help... All I want to do is install Ubuntu without a huge hassle...

---

### Post by Lundis500 on 2011-01-14
Well, what's on the harddrive now? And what filesystems?

---

### Post by Luke oX on 2011-01-14
Windows 7 and documents, music, pics.

---

### Post by ronparent on 2011-01-14
Boot the Ubuntu desktop edition 10.10 to the live cd. I think you will find all your raid0 partitions mountable. Except in systems with quirks, 10.10 is now compatible with all raid chip sets supported by dmraid. One bug possibly remains. The partitioner gparted will not see the raids unless kpartx is installed. If that is the case you can install it to the live session and proceed with starting the install from there. 

In the case of Win 7, I suggest using the win7 to shrink a partition beforehand to provide sufficient unallocated space to install Ubuntu to. Then in the live cd, after installing kpartx if needed, use gparted to create an extended partition to install to. Then start the installer (from the live session desktop icon) and in the partitioning step elect to manually partition. In the next step offered, selecting the unallocated space in the extended partition and electing 'change' create a partition of at least 10 Gb of a ext4 type, elect to format and set '/' as the mount point. Leave enough space to create a swap space at least as large as your ram. Then you can go thru the remaining steps to complete the install. And that should be it. You should now have a bootable system. Some raid systems might not install grub properly. That is fixable. Post here should you  need more help. Good luck and enjoy.

---

### Post by Luke oX on 2011-01-15
I have booted the live cd, and gparted sees both HDs and does not know what to do with them. Also I don't know how to install kpartx, because the command that was given me last time did not work.

---

### Post by Quackers on 2011-01-15
System > Admin > Synaptic Package Manager. When it opens put kpartx in the search box. kpartx will appear in the main window. Right-click it and select "Mark for installation". Click on the green tick in the toolbar to apply the change. Voila kpartx is installed :-)

---

### Post by ronparent on 2011-01-15
Exactly right Quackers. Also the software manager or the terminal (sudo apt-get install kpartx). They all work.

Note: kpartx is not used directly - it functions with gparted to permit gparted to view and modify raid partitions.

---

### Post by dino99 on 2011-01-15
as i know you cant boot on raid0, by the way why using it ? mainly useless and scary

---

### Post by ronparent on 2011-01-15
Pdino99 -  That is true primarily for linux software raid. Fakeraid is bootable from a raid0. I do it all the time. 

It seems to be a safe assumption that since the original poster is turning his raid options on and off in bios that he is using fakeraid.

dino99 - please pardon the multiple post - it seem i was caught by a data base error. I didn't mean to press that point.):P

---

### Post by ronparent on 2011-01-15
dino99 -  That is true primarily for linux software raid. Fakeraid is bootable from a raid0. I do it all the time. 

It seems to be a safe assumption that since the original poster is turning his raid options on and off in bios that he is using fakeraid.

---

### Post by ronparent on 2011-01-15
dino99 -  That is true primarily for linux software raid. Fakeraid is bootable from a raid0. I do it all the time. 

It seems to be a safe assumption that since the original poster is turning his raid options on and off in bios that he is using fakeraid.

---

### Post by ronparent on 2011-01-15
dino99 -  That is true primarily for linux software raid. Fakeraid is bootable from a raid0. I do it all the time. 

It seems to be a safe assumption that since the original poster is turning his raid options on and off in bios that he is using fakeraid.

---

### Post by Luke oX on 2011-01-15
[http://img23.imageshack.us/f/screenshotdl.png/](http://img23.imageshack.us/f/screenshotdl.png/)

I don't know what to do after this...

---

### Post by ronparent on 2011-01-16
It looks like a win 7 install. You would be best off to use win 7 to shrink the larger ntfs partition - shrink that 2nd partition to make at least 10 to 15 gb of unallocated space. Boot to the live cd, install kpartx (again - its only temporary when installed to the live cd), start gparted and make all of that unallocated space into an extended partition (also unallocated). At this point, if you want, you can also create a swap the same size as your RAM, and, use the rest for an ext4 formatted partition  you will use to install to. Then start the install and work your way to the select partitioning scheme screen. Elect the third choice to manually select whre you will install Ubuntu to. In the next screen you pick the partition (or unallocated space if you didn't pre-partition) and hit the change button. In the pop up screen select your partition type (probably ext4), check to format, and select the '/' as the mount point. Now you should be good to go. 10.10 should automatically overwrite the win 7 boot sector with a grub 2 one allowing you to select either OS from the grub menu on reboot.

---

### Post by ronparent on 2011-01-16
It looks like a win 7 install. You would be best off to use win 7 to shrink the larger ntfs partition - shrink that 2nd partition to make at least 10 to 15 gb of unallocated space. Boot to the live cd, install kpartx (again - its only temporary when installed to the live cd), start gparted and make all of that unallocated space into an extended partition (also unallocated). At this point, if you want, you can also create a swap the same size as your RAM, and, use the rest for an ext4 formatted partition  you will use to install to. Then start the install and work your way to the select partitioning scheme screen. Elect the third choice to manually select whre you will install Ubuntu to. In the next screen you pick the partition (or unallocated space if you didn't pre-partition) and hit the change button. In the pop up screen select your partition type (probably ext4), check to format, and select the '/' as the mount point. Now you should be good to go. 10.10 should automatically overwrite the win 7 boot sector with a grub 2 one allowing you to select either OS from the grub menu on reboot. have fun.

---

