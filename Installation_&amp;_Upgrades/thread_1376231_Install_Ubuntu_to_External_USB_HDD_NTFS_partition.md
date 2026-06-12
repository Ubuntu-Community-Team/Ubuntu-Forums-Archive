---
title: "Install Ubuntu to External USB HDD NTFS partition"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by vwchest on 2010-01-08
I am currently downloading Ubuntu from a torrent at:
[http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)
The file will be Ubuntu-9.10-alternate-i386.iso at 689Mb. I have a dial-up connection so the download is taking a long time to complete. I understand this to be a disk image file.

I am using Windows XP v5.1 (Build 2600.xpsp_sp3_gdr.090804-1435 : Service Pack 3) as the operating system on my Emachine. This computer supports booting from a USB drive in the BIOS. I also have a DVD/CD +R+W drive to burn a disk image to if needed.

In short I want to install Ubuntu on a bootable partition of a NTFS external USB hard drive.
The external hard drive is a Western Digital 320Gb USB 2.0 that came formatted as NTFS.
I plan to use "EASEUS Partition Master 4.1.1 Home Edition" to create a ~40Gb NTFS partition on this drive for the Ubuntu install and any future Linux applications that I will acquire. The larger partition will be used for Windows backup storage and as a portable drive with a number of portable windows applications.
1) Should I use another file system other than NTFS? FAT? FAT32? Something Linux?
2) What steps are required to install Ubuntu on the partition?

In addition I would like to try to run Ubuntu inside a "shell" inside Windows XP from time to time. I have software (VMware player v3.0.0-197124) that I think can accomplish this.

I have the following security and utility programs running:
WinPatrol (real-time)
SpyWare Terminator (scheduled scans)
WinMem Optimizer (real-time)
ThreatFire (real-time)
PC Tools FireWall Plus (real-time)
Avast Antivirus (real-time)
3) Are any of these programs known to interfere with the installation of Ubuntu or with Ubuntu running in a shell?

Thanks in advance for your help.

---

