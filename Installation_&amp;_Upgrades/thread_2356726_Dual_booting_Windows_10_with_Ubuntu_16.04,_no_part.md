---
title: "Dual booting Windows 10 with Ubuntu 16.04, no partitions shown"
date: 2017-03-26
forum: Installation &amp; Upgrades
---

### Post by tonyhur on 2017-03-26
I bought a Labtop from Dell preinstalled Windows 10 Home and wanted to install Ubuntu 16-04. I partitioned the C: using diskmgmt.msc (20GB for Ubuntu). But after I  started the Ubuntu installation no partitions are shown (The list is empty). in "Installation type" dialog, I did not get the radio buttom "Install Ubuntu alongside Windows boot manager".Thanks for help
Tony

---

### Post by yancek on 2017-03-26
Windows 10 pre-installed is almost always going to be using UEFI so you must install Ubuntu UEFI or you will have problems.  Do not use the "Install Alongside" method but select the "Something Else" option.  Make sure anything related to hibernation or fastboot is off and read through the link below, the Ubuntu documentation on dual booting windows/Ubuntu UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by RobGoss on 2017-03-26
Hello and welcome, When you partitioned the C: do you see the **unallocated** partition space you created?

I would say run the live installer for **16.04.2 ** choose something else and  then the **Unallocated** partition to begin the installation this should allow you to install Ubuntu with out issues

---

### Post by ajgreeny on 2017-03-26
If you used diskmgmt.msc to create a partition for Ubuntu it is likely that you have a dynamic windows partition which will never work for Ubuntu or any other Linux OS.

You will need to delete that new partition you made using diskmgmt.msc again and simply leave the 20GB as unallocated space which the installer should see.

---

### Post by oldfred on 2017-03-27
Did you leave Windows fast start up or hibernation on?
Then Linux NTFS driver cannot mount the Windows partition, if hibernated or if it needs chkdsk.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Always resize the Windows NTFS partition using Windows tools, and reboot immediately so it can run chkdsk.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

