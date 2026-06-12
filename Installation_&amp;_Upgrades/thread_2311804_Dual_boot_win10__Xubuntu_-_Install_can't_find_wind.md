---
title: "Dual boot win10 / Xubuntu - Install can't find windows"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by guillaume16 on 2016-01-30
Hi,

Trying to install from a usb key. I tried a boot-repair, but it didn't work. I got this url: [http://paste.ubuntu.com/14728885/](http://paste.ubuntu.com/14728885/)

I have windows on the first HDD, where i shrinked its partition to get room for xubuntu.

I have a software raid 1 a set of two 400GB hdd with data on it (backed up), I'll have to rebuild that later.

I've run chkdsk under windows to see if it helped, but not.

Any suggestion?

---

### Post by ajgreeny on 2016-01-30
I don't think the ubuntu desktop installer will work on a software raid system, though my knowledge of any raid setup is lower than zero.

I think you may have to investigate raid problems in installation further, so have a look at [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID).

---

### Post by guillaume16 on 2016-01-30
Hi,

I am not planning to install xubuntu on the raid, it's just for my personal files. Windows is on a "simple" drive, and I want to install xubuntu there too. The raid drives are just extra storage.

---

### Post by yancek on 2016-01-30
I'm not sure what you did or what exactly the problem is as there is no sign whatsoever of any Linux partitions on the drive (sda) on which you have windows installed.  Not sure why you have syslinux in the MBR of that drive which only has windows on it.  Did the boot repair do that.  You seem to have unallocated space on sda.  What exactly happens when you boot Xubuntu and start the install?

---

### Post by guillaume16 on 2016-01-30
Hi!

I freed 25 Gb on sda to install xubuntu, but didn't format it, I wanted to do that under xubuntu install. When I start the xubuntu install, everything seems find except that I don't get the choice to install aside windows because it doesn't detect it.

I guess boot repair did that...

---

### Post by oldfred on 2016-01-30
Syslinux is the standard Windows type boot loader that Boot-Repair installs when it only sees Windows or you want a Windows type boot loader.

Part of issue is either SFS or RAID or both.
I did not think SFS was related to RAID nor RAID related to SFS.
I think the partitioning tool is hanging at trying to see the SFS drives. You can either remove the SFS (recommended) or just disconnect those drives.


SFS is Windows dynamic partitions somewhat like LVM in Linux. It is a logical partitioning system to allow more than 4 partitions with the old MBR(msdos) partitioning. It is proprietary to Microsoft and does not work with Linux nor some Windows tools.

       Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

Also if Windows 10 make sure the fast start up or always on hibernation is off. Installer cannot see NTFS if hibernated or needs chkdsk after a resize.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by guillaume16 on 2016-01-30
Hi Oldfred,

I tried first with deactivating the fast Startup, which was on. Was not enough, so I went for disconnecting phisicaly the two drives of the raid, that didn't do the trick either. Should I try to remove the SFS? I'm not quite sure how I do that, does that mean saying to windows to unbuild the raid? Maybe it's no longer necessary to try as I have tried with disconnecting the drives.

So now I only have the SSD drive with windows on it, as both raid drives are now out of the picture, but still no windows partition detected by the xubuntu installer.

By the way, I have bios, not UEFI.

Thanks for helping!

---

### Post by guillaume16 on 2016-01-30
If this may help, I've attached some print screens.

[ATTACH=CONFIG]267033[/ATTACH][ATTACH=CONFIG]267032[/ATTACH]

---

### Post by oldfred on 2016-01-30
Was drive ever part of RAID? 
Or perhaps just having RAID turned on added RAID meta-data.

I would try this, just on your install drive. I believe turning on RAID would restore this even if you run on wrong drive.

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda

---

### Post by guillaume16 on 2016-01-30
No this drive has never been part of any raid. I'll have a look at the link tomorrow,   thanks!

---

### Post by guillaume16 on 2016-01-31
Ok so the drives are set up as IDE,  ahci prevents win 10 from starting, reporting a boot failure. Dmraid reported no raid to be erased. Os-prober finds the windows recovery environment, but the install finds no os.

---

### Post by oldfred on 2016-01-31
My old XP would not run with AHCI on, and I had to turn it on to have trim work when I got a SSD, so I turned it on.
But it was my understanding that all versions of Windows after XP have AHCI drivers or perhaps Vista needed them installed. But I would think since AHCI has been standard for years all the newer Windows would not have an issue. 
Someone that knows Windows may be able to help.
 [http://www.tenforums.com/](http://www.tenforums.com/)

Have you tried chkdsk on your NTFS partition(s). You need the Windows repair console from either the installer or a repairCD or flash drive that you make from your install when it is working.

---

### Post by guillaume16 on 2016-02-01
So I followed this  [http://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html](http://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html),  and now ahci is on and win10 starts as usual. But still no win10 in the  install menu.

I created a recovery usb drive and ran chkdsk at startup. Still no luck :(

---

### Post by oldfred on 2016-02-01
Then have you turned off the always on hibernation or fast start in Windows?

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by guillaume16 on 2016-02-01
Yes, hibernation is off.

[http://paste.ubuntu.com/14850534/](http://paste.ubuntu.com/14850534/)

---

### Post by oldfred on 2016-02-01
I would use Windows own disk management to shrink the main NTFS partition and reboot so it can run chkdsk.
Partitions are shown ok in Boot-Repair's scripts, so not sure why then installer would not show them.

If not you always should be able to partition in advance with gparted to make / (root) & swap partitions. Plus that gives you more control over sizes & other options.
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


But you have to then use Something Else to select (change button) which partition is /. If swap exists it has already found it and used it to speed up install somewhat and will auto add it.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by guillaume16 on 2016-02-01
Is this a way to manually configure the bootloader to dual?  Kind of overriding the installer?

---

### Post by oldfred on 2016-02-01
Something Else is just a manual version of the installer. I do not like auto installs as they choose what sizes to make everything which usually is not best.

Only real difference is create or selecting previously created partition(s) for / and possibly /home. If in advance you get swap.

And you get the option on where to install grub2's boot loader, default is sda, like the auto installers only option. But most installs want sda anyway, only if installing to sdb or any other drive may you want to change boot loader default.

---

### Post by guillaume16 on 2016-02-03
Yes! at last.

The thing I really misunderstood at the very beginning is that you don't need the installer to detect the other os to make the bootloader work. I just followed the instructions of partitionning and so on, and everything worked by itself.

I did modified the name for windows in the grub, so that it says windows 10.

I don't know if not fixing the hibernation and the AHCI mode would have been a problem, but my raid drives were connected under installation.

For the record, I went for Mint, not xubuntu.

Now I will probably come back around here for some other issues about raid, wine and so on... :)

Thanks for helping!

---

