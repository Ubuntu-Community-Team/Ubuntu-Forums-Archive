---
title: "Cannot install 12.04 inside Windows 7"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by forhpm on 2013-02-09
I am trying to install LTS 12.04 inside Windows 7, the first option on the screen. I see a bunch of lines of Stopping and then Starting and after Stopping System V runlevel compatibility, the next line is 

devd[4921]: '/sbin/blkid -o udev -p /dev/sda2' [7362] terminated by signal 15 (Terminated)

Checking for running unattended-upgrades:
acpid: exiting
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
***Asking all remaining processes to terminate...

And I'm told to remove the media, close tray and press Enter. Don't know what's wrong here. 

So next I tried to install the partition manually. I have created both a formatted and an unformatted partition inside Windows but do not see them in the "Something else" option for the install. It shows me sda, sda1, sda2, sda3 which is ntfs and the largest partition, and sda4. How do I get at the Windows partitions already created? In Windows, I now have c: NTFS, 419.9GB, HP_TOOLS Fat32 99MMB, a formatted NTFS partition called L: at 16.51 GB, RECOVERY (D:) NTFS 16.21GB and SYSTEM, NTFS of 199MB. Below on Disk 0 is an unnamed 12.70 GB of unallocated space, not formatted. 

I am using an HP G62 with 500GB Hitachi hard drive, Intel i3, 4GB RAM, 64 bits, BIOS boot (as far as ESC at bootup shows), Windows 7 Home Premium. Please let me know if you need more information to give me a prod in  the right direction!

Thank you!

---

### Post by oldfred on 2013-02-09
Welcome to the forums.

Are you installing wubi? Not many here know wubi, including me.

But I am concerned that you created more partitions in Windows. Windows will not create the extended partition that allows many logicals but converts to a proprietary dynamic partitioning scheme that does not work with Linux. Are partitions still basic or are they now dynamic?

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubiwubi](https://help.ubuntu.com/community/Wubiwubi)

    
Also be sure to have good backups:
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

### Post by forhpm on 2013-02-10
Thanks for the suggestions. I have data backups but will go ahead and create full system backup, etc.,

The partitions are "simple". I did not select anything fancy when creating them, just followed Windows advice, shrink C: so there is extra space and then create the partition in the free space. As I said, I formatted one to NTFS, the other is not formatted at all. 

I'm not understanding why the Ubuntu installation is not seeing the free space. I have read this article [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) but it is not clear on whether I'm manually sizing the Windows partition or sizing for the Ubuntu partition. 

Thanks.

---

### Post by oldfred on 2013-02-10
If doing a full install it needs one more primary partition as the extended to be able to create many logical partitions inside the extended.

But most Windows 7 systems use all 4 primary partitions.

       Install Windows either before Ubuntu or after:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

    
       Dual Boot Win7 & Ubuntu
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

    
       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by forhpm on 2013-02-10
Hi, I must be a total git but I'm trying to copy Mark Phelps' instructions to the letter. How do I copy the HP_Tools files and folders  into the Win7 OS directory? I can't even find it in Computer, which  shows me Local Disk (C: ) and Recovery (D: ). In C:, there is a folder  called HP_TOOLS_mountHPSF but it is empty. There is also a folder called  HP which has four subfolders: Bin, Data, HPQware and support. In D:  there are a few subfolders,: $Recycle.bin, _MSSETUP.T, System Volume  Information and then other icons that say boot, hp, preload, Recovery  and system.sav. When I click on these, the right hand of the window  shows message from HP: "Recovery Partition, Warning. This areo of your  hard drive [or partition] contains files used to perform a system  recovery. Do not delete or alter any of these files. Any change to this  partition could prevent a system recovery in the future."

Thanks.

---

### Post by U202E on 2013-02-10
if you want to do what I did: install ubuntu on a different partition you'd format the ubu partition as ext4.

It's much easier to partition with the ubuntu live cd, but you can install gparted on win7 and format the partition you need if you prefer that.



in case you didn't know: windows doesn't support ext4, because it's a linux fs.
but there is a program called ext2fsd if you want to access your linux files from my computer on win7.

---

### Post by oldfred on 2013-02-10
HP-Tools is usually a small partition with a few HP utilities. I think some have reported that they can easily down load them again.

You only need one partition to convert to the extended partition. So you do not have to delete recovery. But if you have made the full set of recovery DVDs and a full backup the recovery has little use. But if you do not have a way to recover Windows then you have to order replacement from HP for usually a charge.

---

