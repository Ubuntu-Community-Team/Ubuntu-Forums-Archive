---
title: "Dual boot Windows 7 and Recovery Partition"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by glock356 on 2012-11-24
Hello!

I am planning to install Ubuntu(or any other Ubuntu base distro) on HP Probook with Windows 7 Home Premium 64 bit preinstalled.
There is one 750 GB disk with Win. system partition(100 MB), and recovery partition(to reinstall Win., drivers, and other HP stuff).
I created two partitions - first I shrink existing partition on which windows is to 120 GB, then created on unallocated space a partition of 600 GB for storing data.
This partition have enough fre space to create an unallocated(unpartitioned?) space for Linux installation.
I know well how to install linux on dual boot, create Linux partitions, so there is no problem.

My Question is - what to be with recovery partition after Linux installation?
It still be usable in case to need reinstall Windows for any reason?

Thanks for answers.

---

### Post by oldfred on 2012-11-24
I hope you did not use Windows to create partitions. Windows will convert to dynamic partitions which are Windows proprietary and do not work with Linux. They also are a one way conversion. Although some third party tools may convert back if you have not made other changes.

Windows also cannot create Linux partitions, it usually does not see them correctly and creates issues. Best to use Windows partition tools to shrink Windows and then use gparted to create new partitions.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

    
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

### Post by glock356 on 2012-11-25
> **oldfred said:**
> I hope you did not use Windows to create partitions. 

Sure i am not using windows for this action.
During installation of Ubuntu(or any other Ubuntu base distro) i allways created unallocated(unpartitioned) space for Linux instal **in windows**.
Then during installation when ask me how and where to install Linux select option **Something else(or Manual in Kubuntu)** and then create partition for Linux - boot, swap, root, home.

I asked this question because i **never before** installing Linux on computer with preinstalled Windows and with this Recowery partition, allways on desktop computer with windows installed by user from DVD.

The laptop is not mine, if be mine sure i am not bothering with this.

Maybe my explanation of problem is not clear, this is for my language limitation, english is not my language.

Thanks for links.

---

