---
title: "Partition for  Dual-boot Win 7 &amp; Ubuntu 12.04 on HP Pavilion dv6-6052ea"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Village on 2012-05-29
Hi there,

I am having some difficulty sorting out a dual boot option for MS Windows 7 and Ubuntu 12.04 on my HP Pavilion dv6-6052ea I was hoping to set it up like this and seem to be having difficulties:

**750gb HDD**
104mb (Assume that this is for Windows 7)
120gb Windows System Partition
605gb Windows Data disk
20gb Ubuntu 12.04
5gb SWAP

Can someone tell me if this is even possible or am I missing something here?

Also having re-installed Windows 7 I am having a few difficulties and I am going to put that down to HP driver problems. 

Thanks

Village

---

### Post by oldfred on 2012-05-29
Almost all HPs come with all 4 primary partitions used. So you have to delete one. Best to burn image DVDs, and then you can delete either the backup image and/or the HP tools. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
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

---

### Post by Village on 2012-05-29
OK, thanks for the very comprehensive answer, the Full Circle Magazine was very useful. 

I think I know undersand the problem, although I'm still not sure if I am able to have the disks set up in the way I want at the end? 

Does this make sense to everyone with logical and primary partitions?
[B]
750gb HDD[/B]
104mb (Assume that this is for Windows 7) *Logical*
120gb Windows System Partition *Primary*
605gb Windows Data disk *Primary*
20gb Ubuntu 12.04 *Primary*
5gb SWAP *Primary*

Thanks
Village

---

### Post by Village on 2012-05-29
Hold on just re-reading the Full Circle Mag and am I understanding it right where it says that Ubuntu can be run of logical and not primary partitions?

I thought that OS's had to be run off primary partitions? Any clarification?

Thanks
Village

---

### Post by anonymous5 on 2012-05-29
> **Village said:**
> Hold on just re-reading the Full Circle Mag and am I understanding it right where it says that Ubuntu can be run of logical and not primary partitions?

I thought that OS's had to be run off primary partitions? Any clarification?

Thanks
Village

You can have a maximum of 4 primary partitions in a single hdd. If you want more partition, create an extended partition, which is a special primary partition that can hold logical partitions. So you can have for example 3 primary partitions and an extended one which contains other logical partitions.
Logical partitions act just like primary partitions and you can install Ubuntu wherever you want.

Take a look here for more :
[http://www.ahuka.com/other/partition.html](http://www.ahuka.com/other/partition.html)

---

### Post by Village on 2012-05-29
Right,

It looks like I have been able to get the laptop set up how I would like, and now I seem to understand a little more about partitions. 

Thanks for all your assistance!

I now need to get Windows and HP into the shape I like them. 

I did that in Ubuntu pritty quickly. 

Thanks

Village

---

### Post by oldfred on 2012-05-29
Windows has to boot from a primary partition and Windows 7 creates a separate 100MB hidden boot partition (often sda1). They claim it is so you can encrypt your main Windows partition as the boot cannot be encrypted. It also has the recovery software as the assumption is you may have issues with the main partition but not the boot.

I think it is just so they can use all four partition, then users do not install another system and make their lives difficult as their repair scripts do not know how to handle non-standard configurations.

Linux boots & reads logical partitions just fine. Windows will also read a shared NTFS partition for data you may want to share between Windows and Ubuntu. I have my Firefox & Thunderbird profiles in a shared NTFS partition.

---

### Post by Village on 2012-05-30
All a bit frustrating really with MS Windows.

I have a shared "Data" drive between the two OS's. 

Got to say that 12.04 looks good! 

Village

---