### Post by presence1960 on 2010-01-08
For the external disk I suggest using [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to partition the disk. Make the filesystem either ext3 or ext4. Ext4 is newer but faster. I would also make a swap partition equal to the amount of RAM you have if you intend on using suspend/hibernate functions. That will be linux-swap filesystem not ext3 or ext4.

Then install using the Live CD. Choose the manual option to install. Highlight the ext3 or ext4 partition you created and click "change". Tick the format box and at mount point use the drop down box to select "/". Nothing need be done for swap. 

**_Note the designation of your ext3 or ext4 partition, i.e. sdb2_** as you will need this info when installing GRUB.

When you get to the Ready to install window pictured below click the advanced button. You are going to select where to install GRUB. You want to put it on MBR of the external disk. So if ubuntu was installed to sdb2 you want to select /dev/sdb.

This will allow you to boot with or without the external disk plugged in. With the external plugged in GRUB will take over and you can boot Ubuntu or windows, if the external is unplugged you boot right into windows.

**_Just make sure you go into BIOS and set the external to boot before hard disk in the device boot order!_**

---

### Post by Bartender on 2010-01-09
torrent and dial-up?  I didn't know you could do that!

Who's your ISP?  I'm curious to know what dial-up provider will let you stay on for that long.

---

### Post by darkod on 2010-01-09
Is there any reason you are downloading the alternate image and not the standard desktop image? The alternate will not give you GUI installer.
Do not create any partitions for ubuntu as ntfs, it doesn't work on ntfs anyway. Depending what the current situation on your ext hdd is, if you have the 40GB as free unallocated space, I wouldn't create even ext4 partition from it. Just install ubuntu into that unallocated space during the install process.
Creating the partitions in advance makes it necessary to remount the partitions during install. If you haven't done it before you'll find it weird.
It's not as simple as pointing the windows installer to an existing ntfs partition.

---

### Post by presence1960 on 2010-01-09
> **darkod said:**
> Is there any reason you are downloading the alternate image and not the standard desktop image? The alternate will not give you GUI installer.
[B][U]Do not create any partitions for ubuntu as ntfs, it doesn't work on ntfs anyway. Depending what the current situation on your ext hdd is, if you have the 40GB as free unallocated space, I wouldn't create even ext4 partition from it. Just install ubuntu into that unallocated space during the install process.
Creating the partitions in advance makes it necessary to remount the partitions during install. If you haven't done it before you'll find it weird.
It's not as simple as pointing the windows installer to an existing ntfs partition.[/U][/B]
That method works also. It is a matter of personal preference which method you like or choose to use. But that is the beauty of linux- there are usually multiple methods to accomplish any task.

At least you learned two ways to do an Ubuntu install today! If you are shaky with partitioning basics and installations I would use Darko's way.

---

### Post by vwchest on 2010-01-09
> **Bartender said:**
> torrent and dial-up?  I didn't know you could do that!

Who's your ISP?  I'm curious to know what dial-up provider will let you stay on for that long.

TDS based in Madison, WI but has offices in several states including Virginia. I live in Hot Springs, VA, which is very rural location. As a guess TDS came here at the request of a resort hotel located here. So multi-state internet provider plus few subscribers equals connection time not too significant for bandwidth usage. I dont know really, you can do the math.

---

### Post by vwchest on 2010-01-09
> **darkod said:**
> Is there any reason you are downloading the alternate image and not the standard desktop image? The alternate will not give you GUI installer.
Do not create any partitions for ubuntu as ntfs, it doesn't work on ntfs anyway. Depending what the current situation on your ext hdd is, if you have the 40GB as free unallocated space, I wouldn't create even ext4 partition from it. Just install ubuntu into that unallocated space during the install process.
Creating the partitions in advance makes it necessary to remount the partitions during install. If you haven't done it before you'll find it weird.
It's not as simple as pointing the windows installer to an existing ntfs partition.

First of all I am novice squared when it comes to Linux in any flavor, but really would like to migrate over. I downloaded Ubuntu from links on this web page:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)
As males often do, I didn't read all the instructions and picked the first "i386" torrent in the Ubuntu 9.10 list. Only thing on my mind was this file will take freaking forever to download and lets get it started. By the way using uTorrent 1.8.5 it took 1 day and 22 hours to complete on my humble dialup!
Ok so I dont want to create any partition but need to have unallocated space. 
1) Do I use my disk partition software (Easeus) to unallocate this space? Here are my hard drive usage statistics:
Used space: 41.0 GB (Windows backups and Portable USB applications)
Free space: 257 GB
All of this being in NTFS format.

I can download Gparted Live from:
[http://cdnetworks-us-1.dl.sourceforge.net/project/gparted/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso](http://cdnetworks-us-1.dl.sourceforge.net/project/gparted/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso)
I realize this is an older version but the warnings on [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) suggested using it instead. I am reluctant to download it because this file is 100Mb in size and it'll take a long time too.

2) Is 40Gb ample to comfortably house Ubuntu and a healthy number of future Linux applications?

Thanks once again.

---

### Post by darkod on 2010-01-09
Uhhhh. If you already don't have unallocated space (not belonging to a partition), it gets slightly more complicated.
If you had the desktop image, Gparted is in it, so you could use it without any further download. But you don't have the desktop image as far as I understood. :(
In this case it's probably best to use Easeus to make a 40GB unallocated space, yes.
And yes, 40GB is enough for running ubuntu with installed software on it.
Once you make the space unallocated the ubuntu installer should be able to use and set itself up in it. I haven't personally tried the alternate installer, so this is slight assumption, I haven't seen how the installer steps/screens go.

---

### Post by vwchest on 2010-01-09
> **darkod said:**
> Uhhhh. If you already don't have unallocated space (not belonging to a partition), it gets slightly more complicated.
If you had the desktop image, Gparted is in it, so you could use it without any further download. But you don't have the desktop image as far as I understood. :(
In this case it's probably best to use Easeus to make a 40GB unallocated space, yes.
And yes, 40GB is enough for running ubuntu with installed software on it.
Once you make the space unallocated the ubuntu installer should be able to use and set itself up in it. I haven't personally tried the alternate installer, so this is slight assumption, I haven't seen how the installer steps/screens go.

