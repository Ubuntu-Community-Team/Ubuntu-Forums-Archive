---
title: "WIn7 error"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by castlerock on 2013-06-24
A little background:

When attempting to install Ubuntu 12.04 on the HDD, It got to the  section where I was to choose if I wanted to install the OS alongside  win7, erase OS7, or something else - so I chose something else in order  to ensure I wasn't using too much disk space as I wanted to still use  Win7 as the primary OS while using Ubuntu as a 2ndary.
  
 Well, I was messing with the partitions and ended up "erasing the  recovery partition" as Ubuntu stated that the partition was created  outside of windows. (A 14GB partition I ended up using for Ubuntu" - So  this partition is where Ubuntu now rests, the problem later on was that  Ubuntu couldn't write its MBR correctly, so I choose to install that on  another partition, thus rendering the OS7 unbootable with the error "MBR  is missing" (Now, I could've fixed the MBR issue easily, but the issue  was the Ubuntu OS did not install, but booted after the installation  with the same MBR error, so after trying to uninstall the Ubuntu  Partition completely so I could go back to OS7, more-less made the  system worse, I then got a custom error as the post I had seen on  acronis forums (can't find it ATM), but I booted into Ubuntu livecd, and  cannot find the HDD there, but it shows the HDD system as a "unknown  for system type: ntfs, fat32 etc - I know it is a NTFS but apparantly  its corrupted) - but it states its healthy.
  
 So - if it has a unknown file structure, but appears to be in working  order - Is it possible to perform a repair using the Win7 install cd (I  am obtaining the ISO from digitalriver right now - once burnt, I will  attempt that, but I also have the EasyRE ISO from Neosmart tech. I will  perfrom at next boot.
  
 SO it appears the OS is not valid - but am hoping the software(s) can  ressurect the original OS files as I do not have F8 upon boot nor any  recovery options that way.
  
 SOrry for the long winded post, hopefully this can be fixed.

__________________
A few extra pix for reference:

The below attatched image may be some use - the post in that thread may pertain to my situation but am unsure?
[IMG]http://imageshack.us/a/img834/2971/rrba.png[/IMG]

Also have this when I ran gparted: This shows Local C:\ as "unknown" - but thru this utility, there is not much I can do.
[IMG]http://imageshack.us/a/img404/7067/k6w4.png[/IMG]

---

### Post by oldfred on 2013-06-25
No that guy oldfred is not correct. :)

If you installed grub2's boot loader to the PBR - partition boot sector of a Windows install you break Windows as it has to have a NTFS boot signature which is separate from the partition table. You can use testdisk to repair that.

But may be best to see details first to be sure we do not make things worse.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

This may be the issue but probalby best to confirm first.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by castlerock on 2013-06-25
haha - that's funny about the post.

Hey thanks for your reponse - I am elated to announce I got this solved last night.

I don't know what really what it was I did, but I did run the boot-repair and it told me it completed the repair successfully. Then I rebooted with the windows repair cd in the drive, ran the start up repair - but usually got the "Cannot automatically repair" the system - I saw that the win7 was not listed in the restore section and that it was listed as "unknown on unknown local drive". BUT - I went ahead and ran the boot repair again, then the start up repair - this time ubuntu was not on the drive, so it did fix something, but then I ran the command prompt, and ran the diskpart  -"this part was critical I believe" - I ran the clean & repair and perhaps a couple other commands and rebooted - and once I saw that starting windows logo - I knew I was set.

So bottom line - don't choose the "something else" option and attempt to mess with partitions - as in my case I accidently deleted and formatted over my recovery partition :( So next time I will simply choose install alongside of.

Also I was testing my USB ports thru ubuntu - it appears to be hardware failure ugh.

Thanks again!

---

### Post by oldfred on 2013-06-25
Glad you got it resolved.

With most Windows 7 systems, you do have to delete one partition as they are configured to use all 4 primary partitions. You have to delete one to create the extended partition, so you can add many logical partitions inside the extended.
The choice is usually between the vendor recovery and the vendor utitlites.
Vendor recovery is only needed it you want to restore system to as purchased. More only if you want to sell system later with a clean Windows.
Better for your use to make an image so have have all the changes you have made to date.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

