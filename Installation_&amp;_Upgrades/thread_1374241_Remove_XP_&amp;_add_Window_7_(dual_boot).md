---
title: "Remove XP &amp; add Window 7 (dual boot)"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by jryprt on 2010-01-06
I have a dual boot setup with XP & ubuntu 8.04 how do I remove XP & add Window 7 
Thanks

---

### Post by presence1960 on 2010-01-06
> **jryprt said:**
> I have a dual boot setup with XP & ubuntu 8.04 how do I remove XP & add Window 7 
Thanks

You can boot the windows 7 DVD and install over the XP partition. I would format to NTFS the XP partition from the windows installer .

When windows 7 is installed you will have to restore GRUB to MBR as Windows will write it's bootloader over GRUB on MBR.

The method of reinstalling GRUB varies depending on which version of GRUB you are using, either GRUB 0.97 or GRUB2 (version 1.97). Post back which version of GRUB you have if you don't know how to reinstall GRUB.

---

### Post by kansasnoob on 2010-01-06
> **jryprt said:**
> I have a dual boot setup with XP & ubuntu 8.04 how do I remove XP & add Window 7 
Thanks

Just general process without seeing your specific partition arrangement:

#1. Backup all data on XP - it will be gone for good!

#2. Install gparted in Ubuntu if it's not already and go to System > Administration > Partition Editor. Then right click on the Windows partition and select delete, then apply. Do NOT create a new partition or format anything, just leave the new space unpartitioned.

#3. Insert the Windows 7 disc and reboot, it should come to a screen that looks similar to this:

 [ATTACH]142702[/ATTACH]

Be absolutely certain to choose "Unallocated Space".

#4. When the installation is complete you'll only be able to boot Windows so you'll need to restore grub like this:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

You may also need to edit the menu.lst as it will still show Windows XP.

Basically other than deleting a partition rather than resizing just look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by presence1960 on 2010-01-06
> **kansasnoob said:**
> Just general process without seeing your specific partition arrangement:

#1. Backup all data on XP - it will be gone for good!

#2. Install gparted in Ubuntu if it's not already and go to System > Administration > Partition Editor. Then right click on the Windows partition and select delete, then apply. Do NOT create a new partition or format anything, just leave the new space unpartitioned.

#3. Insert the Windows 7 disc and reboot, it should come to a screen that looks similar to this:

 [ATTACH]142702[/ATTACH]

Be absolutely certain to choose "Unallocated Space".

#4. When the installation is complete you'll only be able to boot Windows so you'll need to restore grub like this:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

You may also need to edit the menu.lst as it will still show Windows XP.

Basically other than deleting a partition rather than resizing just look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

+1

That will work too.

---

### Post by jryprt on 2010-01-06
Thank You presence1960 & kansasnoob I am waiting for Window 7 to get here then I will try it does not look hard.

---

### Post by darkod on 2010-01-06
I would dare to disagree with kansasnoob, at least with the part about deleting the XP partition. From my limited experience with installing win7, if you use its installer to create the system partition from unpartitioned space, it will also create the small 100MB boot partition. This partition is completely useless and depending on your partitions it can make complications for you (now or later) by wasting one primary partition for the 100MB. Win7 works just fine without the 100MB separate partition.
I would go with the option presence initially mentioned. Just use the same XP partition for the win7 system partition and format it as ntfs during the install. That will wipe XP completely.
Of course, as mentioned, copy everything you need from XP first.

---

### Post by jryprt on 2010-01-18
> **kansasnoob said:**
> 

#4. When the installation is complete you'll only be able to boot Windows so you'll need to restore grub like this:

Basically other than deleting a partition rather than resizing just look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

This worked great Thank You

---

