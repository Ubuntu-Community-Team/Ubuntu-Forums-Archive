---
title: "Please Help:  Installed Ubuntu, grub did not detect XP"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by betty on 2007-06-07
Hi,

I'm at a loss on how to proceed.  I have two IDE Hd's.  I had windows installed on my SLAVE, assuming the MBR was on the Master.  I then installed ubuntu on the MASTER, and then I did not get an option for GRUB.  instead, the computer boots ubuntu only.  

I know XP is sitting there on the SLAVE drive, but am I going to be able to boot it?  How can I do that?  I DON"T want to go through the installation of XP again - which is a PAINFUL process.

Thanks!!!
betty

---

### Post by mckinneycm on 2007-06-07
Open a terminal session and type:

gksudo gedit /boot/grub/menu.lst

This will allow you to edit your menu file. In there you'll see an example of a Windows menu item. Copy that to the active menu items at the bottom of the file and then edit the entry to reference your second hard drive. For example change the (0,0) to (1,0), so the system will load the OS on Disk 1, Partition 0 instead of Disk 0, Partition 0. Remember that the system uses 0 as the first disk.

---

