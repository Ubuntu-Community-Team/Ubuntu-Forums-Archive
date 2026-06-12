---
title: "Dual Boot - install woes -- Ubuntu doesn't see my Windows boot drive (SSD)"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by datdaddy on 2016-10-14
I have done a dual boot install on many machines over the years and had good success.  I'm now running Win 10/64 and want to do the same.  I shrink my Windows partition on my SSD, then boot with the Ubuntu live, and choose the install alongside option.  then I'm presented with NOT my main drive which has the Windows partition and the free space I just made (70 gig) - but rather the 4 gig "storage" drive I have in the machine.  The SSD is nowhere to be seen in the dropdown.  If I go to the advanced options, I see the space I made for the Ubuntu, but don't know what the heck to do at that point.  At one point I tried to choose that 70 gig space and it told me it could not be used (for what reason I can't remember now.)  Any tips on how to get this thing going?

Thanks much.

---

### Post by yancek on 2016-10-14
I don't use UEFI but from everything I've read, you will have problems using the auto-install (Install Alongside) method with UEFI which your windows almost certainly is.  You need to select the manual (Something Else) option so you have some control over where to install.  Read the Ubuntu documentation at the link below on dual booting windows/Ubuntu UEFI.  

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Posting the reason it would not use your 70GB space from the Advanced options would certainly be useful information.  Do you have windows hibernation off before you boot?  windows 10 is almost always UEFI if pre-installed so you might check to see if it is.  If you installed it yourself, you should know.

---

### Post by oldfred on 2016-10-15
You cannot make partitions in Windows for Ubuntu.
But should use Windows to shrink the Windows NTFS partition & reboot so it can run chkdsk. And fast start up must be off for Linux NTFS driver to be able to see the NTFS partition with Windows in it.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

From my link below in my signature.

 Summary UEFI install instructions:
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit installer, flash drive or DVD.
Use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot.
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

### Post by datdaddy on 2016-10-15
I'm Legacy, not UEFI.  Just ran the shrink in Windows, rebooted into Windows, then rebooted with live UBUNTU USB.  If I go into advanced install, it shows me the 70 GB there as unallocated space, but I'm at a loss as to what to do at that point.  Usually when I've done this, it just finds the space and uses it without much intervention on my part.  Of course I'm an idiot with Ubuntu, and if it don't go easy, I'm just lost.

---

### Post by oldfred on 2016-10-15
It depends on install option, choose wisely as several like full drive encryption are full drive meaning entire hard drive and erase Windows.
And you have to have fast start up off in Windows for Ubuntu installer to see it with the standard install along side.

Generally better to use Something Else, but then you have to design your own partitioning scheme instead of the default of / (root) & swap. I prefer manual partitioning mainly as auto usually makes swap too large as it assumes you may want to hibernate. If more than 4GB of RAM you do not need large swap normally.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Some of these are older versions, but process is still the same.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

