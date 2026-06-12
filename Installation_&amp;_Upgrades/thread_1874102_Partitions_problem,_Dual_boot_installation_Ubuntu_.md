---
title: "Partitions problem, Dual boot installation Ubuntu 11.10 and wWindows 7"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by azkraja on 2011-11-02
Please help me, I was trying dual boot installation with windows 7 after testing 11.10 through wubie. i am explaining my drive set up as its shown in windows 7 disk management option window.

Partition 1 : 900 MB Windows boot system
Partition 2 : 70 GB Windows OS (Drive C)
Partition 3 : 200 GB (Drive D)
4-Unallocated space: 30 GB which I have created by shrinking Drive **D** (Partition 3)in windows disk management option (This was suppose to be used for Ubuntu 11.10 as i plained) 

Now when I attempt to install Ubuntu 11.10 via live CD, (after marked some thing else option) disk showing as follows

sda1: 900 MB-unknown
sda2:70 GB-Windows 7
sda3: 230 GB (Showing total capacity in one -unallocated space and drive D)
sda4: unallocated space 1 MB 

When I reboot and checked again in windows disk management option it was the same as I mentioned above.
Unallocated space 1 MB and 1GB sda 2 which is shown by Ubuntu live CD is not shown by windows.
How can I make this possible to install Ubuntu 11.10 without disturbing my valuable data as I do not have any external hard drive to back up whole data.

Following machine I am using.

HP laptop G62 series
Core i3 2.4GH
HD 320 GB
RAM 2 GB

---

### Post by Mark Phelps on 2011-11-02
First things first, if you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

Now that you have a Repair CD, you need to confirm that the final partition is not actually INSIDE an extended partition -- which would explain why there is no actual free space seen by the installer.

To do that, boot from the Ubuntu desktop CD, choose Try Ubuntu when the screen comes up. When you get to a desktop, use Dash to search for Disk Utility and click that.  When that opens, look at the partition arrangement on your PC.

IF it shows the last 30GB as actually unallocated, then it's a mystery why the installer doesn't see that.

---

### Post by oldfred on 2011-11-02
It is always best to have backups. There are no guarantees that a hard drive will not fail, software may not do what you expect or a user makes an error and erases something.  I consider myself pretty knowledgeable and have had all those occur to me.

Post screen shot from Gparted and a copy of this from the terminal.

sudo fdisk -lu

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by azkraja on 2011-11-03
Thanks for reply, this is also a mystery for me, even i have checked with GPARTED live CD, but it not showed the unallocated space which I have created (shrunk by built in Windows 7 option).
When i reboot and checked again in Windows 7, it was there. even I have tested another way, format Fat 32 file system, but could not succeed to locate by Parted or Ubuntu live CD disk utilities. Now i have started to read above given links of threads of Oldfred and some articles on Google regarding this problem. After one more attempt I will let you know.
Thanks

---

### Post by darkod on 2011-11-03
Are the partitions exactly as you said, 4 primary partitions? Or we are talking about logical partition inside extended?

In that case you can shrink the logical partition, but the extended is still the same size.

It's best if you can boot in live mode and post a screenshot of Gparted, much easier to understand what is going on. In live mode you should have internet so you can literally make the screenshot and post it here.

---

### Post by oldfred on 2011-11-03
I also have had gparted not show my sda drive when my XP install needed chkdsk. After I ran chkdsk then it worked and my XP booted faster.

@Darko
Have not seen you for a while. Hope things are well. Good you are back.

---

### Post by azkraja on 2011-11-03
> **darkod said:**
> Are the partitions exactly as you said, 4 primary partitions? Or we are talking about logical partition inside extended?

In that case you can shrink the logical partition, but the extended is still the same size.

It's best if you can boot in live mode and post a screenshot of Gparted, much easier to understand what is going on. In live mode you should have internet so you can literally make the screenshot and post it here.

I will post the screen shots soon, as currently I am in office with busy work.

---

