---
title: "Format and Reduce WINDOWS 10 on Dual Boot System"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by bit-bit on 2018-11-03
Hi guys,
I wanted to format&reduce the Windows partition and then reinstall Windows 10, having Ubuntu on Dual Boot.
Actually most of the space is dedicated to Windows but I would like to give a fifty-fifty disk space for each partition: it's a good idea or there is a possibility to create a partition for each OS and an extra partition for data? What do you suggest?
And then to reinstall Windows I just delete its partition with GParted then start with the installation?

Thank you :)

---

### Post by yancek on 2018-11-03
Why re-install windows?  Is it not booting?  If your windows is functional, just go to Disk Management in windows and resize/shrink the largest partition.  If it is functional and has been installed for some time, you might want to run Disk Defragmenter first.  After resizing, it would be a good idea to re-boot into windows and run chkdsk.  After doing this, you can then install Ubuntu on the unallocated space created after shrinking windows.  If you use the manual (Something Else) option in Ubuntu, you can set the size of your partition for Ubuntu as well as a separate /home or /data partition.  If you want a data partition you can share between Ubuntu and windows, format it to ntfs.

---

### Post by bit-bit on 2018-11-03
I already have Ubuntu installed and tried multiple times to defrag and shrink but never succeded to empty more than 20GB (on more than 300GB free). It's not a problem for me to format Windows and it's a thing I've planned for weeks, so while I'm doing this I would like to reserve more space for Ubuntu.

The data partition will be available both for Windows and Ubuntu (formatting in NTFS)? So now I can give windows partition 200GB for example and the other 6-700GB for data?

---

### Post by oldfred on 2018-11-03
This is old info, but still applies:
       Resize Vista partition, similar for newer Windows.
If problems, try temporarily disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC or Disk Management.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS. 


    Is Windows UEFI or BIOS boot? If preinstalled it is UEFI.

---

### Post by bit-bit on 2018-11-03
It's UEFI. 

So I resize partition size (hope to succeed :P) and then create the partition for data? Can I later reinstall Windows on that resized partition?
Thanks

---

### Post by Mark Phelps on 2018-11-03
The Partition Wizard tool mentioned by @oldfred does allow you to shrink the Windows OS partition more than the stock built-in Windows tool does.

I would recommend trying that first before going to all the trouble of reinstalling Windows.

---

### Post by yancek on 2018-11-03
You can re-install windows to an already existing ntfs partition if you use the Custom install option.  That choice should be available right after the screen with the EULA for microsoft.  You should be able to select that specific partition at this point.  If you use the standard windows install, it is likely to overwrite everything on the disk without asking or informing you.

I would think it would be a lot easier to use the suggestion to use 3rd party software to resize/shrink your windows rather than re-installing.

---

### Post by bit-bit on 2018-11-04
Forgot to reply :D
I installed Windows on a reduced partition and the remaining part is now for data.. thank you guys!

---

