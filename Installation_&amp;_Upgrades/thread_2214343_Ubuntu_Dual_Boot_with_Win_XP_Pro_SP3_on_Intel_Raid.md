---
title: "Ubuntu Dual Boot with Win XP Pro SP3 on Intel Raid 1 mobo array"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by david179 on 2014-03-31
Good Morning,

  I am attempting to set up a dual boot system on a raid 1 array with Win XP.  I am completely new to Ubuntu, however I did a lot of reading and figured I'd try to complete the subject title configuration on a refurb project.  
The current setup is: 
Dell Dimension e520 running bios 2.4xx
Pent 4 2.xx Ghz HT 775
3074 MB system memory
2x 160 GB WD SDA's.
Intel ICH7R chipset
onboard floppy, dvd, and usb.

I installed windows XP onto the raid 1 array after a bios flash from Dos using intel raid drivers in tandem via floppy with the xp pro installation cd.  I partitioned the array using 100GB for the Windows partition leaving 50.x GB for Ubuntu 12.04 LTS. XP pro is updated and works properly.

At first I tried using the Desktop ISO vis USB.  After trying Ubuntu live I was unable to see the raid array form the desktop.  Using Googled / forum reading I found that I needed to download and use the [B][U]Alternate ISO to DVD. *I did*
[/U][/B]I booted from the ISO and started the Installer.  The LIVE "Try Ubuntu" was not an option using the alternate ISO, which I was hoping it would be.
The installer loaded dmraid scripts among others on the package prep status line on the bottom of the screen, and the installer allowed me to proceed to the partitioning portion of the installer.
The intel Mobo raid was visible showing the Windows 100gb partition, and the 50.xx GB's of free space.
I went about setting up my partitions in the free space as follows:
16Gb as a primary partition of the root "/"  *I did not rename it I left it as a "/".
33.xx GB as a logical partition for /home in EXT 4
 3074MB as a logical partition for /swap in /swap "took me a minute to realize that I had to change EXT 4 in the drop down and select swap" -->I'm a newbie go ahead and chuckle.

I then proceeded to write the partitions to the raid 1 array.
I confirmed that it was only writing the EXT 4 partitions / swap and not overwriting the WIN XP partition.

Installer failed on creating the swap partition posting an error to the tune of "unable to write to the disk while disk is being read dev #126 failed, etc". 

I improv'd and played around with the partitioning. 
I let the alternate installer create partitions for me "failed with same error"
I created the same partitioning tables w/o the swap file since the error specifically called out "failed to create swap" etc.  This failed with the same type of error for creating the /home partition again "failing to write to the array while reading device failure #126".

I'm assuming that the installer is unable to write / create partitions to the array for some reason.

I am thinking of using Gparted to set up the partitioning; once I find it on the live ISO. "I read a minute ago that I should use the search command for gparted under the UBUNTU icon that shows your programs"

So, would creating the partitions on the raid 1 array using Gparted from the ISO normal desktop solve the problem?  Would the desktop ISO gparted be able to see the raid 1 array since the normal desktop ISO cannot identify the raid properly without the dmraid files? If I am able to partition using Gparted from the normal ISO will the alternate ISO installer have problems skipping the partitioning portion of the installer and be able to write/install to the array proceeding with the OS installation?  If I am not able to find/use Gparted from the live ISO desktop is there a way to run Gparted from the alternate ISO that would accomplish the partitioning that the alternate ISO installer cannot?

Should I do something else entirely besides what I outlined above?

Thank you for any time you spend reading and/or responding.

V/R

Dave *Linux Newbie*

**Update 4/2/14**
I found and ran Gparted.  Gparted detected my SdX's, however instead of 1 raid disc the program recognized it as sda & sdb.  Each device showed a 100GB NTFS partition and 50 gb of free space with a partition table of MSdos.  I then started playing with the partitions and the alternate ISO as follows:
sda- created 50.xxgb extended partition in EXT 4.  Created logical partition sdb5 16gb "/" EXT 4 , logical partitition sdb6 31gb "/home" EXT 4, logical partition 3gb "/swap" /Linux-swap. ran operations.  Gparted operations successful.  sda device partitioned.  sdb partition shows free space.
I rebooted and ran alternate ISO cd.  Installer went to partition creator.  Partition tool recognizes raid, but as 160GB instead of 100gb ntfs, and 50 gb useable.  Unable to select or modify partition without destroying windows.
Reboot ran live desktop iso.  Gparted detected all sdx's.  Deleted sda partitions.   Partitioned again as above, but I created the same partitions manually on sdb.  ran operations.  Now sda and sdb have 50.xx extended partition in EXT 4, and 3 logical partitions on that extended as above.  16gb /, 31gb /home, 3gb / swap.
Reboot and ran alternate iso.  Installer started and saw the same 160gb single partition not recognizing primary ntfs partition of 100gb, or the 50 gb extended partition with the 3 logical partitions inside the extended.
That's as far as I made it before I had to call it quits last night.

Looks as if I need some kind of package or tool running to have Gparted recognize and partition the sdx's that are in raid as one sdx instead of sda, and sdb.  I don't know what that would be at the moment.

---

