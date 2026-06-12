---
title: "I dual boot and am worried about upgrading"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by ratdog on 2012-11-18
Hello,

My laptop uses grub 1.5 to load Ubuntu 10.04 and Windows 7.  I want to upgrade Ubuntu with a fresh install and still be able to access Windows 7.  If I remember correctly, grub is no longer used.  What do I need to be aware of before I reinstall Ubuntu so that I can still have access to Windows 7?  I have software installed on the Windows 7 partition that would not be easy to recover.

Thanks for the help!

---

### Post by oldfred on 2012-11-18
I do not think there was a grub 1.5. There was grub legacy which had a max version of 0.97 and grub2 which started at about 1.9x. The very newest Ubuntu now uses grub2 version 2.00. Ubuntu 12.04 uses grub2 1.99 and will update to v2.00 with the next point release in Jan.

Backups are the most important thing. And you will want a liveCD of the new version if you have to make repairs as grub needs the same version liveCD to make correct repairs.

Are you directly upgrading in place or reinstalling clean? Best either way to test liveCD to see if all your hardware still works and see the new Unity interface. 

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
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
       Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by ratdog on 2012-11-18
Thanks for the reply and the info.

OK,  I knew I remembered about 1.5, but what it says on startup is "GRUB loading... step 1.5.  I don't know what version I have.

I'm just wanting to do a fresh install of Ubuntu, and shouldn't be touching the Windows partition, so I'm not really worried about backing up Windows.
  
What I am worried about is still being able to load Windows from the GRUB if a new GRUB is installed.  Will the Windows option disappear?  What do I need to know to be able to get the Windows option back if it does disappear?

---

### Post by oldfred on 2012-11-18
Stage 1.5 was one of the parts of grub legacy booting.

Grub legacy found XP installs ok, but almost never found Windows 7. We normally had to manually add a Windows 7 boot stanza to menu.lst.

With grub2 on a sudo update-grub it also runs its os-prober. The os-prober finds just about any other system installed and will add a boot stanza for it.

If for any reason it does not work, it often is a Windows issue and then Windows repairs are required. And occasionally we have to update something manually but now Boot-Repair fixes most of the common issues.

Be sure to have the current version liveCD of Ubuntu. Also double check that everything still works with your hardware and understand the new Unity gui.

You need the current version liveCD to be able to reinstall grub or can download Boot-Repair into the liveCD.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ratdog on 2012-11-19
Thank you so much!

I feel a lot more confident about doing the upgrade.

---