I am poised to take action. Here's what I have in hand:
1) A CD that was burned with the Ubuntu 9.10 alternate image[INDENT]E:\>dir
 Volume in drive E is Ubuntu 9.10 i386
 Volume Serial Number is B0E3-DDD1

 Directory of E:\

10/27/2009  12:18 PM    <DIR>          .disk
10/27/2009  12:18 PM               222 README.diskdefines
10/23/2009  11:21 AM             1,020 cdromupgrade
10/27/2009  12:18 PM    <DIR>          dists
10/27/2009  12:18 PM    <DIR>          doc
10/27/2009  12:19 PM    <DIR>          install
10/27/2009  12:19 PM    <DIR>          isolinux
10/27/2009  12:19 PM           160,907 md5sum.txt
10/27/2009  12:18 PM    <DIR>          pics
10/27/2009  12:18 PM    <DIR>          pool
10/27/2009  12:18 PM    <DIR>          preseed
10/27/2009  12:19 PM                 0 ubuntu
               4 File(s)        162,149 bytes
               8 Dir(s)               0 bytes free
[/INDENT]2) External HDD with 40Gb unallocated and unformatted space. I have a screen shot attached as JPEG image.

Easeus gave me the option of creating a partition that would assign a drive letter (something the system would now recognize) but have no file system (unformatted). Does the Ubuntu installer recognize unallocated space regardless? The reason I'm concerned is that Easeus also created another unallocated space of 94.13Mb (remainder of drive partition math???) and I'm afraid Ubuntu might pick the smaller over the larger unallocated space to install to OR consider both unallocated spaces as one and do some kind of illegal combining or cross writing.

With the above concern settled, what are the steps to install?
1) Reboot, pick boot from USB in BIOS and then follow an autorun installer program? I have dumped the CD's directory list (above).

One more concern is that while doing internet research in general I came across a site that suggested disconnecting the SATA cable from the Windows HDD (drive C and D for mine) during install to eliminate Linux "where to install" confusion. Do you think this is necessary for an Ubuntu installation? Sorry for so many questions but I'm just doing my homework.

Thanks again.

---

### Post by darkod on 2010-01-09
Ubuntu will not mind the smaller partition, it goes for the largest space anyway. But something else is bothering me. As you can see in the screenshot, and as you wrote, you actually created a partition (extended, also called logical). Yes, the space inside the extended is unallocated, but the existance of the partition itself might make ubuntu ignore it.
The space needs to be unallocated as in not belonging to any partition at all. Try deleting the 40GB logical partition and leave it just like that.

Reboot but select the CD to boot from, not USB. You said you burned the image to a cd so you need to boot from it.
Unfortunately, as I said, I haven't used the alternate installer so far but I'm pretty sure it will recognize the 40GB unallocated unpartitioned space and offer a guided install in it. Which means it will create the standard root and swap partitions. You should have no problems installing it.

I wouldn't disconnect the int hdd. Just be careful when selecting where and how to install ubuntu and you'll be fine. The thing is, grub (the bootloader) will set itself to boot ubuntu and any other OS it finds. With the int hdd disconnected, it will not see windows to add it to the list.
Even worse, it will not know there is another drive and will consider the ext hdd as drive1 (hd0). When you connect the int hdd back, it automatically becomes hd0 before the ext hdd which is now hd1. And before you know, thinking you did evrything right, grub will look for ubuntu on hd0, in fact your windows disk.
IMHO, the time to disconnect drives is when troubleshooting. If all your hardware is working fine connected, use it like that.

---

