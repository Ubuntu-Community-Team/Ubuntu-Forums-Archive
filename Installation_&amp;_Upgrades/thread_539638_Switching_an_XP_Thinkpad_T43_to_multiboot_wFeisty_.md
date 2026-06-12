---
title: "Switching an XP Thinkpad T43 to multiboot w/Feisty Fawn 7.04"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by CorbaTheGeek on 2007-08-31
My Thinkpad T43 had a 40GB drive with Windows XP Pro.  I wanted to run Ubuntu on my T43, but still have some important files/applications on XP so I wanted to have the option of booting to either OS.

With the OS and my files, I was using up about 33 GB of space on the drive.  So, as part of the switchover, I upgraded the machine to an 120GB drive for about $100 so that there would be ample room for both OSes.  (If you do the hardware upgrade, make sure you purchase a PATA drive, since SATA won't plug into the T43. Most of the 2.5" laptop harddrives that I saw at Fry's are SATA now.)

The basic strategy was to backup and restore the entire C:\ drive to a larger harddrive, then shrink the C:\ partition so that Ubuntu 7.04 could be installed on the same drive.  So, here are the steps that I went through to convert my Windows XP Pro Thinkpad T43 to a multiboot configuration with Ubuntu 7.04 (Feisty Fawn):

[LIST=1]
[*]Download the latest [IBM Rescue and Recovery software, version 4.1]("http://www-307.ibm.com/pc/support/site.wss/MIGR-4Q2QAK.html")
[*]Back up the Windows XP drive using the IBM Rescue and Recovery 4.1 utility to a network drive. I iniitally tried backing up to a USB drive but that wasn't detected properly when the IBM Rescue and Recovery CD-ROM booted up...  Just FYI, the backup consumed around 20 GB.  (There is an Thinkpad recovery partition on the T43, but you don't need to back that up.  It is automatically installed by the IBM (okay, okay,... Lenovo) Rescue and Recovery CD.)
[*]As part of the backup process make sure you create a restore CD.  Don't forget!!!  (You'll use that in step 5 below.)
[*]Shutdown the laptop and replace the 40GB drive with a 120GB drive. Instructions are in the [IBM Thinkpad T43 Troubleshooting Guide]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/39t2332.pdf").  (The trick (?) is to open the laptop lid slightly, otherwise the harddrive adapter is caught behind the lid.)  There is one screw on the outside of the case that releases the harddrive.  Once removed, the harddrive is mounted in a frame that takes 4 screws to remove.  Make sure you maintain the same orientation when putting the new drive in the mount.  Now put it all back together, and...
[*]Boot up with the IBM Rescue and Recovery CD
[*]Choose the restore all files option. The next dialog box asks for the backup medium.  In my case I specified "Network" and was prompted for the location of the network drive.  It's in the format of \\servername\drivename and hopefully you've noted that location before this step ;-)
[*]Take a Looooonnnnggg break.  The restoration of 33GB took a couple of hours.
[*]Take out the CD and reboot.  Should reboot just like before (to XP), only now with 120GB of space on C:\.
[*]Shutdown the laptop.
[*]Boot up using the Ubuntu 7.04 Feisty Fawn i386 Workstation DVD.  Your BIOS needs to be set so that it boots from a CD/DVD before the harddrive.  (I believe this is the default.)
[*]Run 'sudo gparted' from a terminal and decrease the C:\ partition size to about 60GB.  (60GB is arbitrary.  But whatever size you decide on, it has to be enough to accommodate the Windows XP data, but you knew that...)
[*]Reboot and make sure that XP is still working with a 60GB partition.
[*]Reboot again, this time with the Ubuntu 7.04 DVD.
[*]Install Ubuntu Linux to the **unused** partition.  Make sure to reserve enough space for a swap partition when selecting the new partition sizes.
[*]Proceed with installation.  Grub automatically recognizes the XP partition and adds it to the multiboot configuration.
[*]Once installation is complete, reboot your laptop and note the Grub multiboot goodness!  You get about 5 seconds to select the OS that you want to boot up to.  (The latest Ubuntu kernel is the default.)
[/LIST]
Questions and comments welcome!

---

### Post by wolfen69 on 2007-08-31
i think it wouldve been easier to back up your files on xp to a usb drive, then repartition, install xp, then ubuntu. but then again, i prefer fresh installs when doing things of this nature.

---

### Post by CorbaTheGeek on 2007-08-31
> **wolfen69 said:**
> i think it wouldve been easier to back up your files on xp to a usb drive, then repartition, install xp, then ubuntu. but then again, i prefer fresh installs when doing things of this nature.

True, true,...  but I didn't want to have to reinstall and reconfigure things (like my Flex Builder/Eclipse installation which has 3 hotfix patches and all my workspace configurations in it) that I've spent a lot of time setting up.  I wanted all the old XP applications ready to go, so that's why I did it this way.

---

