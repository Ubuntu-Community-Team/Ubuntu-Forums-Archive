---
title: "Cannot &quot;install alongside Windows 7&quot;"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by stuwat on 2012-10-05
I have a Toshiba Satellite Z930. It came with Windows 7 pre-installed and I want to install Ubuntu as well. Unfortunately the Ubuntu installer doesn't give the me option I require, which is to "install Ubuntu alongside Windows 7". It says it detects multiple operating systems and gives me the option to "erase disk" or "something else".

There is actually only one operating system, so my guess is that the problem lies with the number of existing partitions: there are 4 of them. The first is the boot loader, the second is the Windows OS, the third is the recovery partition for Windows and the fourth appears to be something called Intel Rapid Start. I am led to believe that 4 partitions is the max. Is that true? Is the best solution therefore to delete one or both of these last two? Will this then give me the option to "install Ubuntu alongside Windows 7"? Any advice would be gratefully received.

---

### Post by Wim Sturkenboom on 2012-10-05
The maximum is indeed 4 **primary** partitions. You can remove a primary partition and replace it with an **extended** one (this is usually done automatically when you create the first **logical** partition). You can have quite a few logical partitions inside the extended partition.

If the system has an option to make a bootable install CD, use that. Else I strongly suggest that you make at least an image of the recovery partition. 

As I don't have experience with these types of setups, I will not advise further.

---

### Post by Mark Phelps on 2012-10-05
You CAN delete the Recovery partition, but if you do, you will lose the ability to restore Win7 to its original condition.  One good way around that is to download and install the Free version of Macrium Reflect, use that to image the boot and Win7 OS partitions to an external drive, and then use the option to create and burn a Linux Boot CD.  After that is done, you then have the ability to restore Win7 to your current state -- and you no longer need the Recovery partition.

Also, if you are planning on shrinking down the size of Win7 to make room, do NOT choose the side-by-side option using the slider.  Doing so risks corrupting the Win7 filesystem and rendering it unbootable.  Instead, use ONLY the Win7 Disk Manager utility to shrink down Win7.

And finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will allow you to repair the Win7 boot loader -- should that become damaged as a result of your dual-boot installation.

---

### Post by oldfred on 2012-10-05
Many of these new systems with Intel Rapid Start actually have a RAID configuration to use the SSD. 

Some that were willing to remove the Rapid Start from Windows and Install Ubuntu into the SSD. Removing the RAID makes system have two drives.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

Some info on re-instating Rapid Start with Ubuntu on Hard drive.
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by stuwat on 2012-10-05
Thanks to everyone for the great responses. It's really appreciated.

I have created a recovery disk (actually USB drive) for the Windows OS, using the Toshiba software that came with the computer. My plan now is to wipe the recovery partition from the hard drive, but leave the Rapid Start partition in place. I will also shrink the W7 partition from the Windows OS, as advised by Mark. Hopefully I will be left with a working Windows system and the ability to install Ubuntu alongside it. 

Unless anyone has any other advise, I will proceed with that when time permits and report back on my progress. Thanks again everyone.

---

### Post by stuwat on 2012-10-06
I have deleted the W7 recovery partition and the result is that the installer now offers a third option, which is to install Ubuntu alongside the "other operating system". This is good, however I haven't continued beyond that stage because there is one more thing I should probably do first: I am now left with the Rapid Start partition sandwiched between two regions of unallocated space on the (SSD) disk and should consolidate all the unallocated space into one, for the purpose of installing Ubuntu.

My question is: is it okay to move the Rapid Start (hibernation) partition? Gparted warns about the consequences of moving partitions, but I believe this is more a concern for boot partitions. Does anyone know if it is okay to move?

Thanks.

---

### Post by stuwat on 2012-10-06
I moved the hibernation partition which allowed me to maximise the disk space available for my Ubuntu installation. Ubuntu installed alongside Windows 7 and both operating systems are working. Great! 

The funny thing is that Grub gives me the option of booting into Ubuntu, Windows 7 (sda1) or Windows 7 (sda2). Both Windows options seem to do the same thing, so I'm not particularly concerned.  

I took a look at the partitions using the Windows disk manager and sda1 is called the "recovery partition". I thought I'd deleted that, but what I actually deleted was sda4, which was called "HDDRECOVERY" and amounted to a little over 10Gb. What did I delete? Did I delete the wrong thing? Should I have deleted sda1 instead?

---

### Post by oldfred on 2012-10-06
It is confusing.

Windows has a hidden (In Windows) 100MB boot/repair partition. That was primarily so you could encrypt c: as boot files cannot be encrypted. It also has the repair console or f8 when you boot and Windows has to call it Windows Recovery.

The vendor does not provide install DVDs since forever, but creates a image of the hard drive and some tools to rewrite drive to as purchased or create DVDs to create drive as purchased. That is the Vendor recovery partition which I believe you deleted. The only reason to use Vendor recovery might be to totally restore system to as purchased it you wanted to sell to someone who only wanted Windows.

Better to have houseclean all the cruft from Windows, updated it and then make a full image copy of that. Then reinstall is a lot easier.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by stuwat on 2012-10-07
Thanks again for all of this valuable information. I've learned a lot from this experience and am happy to see my new laptop running Ubuntu... as it should be.

---