### Post by vwchest on 2010-01-10
> **darkod said:**
> Ubuntu will not mind the smaller partition, it goes for the largest space anyway. But something else is bothering me. As you can see in the screenshot, and as you wrote, you actually created a partition (extended, also called logical). Yes, the space inside the extended is unallocated, but the existance of the partition itself might make ubuntu ignore it.
The space needs to be unallocated as in not belonging to any partition at all. Try deleting the 40GB logical partition and leave it just like that.

Reboot but select the CD to boot from, not USB. You said you burned the image to a cd so you need to boot from it.............

After hours of tinkering here are my results:
1) Easeus doesnt offer an unassociated unallocated space. Unallocated space always becomes a logical extension. So I first tried to install Ubuntu to this space and amazingly the installation completed without any errors (including writing to the MBR for OS boot choice). However after reboot (both with removable drive and then hard drive as first choice in BIOS) there was no offer of boot choice, just went right into Windows without incident.
2) I tried making this unallocated space drive U first as unformatted and then drive U as NTFS in Easeus. Tried giving Ubuntu install ownership of drive U's, and thirdly ownership of the entire USB drive. In every case it would create the ext4 and swapfile (as new unallocated space), complete installation without error, but never became a bootable option.
3) After any install of Ubuntu, Easeus would show a designated space for both the ext4 and swapfile with correct disk sizes. It would recognize the file systems as 'other' (as opposed to FAT,FAT32,NTFS,Unformatted, or Unallocated). There wasn't any drive letters assigned and Windows didn't recognize them as drives in Explorer.

I am currently downloading Gparted v0.4.6 which at the time of this writing will be 4h45m to complete. I hope this can remedy something. Am I on the right course at this point?

Thanks again

---

### Post by vwchest on 2010-01-10
> **darkod said:**
> Ubuntu will not mind the smaller partition, it goes for the largest space anyway. But something else is bothering me. As you can see in the screenshot, and as you wrote, you actually created a partition (extended, also called logical). Yes, the space inside the extended is unallocated, but the existance of the partition itself might make ubuntu ignore it.
The space needs to be unallocated as in not belonging to any partition at all. Try deleting the 40GB logical partition and leave it just like that.

Reboot but select the CD to boot from, not USB. You said you burned the image to a cd so you need to boot from it.......................

I was able to install Ubuntu as a guest operating system using VMWare. However I can't seem to get out of the 'command-line' mode to the Desktop GUI. Is it just that I don't know the command or am I back to I should have downloaded the 'desktop' ISO as opposed to the 'alternate' ISO. This is frustrating, its like smelling the meal, feeling the hunger, seeing the plate, but can't get to the table!

Thanks

---

### Post by darkod on 2010-01-10
Not sure if the alternate installer installs desktop gui by default. Once you load the text mode command line, try:
sudo apt-get install ubuntu-desktop

Provided internet is working, it should install the gnome desktop.

---

### Post by Bartender on 2010-01-10
The alternate installer should give you the standard Ubuntu desktop.  There really shouldn't be any difference at all in the end result, it's just that the alt-install CD gets you there with less bell and whistles than the LiveCD

---

### Post by vwchest on 2010-01-10
> **Bartender said:**
> The alternate installer should give you the standard Ubuntu desktop.  There really shouldn't be any difference at all in the end result, it's just that the alt-install CD gets you there with less bell and whistles than the LiveCD

I have internet access through VMWare+Ubuntu and the installation process is working but........
As you can see it wants to download 342Mb of archives. Do you know the command to either exit the text commands and run Gnome Desktop or use a text command to edit some boot file to execute Gnome on boot? If so how do I abort the download and if I abort, does it corrupt the existing Gnome by incomplete installation? I have suspended the Ubuntu virtual machine at this time.

P.S. I am currently downloading Gparted to go back and ultimately attempt to do a proper Ubuntu installation'

Thanks

---

### Post by vwchest on 2010-01-11
> **Bartender said:**
> The alternate installer should give you the standard Ubuntu desktop.  There really shouldn't be any difference at all in the end result, it's just that the alt-install CD gets you there with less bell and whistles than the LiveCD

