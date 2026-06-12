---
title: "[SOLVED] inconsistent ubuntu studio installation DVD-I ran the checkdisk 1st!"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2007-12-14
Hi!
I had Ubuntu Studio and JAD installed on my 2cnd HD (windows on the SCSI) and messed up grub.  So I deleted then formatted the separate primary boot partition that had been created to allow 2 linux distros to boot and then formatted a logical partition to put Ubuntu.  I got a new USt. DVD from the tech who seemed to burn it properly and I checked the DVD for errors 1st with the disk integrity check.  

I had to install manually and the 1st time I botched the grub by calling the partition hda rather than sda so I reformatted the boot partition to be sure and remounted it again.  I then erased and reformatted the partition for the OS and mounted it as / (root) again.  This time everything went fine exept there was no network detection at all and worse, the install did not ask me for a superuser or user name/password!  So U.Studio is installed but I can't log in.  Grub found windows but no JAD (which may be more to do with extended partitions having been wiped from the list in the MBR when I deleted it (the 1st partition).

Long Story Short!  Does it sound like I need to get another copy (it was burned at 2x). I can also try to burn at 1x with my older- newly installed DVD drive- which my motherboard finally could recognise and boot with!  How can an install DVD do things once then omit things the next time-is there a bug know to gutsy install? 

In recent times, I began tinkering with linux on older computers and going nowhere then getting warmer with installing on my main computer ( heck with help I actually am using Xubuntu on my P3!  so that's progress), I still consider myself a newbie and it has given me much headaches, but I won't quit 'til I reach the pot of gold- exploring the great open source multimedia software!)   
Any help is GREATLY appreciated!  
note to self: next time minimise or eliminate multi-boots!:guitar:

---

