---
title: "Update to 16.04.1 on dual boot system fails"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by Bob_Dennis on 2016-08-18
Two step problem.
1.  I tried updating Ubuntu Studio from the desktop when prompted to do so.  This crashed, leaving me with a blank screen, part way through, possibly because the update program interpreted some mouse movements as mouse clicks. (The problem occurred when I was trying to answer a question, don't remember what it was about.)  Now Ubuntu won't start, error is "Target filesystem doesn't have requested /sbin/init".  Is there a way to recover from that?

2.  I downloaded an ISO image and booted it from CD.  When I tried to install the new version I could not figure out how to install it in the same place as the partially-updated version.  As far as I can see, the partitioner wants me to create a new partition, rather than overwrite the old partition (with partially-updated Ubuntu).  Of course, it would be better to update just the OS, leaving user files untouched, but I suspect that's not possible now. Also, I don't see to have the option of just formatting the old Ubuntu partition to get rid of the old files.  Should I just reduce the size of the old partition as much as possible and put up with the loss of disk space?  I am also a bit worried that the old partition also thinks it is Ubuntu 16.04.1, which I suppose could cause problems with the bootloader.

The other OS in my dual boot is Windows 10. Computer is a Lenovo B590

---

### Post by oldfred on 2016-08-18
Is system UEFI with gpt or BIOS with MBR partitioning?

Is Windows fast start up off?

I prefer to separate system like / (root) from data like /home or more advanced keep /home inside / but have a separate /mnt/data partition. Disadvantage of data partitions is that you have to manually create, add to fstab, and set ownership & permissions. A /home during install does all that automatically.

If /home is inside /, there is the dirty install. All your changes to exisiting configuration files will still be overwritten. You will not keep installed apps( why I export list as part of backup), but all your files that are not part of system are not changed.
Dirty install is reusing partition but NOT checking the format box. Normally a reformat totally resets everything. It also removes old logfiles and other cruft that does build up over time as most do not do thorough housecleaning regularly. 

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by Bob_Dennis on 2016-08-20
No idea on your first question, on UEFI or BIOS.

However, the problem seems to have resolved itself, leaving me even more confused.  I discovered that Windows also had been damaged, so I reinstalled that.  Then, when I tried again to install Ubuntu from DVD, the menu gave me the option of installing over the previous failed install.  That option was not available on previous attempts.  So I suppose that reinstalling Windows somehow cleaned up the partitions.  Anyway, I'm now up and running on both OSs, just need to reload my apps.

---

