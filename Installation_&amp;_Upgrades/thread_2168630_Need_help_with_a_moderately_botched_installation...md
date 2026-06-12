---
title: "Need help with a moderately botched installation..."
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by Andrew_Horwitz on 2013-08-18
I'm more used to CentOS and wanted ubuntu for my own machine. I have a Lenovo W530 with Win8.   
Before botching: 
-Got UEFI disabled 
-Partitioned using EaseUS before realizing that Ubuntu had a built-in partition manager.
 -Tried using the top item in the Install Ubuntu menu (with Windows or something) then realized I should delete the old partition I had made before I did anything
 -Deleted it and tried to expand the original Windows partition so I could work with the aforementioned top item, but didn't realize that EaseUS officially made the change on reboot.  

From here, I rebooted straight to the DVD and tried to install, without realizing that I hadn't actually expanded the partition. Ubuntu said the install was successful, so I rebooted and saw EaseUS fail at trying to expand the partition. I got into Windows with no problem, tried rebooting and it wouldn't register Ubuntu, so I booted EaseUS back up and saw that what was originally a ~260GB Windows partition and ~200GB of free space had become:  

-Same 260GB Windows partition 
-1MB "Unknown" partition (doesn't register in Ubuntu as anything either)
 -~190GB ext4 partition 
-~8GB partition that it says is unused. 

 Those are the only new things from before this debacle. For some brilliant reason I decided to delete the ext4 partition because it said there was nothing in there. After doing so and realizing I may have messed up, I ran boot-repair and got paste.ubuntu.com/6000576/

  I don't think it's possible to recover the partition at this point, but if it is I have no problem doing so. Common sense would dictate that the ~8GB partition is the Ubuntu system files and that the 1MB partition is from Grub (which after a quick Google search seems to be true). Is it safe to just format, delete, and merge those partitions into the free space, then try again? And for future reference, what's the difference between the top choice in the "Install Ubuntu" screen (install alongside Windows) and the bottom choice (the manual partitioning)?  

Thanks to anyone who can help.

---

### Post by zealibib slaughter on 2013-08-18
the top choice automates the process of installing while keeping your windows install (resizing, making new partitions ect.) at this point I would reinstall and use the manual partition to delete everything except windows, create partitions in the ~198-200 GB space that you should have free, and install ubuntu to that area. I really dont think that you will be able to recover the ubuntu install at this point.  As long as windows is booting and you are not blue screening at all then It should be safe to just delete whats corrupt and start over.

---

### Post by Andrew_Horwitz on 2013-08-18
I'm being really cautious in response to the "delete everything except Windows" - there's a few before the main Windows data partition and one that's clearly marked recovery at the end. Should I delete all three in between? (the 1MB one, the free space, and the ~8GB one)

---

### Post by zealibib slaughter on 2013-08-19
in that case i would delete the 8GB one as long as you are sure its ext 3-4 format since that would indicate a nix file system.  the 1MB one err on the side of caution and leave it alone and of course the free space is just that.  Anything marked NTFS, FAT or another dos/windows format leave alone, also any recovery partitions.  Maybe posting a screenshot of what you are looking at would be helpful if you can.  Sorry about the delay getting back to you.

---

