---
title: "install ubuntu keep recovery partition"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by andre27 on 2014-08-23
Hi,

I want to install ubuntu on a new laptop.
It's very important that my recovery partition is preserved.
The partition with windows on it (sda2) can be used for ubuntu

I'm a bit scared that I accidentally do the wrong thing, and I find the something else option confusing so bear with me.

Can you please give me a detailed step by step plan for ALL the settings I have to make to install the OS while using the wizard.

(I made a backup of the contents of the recovery partition)

Thanks,

Andre

---

### Post by TheFu on 2014-08-23
Welcome to the forums.

No, a detailed step-by-step plan in a forum post isn't possible with the information provided.  Plus anyone claiming to provide steps will forget a few details - it is human nature. Depending on which small step is forgotten, bad things may or may not happen. Can't tell until it happens.

MBR/GPT disks?  **boot-info** script output would be helpful.
BIOS/UEFI boot?  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Total Storage?  **parted -l; df -h**
CPU model/cores / RAM?  **more /proc/cpuinfo /proc/meminfo**

There is much reading at htp://help.ubuntu.com - or look for an "installFest" in your city for hands-on help.  My LUG will have an installfesst in a few weeks. It is hard to replace the in-the-same-room experience through forum posts.

The main thing will be to pre-allocate the storage for / and swap before you begin, then select "do something else" at the disk partitioning question. Do not use LVM or encryption - or more complexity is required (more partitions).

Of course, having a know-you-can-restore backup of any data is smart. Partitioning can be dangerous for anyone not used to doing all the time.

---

### Post by oldfred on 2014-08-23
While first install can use some of the auto install options, several like LVM or LVM encryption are full drive erase installs.

You do want to shrink Windows using Windows own partition tools and immediately reboot to let it run chkdsk and update to its new size. Make absolutely sure fast boot is off.

If installer does not see Windows, then it will overwrite it. And then Something Else is the only option. And any reinstalls need to use Something Else or entire drive will be erased.

So full back ups of Windows & the efi partition are required.
Backup windows before install - post by Mark Phelps
 [http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
And always good to have a Windows repair tool. You should always have a current version repairCD or flash drive for every system installed. 
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

    
       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by TheFu on 2014-08-23
@oldfred - THAT is a post worthing of saving - sticky - bigtime!  May I use it on our InstallFest pre-reading list?

---

### Post by andre27 on 2014-08-23
Thanks for the replies.
The sure is a lot of reading material.

Just to make my intentions clear: I do not want to keep windows, just the recovery partition that can reinstall windows is to be preserved.
When selectin the installation type I have three options:
1: Install Ubuntu inside windows7
2: Replace windows with ubuntu
3: Something else

If I select something else
I see 5 Devices
1: /dev/sda
2: /dev/sda1   Windows 7 (loader)
3: /dev/sda2   no system info, but this is the partition currently in use by windows
4: /dev/sda3   Windows Recovery environment (loader)
5: /dev/sda4   no system info but this is the partition with HP system tools

below this list I see two buttons: New Partition Table and Revert

In the pulldown I can select the device for bootloader installation
This is set by default to the first option of the list mentioned above

So my question is really what to selection to make

NB: Shrinking the volume does not work for me as windows will not yield enough space.

---

### Post by oldfred on 2014-08-23
@ TheFu
I have even more UEFI info in the link in my signature. And some work arounds for HP, Sony and others that only let you boot Windows from UEFI.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

@andre27
You have a standard BIOS install using MBR(msdos) partitioning and that has a 4 primary partition limit. You have to delete one primary partition to convert it to an extended partition and then can have an unlimited number of logical partitions inside it.

Most seem to backup HP tools, but some have said you can also download that again if needed. It is a small partition, but not large enough, so you still have to shrink your Windows main install and reboot to run chkdsk in Windows. Then I think the auto install should work since Windows 7 and BIOS/MBR. Just make sure it is not hibernated or needing chkdsk.

       
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

I believe this was Vista but the same issues apply to all newer Windows.
 [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

