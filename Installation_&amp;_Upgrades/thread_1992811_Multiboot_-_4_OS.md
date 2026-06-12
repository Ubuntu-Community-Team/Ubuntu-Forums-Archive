---
title: "Multiboot - 4 OS"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by ecsubutnu on 2012-05-31
I am looking to install the following on one 320 GB hard drive:

Win 7
Win 8
Server 2012
Ubuntu 12

What is the recommended HDD configuration and install sequence for this setup?

---

### Post by oldfred on 2012-06-01
What Server 2012?

One drive makes it a bit more difficult as Windows wants to boot from primary partitions and Windows 8 does not play well even with other Windows.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Use two of the primary partitions for Windows and the extended and install Ubuntu into logicals in the extended. Windows will install to one NTFS partition if you create it and format it NTFS first and set boot flag, otherwise Windows 7 installs to two partitions. Not sure then what Windows 8 does.

---

### Post by ecsubutnu on 2012-06-01
I started out by doing the Win 7 install and made three partitions for the three Windows OS and of course it created the system partition of 104 MB.  I now have the free space left and am not sure if I do the Ubuntu install if it will mess up the boot manager for the rest of the OS...

---

### Post by ecsubutnu on 2012-06-01
I may be better off running Ubuntu as a virtual machine in Windows.  I primarily work with Windows systems, but like to test Linux distros for possibilities in implementing customer systems.

---

### Post by oldfred on 2012-06-01
If you used the 100MB boot partition and 3 system partitions you have used all four primary partitions that MBR(msdos) partitioning allows. You cannot create a 5th partition. You have to use one of the 4 primary partitions as the extended to hold the logical partitions that Ubuntu can use. 

Windows will install to a logical partition as long as it can boot from a primary partition. Not sure it that applies to 8 or not. It litterally moves all the boot files from the second install to the primary partition with the boot flag. We see many users who have XP, install 7 then delete XP and wonder why they cannot boot 7. All of 7's boot files were in the XP partition as it was the primary partition with the boot flag (or active partition in Windows).

You can put a full install of Ubuntu in a flash drive of 8GB or more. I have a full install of 12.04 in a 16GB flash with 8GB / and 8GB for data. It is not speedy (slow writes) but functional.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

