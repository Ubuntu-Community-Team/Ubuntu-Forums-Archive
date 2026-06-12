---
title: "Can't seem to install Ubuntu (14.10). Stuck on &quot;Preparing to install Ubuntu&quot;"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by bogedy on 2015-01-31
I have Windows 8.1 on my computer. Recently it's been weirdly slow and buggy, and for some reason takes an enourmous amount of time to boot. The bios part before Windows seems to take forever to boot as well. I got all my files off of Windows and now I want to install Utopic, wiping everything in the process.

When I go to install Ubuntu, after I select my language, I get to the "Preparing to install Ubuntu" screen. It has check boxes for downloading updates while installing and shows that I have enough space and am connected to the internet. When I click continue, I get the loading icon and nothing.

I suspect that something is wrong with my hard drive. So I open GParted to look at the drive. It too is stuck. It is completely grayed out and is stuck saying "Searching dev/sda partitions".

I appreciate any help you can give!

update:

I left Gparted running al night and nothing happened. Restarted the computer, seemed to be the same, and then somwething came up!

[IMG]http://i.imgur.com/tTUypgW.png[/IMG]

The warning says:

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.

---

### Post by mörgæs on 2015-01-31
Are you able to read SMART data from a live boot?

---

### Post by bogedy on 2015-01-31
I'm sorry, I don't know what that is. Could you tell me where to look?

---

### Post by fantab on 2015-01-31
You don't have space to install Ubuntu. Ubuntu or any Linux will NOT install to the NTFS partitions. You'll either need linux compatible filesystem like, ext4 or you need to leave some (20-30)Gb unallocated space for linux to install.

If you were using Windows8 then, have you disabled [FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") and properly shutdown Windows?

SMART test can be run on the Hard Disk using the utility 'Disks' which is part of Live Ubuntu. You should boot Ubuntu in 'Try Ubuntu' mode from DVD/USB.

---

### Post by yancek on 2015-01-31
After disabling fast startup and rebooting windows, you may need to run the check disk command explained at the site below, then run disk defragmenter, then use the windows Disk Managment to shrink the windows partition to make some unallocated space on which to install Ubuntu.  

[https://technet.microsoft.com/en-us/magazine/ee872425.aspx](https://technet.microsoft.com/en-us/magazine/ee872425.aspx)

---