### Post by darkod on 2011-11-03
> **oldfred said:**
> 
@Darko
Have not seen you for a while. Hope things are well. Good you are back.

Thanks. Too much time at work and too little spare for myself...(and the forum) :)

---

### Post by azkraja on 2011-11-04
> **azkraja said:**
> I will post the screen shots soon, as currently I am in office with busy work.

Here I am attaching 2 Screen Shorts, Windows 7 Disk Management, Ubuntu Disk Utility.

---

### Post by azkraja on 2011-11-04
Here is the screen short of G Parted.

---

### Post by darkod on 2011-11-04
There's your problem. Windows screenshot. Look under Disk 0 where it says Dynamic.

I have no experience with dynamic disks, maybe someone else will jump in, but from what I have figured out, ubuntu can not recognize properly dynamic disks. Only Basic.

Dynamic disk is where you can resize partition without deleting and formatting which is nice, but only windows can understand it.
Linux has a similar feature with LVM, but again, windows can't see LVM or any other type of linux partitions (not by default).

I don't think so you can install on dynamic disk, and I don't think you can convert it to basic without having to move the data, convert the disk (delete all), again create partitions and move the data back. This includes moving the windows OS (either clone or reinstall).

---

### Post by darkod on 2011-11-04
> **azkraja said:**
> Here is the screen short of G Parted.

Look how all partitions have red exclamation marks. Move the cursor there and it will say something, what it finds.

---

### Post by azkraja on 2011-11-04
I have moved the cursor on them, not shown up any thing, even I have extended that partition again using windows disk Management and re-boot with Ubuntu live CD, open GParted to re-size big Partition D and even tried Windows Partition C as well, but Re-size option is totally Dull, cant do anything, May be i have to Borrow some portable hard drive to shift all data first for re-partitioning. it will take time and i can do it only when i will got a couple of leaves from my Office.
I was using Ubuntu since version 10.10, and installed many times through Wubi, but it was not stable, as whenever i have defrag the windows partition, off and on i faced the problem to re-boot Ubuntu, than i have to UN-install Ubuntu. I want to use this OS at my home, till i will learn it completely. 
I salute Ubuntu Forum to get support on time, and many thanks for your valuable advise, i will continue to visit my thread if some solution comes up in existing scenario without shifting my data, i will go for it, otherwise i have to do it another way. But one thing is sure, my future OS will be Ubuntu. Have a great time.

---

### Post by oldfred on 2011-11-04
Converting is high risk. Windows offical policy is to backup, delete everything repartition to basic, reinstall and restore data.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by azkraja on 2011-11-05
[I]_______________________________________________________________________
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)[/I] [I]
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)[/I] 
________________________________________________________________________
I have downloaded MiniTool Partition Wizard, but i will do this when i have something like Portable hard drive to back up my valuable data. for the time being i have reinstalled Ubuntu 11.10 through Wubi, after update several my favorits, now i am facing following problem. 
Software center refuse to install updates. I am attaching screen short of this error, please guide me what i have done wrong, and how i can fix this problem, i have installed following.
Ubuntu Ristricted Extras, 
Gnome Shell 
VLC
SM Player,
Cairo Dock
Advance settings
and some few others accessories like gnome tweak tools
Screen Short.

---

### Post by oldfred on 2011-11-05
So you have wubi working in the dynamic partition? I thought that did not work either.

You new questions are a whole different topic, best to start a new thread with appropriate title so those who know wubi & medibutu can comment.

I used to install medibutu, but since Ubuntu added the restricted extras, I am not sure it is needed.

---

### Post by azkraja on 2011-11-05
Thanks, Wubi was giving problem in my last installation, but whenever ubuntu was refuse to boot, i have run Check Disk from windows utility to fix file errors, and its work for me, i have found these information in Wubi Manual. 
Thanks for your valuable advise,  I will go for separat installation after purchasing my Portable hard drive, till i will bear with Wubi. (Starting new thread regarding software center error)

---

