---
title: "Help upgrading Windows 7 netbook dual boot to Quantal Quetzal 12.10"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by bulldogwings on 2013-02-07
I used wubi to uninstall older version and then installed
12.10 from USB stick.


Hi All,

I have a Toshiba Netbook that came with Windows 7 starter.
I upgraded the RAM to 2GB and installed ubuntu 11.04 using
the windoze installer. [I know, wipe the dreaded OS and make it pure Linux - can't as my wife cannot handle anything past using the bootloader]

I have moved to a place with hideous internet connectivity so
after several abortive attempts to download 12.10 I purchased
a bootable USB stick with version 12.10.

Boots into 12.10 great and I love the new version.

I would like to upgrade to 12.10 (i.e. remove 11.04 or over write it) so that I have only Windows 7 and 12.10.

Sadly, I cannot seem to find the key to this feat in the forums.
I don't want to hose the netbook mucking about, so I am here, hat in hand.

I would be very appreciative of any guidance from other members.

Cheers!

---

### Post by oldfred on 2013-02-08
I do not know wubi. Are you wanting to install a new version of wubi? Or a full partitioned install. If you like Ubuntu you may want a full install.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

            [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubiwubi](https://help.ubuntu.com/community/Wubiwubi)

    
       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

    
Often the issue with most Windows 7 systems is that all 4 primary partitions are used and you have to delete one. Then best to have full backup of Windows and a Windows repairCD. Then you may have to delete the Vendor recovery after making the Vendor recovery set of DVDs or a Vendor tools partition to make an extended partition to allow several logical partitions for Ubuntu.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