1) Couldn't abort the app install download, so I suspended the virtual machine and deleted it (no problem).
2) Downloaded the Gparted ISO, burned CD, booted the CD and #$@% wouldn't load the OS to run it. Tried install to RAM, normal, failsafe, etc.
3) Found another partitioner, [http://partedmagic.com/download.html](http://partedmagic.com/download.html), downloaded it (has Gparted as a component). Burned CD and booted it to RAM. Voila! A beautiful fully operational Linux with Desktop in RAM none-the-less. Ran the partitioner and created 35Gb ext4 for Ubuntu, 5Gb ext4 for Home directories, and 5Gb swap area. Ubuntu installation jumped right in and filled each one without complaint and wrote to MBR for OS choices (recognized Win XP as an OS). Started a series of reboots poking through first boot options in BIOS (HDD, removable, etc). Never had an acknowledgment of Ubuntu as a boot choice. I followed these instructions, [http://partedmagic.com/documentation/119-using-gparted.html](http://partedmagic.com/documentation/119-using-gparted.html), on the first round of partitioning. On the second round, I made the 35Gb Ubuntu a primary drive with boot flag on and the other two drives as logical to it (same results). I'm now suspecting some kind of MBR protection from the BIOS, anti-virus software. the xHDD, or Emachines/Win XP 'proprietarinism'. In any case. PLAN B.

My ultimate goal for the 320Gb xHDD was to have a bootable portable OS (Ubuntu Linux), a backup drive for my Windows XP data, and as a pseudo-flash drive with a host of portable Windows applications. Take this puppy anywhere, share files, boot Ubuntu anywhere, and run my favorite portable apps anywhere in there pseudo-sandbox. By the way, I'm a big fan of TOR, the onion router, and anonymous browsing when at work (oops) or on the road.

Here are my plans for now:
1) Go the VMware virtual machine route. It will work and is able to share all hardware and internet connection as is. I have a Knoppix v6.0.1 Adriane virtual machine that is working. I lose portability (unless VMware gets installed all over the world) but still get to explore and benefit from Ubuntu and Linux applications.
2) Download the Ubuntu Desktop ISO. But work on the Alternate ISO text command problem in the mean time.

Thank you for your time and patience. I am taking up too much forum realstate. But if I solve this problem I will return and spell out the solution for any future readers.

---

### Post by vwchest on 2010-01-13
> **vwchest said:**
> 
Thank you for your time and patience. I am taking up too much forum realstate. But if I solve this problem I will return and spell out the solution for any future readers.

I completed the download of Ubuntu v9.10 Desktop ISO. It installed on a virtual machine using VMWare without any problems. I have setup Firefox with Xmarks and have complete bookmark sharing with Win XP Firefox and Cometbird. I was able to setup Evolution email with my Gmail account- no problems. Ubuntu as an OS seems to be working just fine as a VM.

I will venture a guess that the 'Easy Install' feature of VMWare of Ubuntu Alternate ISO assumed that it was a shell-only installation as opposed to a GUI one. Your guess??

As far as a complete installation of Ubuntu Desktop on a real HDD goes, I think I will use another external 40Gb that I have. I plan to reformat and partition this HDD completely dedicated to the ext4 file system and a swap file. I will make it primary with bootable flag on. I will research the potential MBR write protection and try to disable it for the Ubuntu install, as stated before I suspect the BIOS or my anti-virus software.

As before, I will return and spell out the success of the real HDD install when and if I can get it done.

---

### Post by inspectorweb on 2010-05-11
I recommend [AnVir Task Manager](http://www.anvir.com/) or its [free version](http://www.anvir.com/taskmanagerfree). It shows everything running on a computer. I've been using it for about 4 or 5 years on a couple of pc's, and never get any problems with viruses or slow PC.

---

### Post by inspectorweb on 2010-05-11
I recommend [AnVir Task Manager](http://www.anvir.com/) or its [free version](http://www.anvir.com/taskmanagerfree). It shows everything running on a computer. I've been using it for about 4 or 5 years on a couple of pc's, and never get any problems with viruses or slow PC.

---

