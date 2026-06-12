---
title: "error: unknown filesystem= unbootable computer"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by Photobug on 2013-12-17
I am trying to create a dual boot system with Ubuntu 12.04 and windows 7.

After creating a fresh install on W7 I created a 10GB free space to work with Ubuntu.  I used Ubuntu to split off a a 1GB swap partition then created a 9GB ext4 patition and installed Ubuntu on it.  On restart I had an option to open up Ubuntu or W7 or memtest or Ubuntu trouble shoot OSs.

On startu of Ubuntu I could not get it to run.  I got one purple Ubuntu screen for a minute or so then a error noise followed by a black screen.  I opened up a Ubuntu trouble shooting OS but did not know my way around it so closed it and booted from a thumb drive into a live Ubuntu.  In there I have tried to reinstall and have had no luck. 

Now i cant even get into Windows.  When i try to start the computer, I get an 
Error: unknown filesystem
grub rescue>

What should I try?

---

### Post by Photobug on 2013-12-17
At this point I am locked out of using my hard drive at all.  When I try to log on to the computer I get a [SIZE=4]grub rescue>[/SIZE] screen.

I would like to now just get rid of the Ubuntu install so I can get back to the Windows 7 and make a copy of that install, before I try again.  I did not back that install up since i figured I was adding the Ubuntu system to a second partition.  I was assuming that OS would be safe, not the case.

I have gone into the Ubuntu setup and choosen "do something else" in install.  I tried to use the formatting tool to delete the Swap and install partitions to remove the Ubuntu portions to get rid of the [SIZE=4]grub rescue>[/SIZE] screen and get back to Windows 7 with no luck.  I am pretty sure I was able to get rid of the partitions so that area of the disk was unassigned yet I still got the [SIZE=4]grub rescue>[/SIZE] error on computer start.  I have read up on GParted and know how to use it.  If i deleted those two partitions in GParted would I be able to get back past the grub rescue screen?

---

### Post by CitadelUniversal on 2013-12-17
Please have a look at the ubuntu wiki here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) - it explains a bit about dual-booting windows & ubuntu together..

---

### Post by Photobug on 2013-12-17
> **CitadelUniversal said:**
> Please have a look at the ubuntu wiki here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) - it explains a bit about dual-booting windows & ubuntu together..

Thanks good info for future trys at getting this right.  Even though I used another source for my techniques i think I did the installation correctly originally.  When it did not work correctly I then started making a mess of it.  In order to get back to my original W7 only install I tried to delete the partitions that held the swap and Ubuntu Root.  Since then I have been getting the grub error on start up.


I am now trying to manually format my extensions and re install Ubuntu on the partitions.  However I am getting an error on the install attempt shown below.  I have tried a few times to install on an ext4 but tried ext 3 this time, because I have seen it used in some examples and wanted to try something different than what had failed on previous attempts.[ATTACH=CONFIG]248668[/ATTACH]

From the  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) I am looking at optiond to try to fix the Grub 2 installer.  I want to believe the Ubuntu system I installed is non existent since I used the format tools in the installation to delete and reformatt those partitions.  Yet I get the grub error when trying to start from my hard drive and I get the error when trying to install a new Linux on these partitions.  
[ATTACH=CONFIG]248670[/ATTACH]
Here is a look at the command line I ran to examine the status of the hard drives.   It is showing a linux and swap drives installed even though I got the error pictured above during my last attempt to install.  If there is Ubuntu installed on that computer it will be on sda6.

Should i try to update the grub2 install using these techniques?
[ATTACH=CONFIG]248669[/ATTACH]

---

### Post by Photobug on 2013-12-17
My windows 7 is located on the sda2 partition.  Would running this command

sudo mount /dev/sda2 /mnt

Cause my computert to boot up in Windows 7 on startup?

---

### Post by oldfred on 2013-12-17
This can reinstall grub or install a Windows type boot loader to boot Windows.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Better to use ext4. Your 10GB is not very large but should work. My working install uses about 10GB, but I have all data on other partitions.

After you install once, you need to use manual install or Something else. Then you can choose the already created partition to reuse, reformat it. But you have to specify mount like /, format like ext4.

---

### Post by Photobug on 2013-12-17
> **oldfred said:**
> 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


Here is a copy of my boot repair report.

[FONT=Garamond][SIZE=3]http://paste.ubuntu.com/6589848/[/SIZE][/FONT]


> **oldfred said:**
> s.
Better to use ext4. Your 10GB is not very large but should work. My  working install uses about 10GB, but I have all data on other  partitions.

After you install once, you need to use manual install or Something  else. Then you can choose the already created partition to reuse,  reformat it. But you have to specify mount like /, format like  ext4.

I have been using Something else from the begining to create partitions and install.  I also have been using ext4, but only tried ext3 the last time after having 5 other efforts fail with ext4.  After some reading while trying to solve my current issues, I realized the sizes of partions are not adequate and plan on upgrading the size of the my partitions.  Maybe 2GB for swap 8 for the install and creating another partition for home of maybe 20 GB.  Once i get past this current hurdle I will looking for suggestions on how to format my partitions for initial configuration of Ubuntu.

---

### Post by oldfred on 2013-12-17
Boot-Repair had all sorts of issues mounting your NTFS partitions. Did you leave Windows hibernated? Or did you resize using the installer, not using Windows own disk tools to shrink the Windows main partition?
Both hibernation and resize set flags that then the Linux NTFS driver will not normally mount the NTFS partition. 
Do not use hibernation if dual booting and run chkdsk from Windows. If Windows does not boot then you need your Windows repairCD or flash drive. Some third party Windows repair tools may run a chkdsk also.

Because Boot-Repair could not see the NTFS Windows partitions to know if they had boot files, it did not offer to install a Windows boot loader. Not sure if installing a Windows boot loader would then let you use f8 and get into a recovery console or not.

This is just to put a Windows type boot loader into the MBR, you then will not have grub to boot Ubuntu and would have to run Boot-Repair to restore grub. But grub will only boot a working Windows so you do need to fix that first.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

If you did this before installing Ubuntu good for you. Otherwise you need another computer, or a friend, co-worker etc with the same 32 bit or 64 bit version.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Photobug on 2013-12-17
> **oldfred said:**
> Boot-Repair had all sorts of issues mounting your NTFS partitions. Did you leave Windows hibernated? Or did you resize using the installer, not using Windows own disk tools to shrink the Windows main partition?
Both hibernation and resize set flags that then the Linux NTFS driver will not normally mount the NTFS partition. 
Do not use hibernation if dual booting and run chkdsk from Windows. If Windows does not boot then you need your Windows repairCD or flash drive. Some third party Windows repair tools may run a chkdsk also.

Because Boot-Repair could not see the NTFS Windows partitions to know if they had boot files, it did not offer to install a Windows boot loader. Not sure if installing a Windows boot loader would then let you use f8 and get into a recovery console or not.


I used the Disk Management in Windows to free up 10GB of free space then used the tools in "Do Something else" to format those 10GB for Ubuntu.  After running first install it showed the following options for startup.  (Not sure these are correct because they are from memory but close.)
Ubuntu 
Ubuntu repair
Memtest 
Memtest 86+
Windows 7
On intial start up it looked good for Ubuntu showing a purple page with the Ubunu logo then made a "bonk" noise and went to black screen.  I then started it using the windows repair mode and was sent to an Ubuntu screen with a number of options, which I did not know how to use at the time, so left it and tried to reboot using "Do Something else."  I dont believe I used hibernate in Windows but don't know for sure.

It appreared most everything was right intially in terms it saw W7 and Ubuntu at least all options were availalbe to me on initial boot up ina purple Ubuntu screen. But except for the Ubuntu repair I have not been able to get to either system since adding Ubuntu to the computer except for right now using a USB live session.  I did not try windows at all, but went straight away to try and re-install Ubuntu when it did not work off the bat, I think that is when I made the mess you see on the 

Is running this LILO how I am trying to get a bootloader installed?  I ran the first command of the lilo and got this message:
 LILO configuration                                                        &#9474;   
 &#9474;                                                                           &#9474;   
 &#9474; It seems to be your first LILO installation. It is absolutely necessary   &#9474;   
 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474;   
 &#9474; /sbin/lilo after this.                                                    &#9474;   
 &#9474;                                                                           &#9474;   
 &#9474; LILO won't work if you don't do this.  

I am not sure how to go about it I tried running liloconfig and liloconfig(8) in the terminal without luck. How do i configure LILO?  Since I am running of a USB disk will the LILO affect the non booted hard drive?  I do see how the next command has "sda" in it.  sudo lilo -M /dev/sda mbr

I do have a W7 recovery disk and tried to do some sort of test but got  an error saying something to the effect of "if you have installed a new  camera unplug it and try again."  which I have seen before and can't get  past.  I can try to see if there is a chkdsk feature available on it.

---

### Post by oldfred on 2013-12-17
I said to ignore error messages. Lilo is a full boot loader like grub is, but works somewhat more like Windows in that it uses the boot flag and has boot code in a PBR - partition boot sector. We do not want Lilo installed just its Windows like boot loader. Then it will boot Windows, if Windows is bootable, or may let you use f8 to get into Windows repair console. This is more for those that only have Linux to try to fix Windows.

If you have a Windows repair disk you can use it to fix Windows also. But you have to run auto fix 3 times to get everything fixed or use its command line.

In Windows the fixMBR is also installing a Windows boot loader to the MBR. That is essentially the same as just the install of the lilo boot loader to the MBR. All the boot code in the MBR does is look at partition table, find boot flag, do some error checks and jump to the partition that had the boot flag. PBR for Windows has in it to then boot with ntldr for XP or bootmgr with later Windows.

f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

    

 Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)

---

### Post by Photobug on 2013-12-17
Thank you so much OldFred,
After completing the LILO commands here my windows 7 OS fired right up.  I have spent the last couple of hours making multiple backups and organizing the D drive to make room for a backup of the OS as well as backing it up before moving on to trying to get Ubuntu running alongside windows 7.  

How should I proceed from here to clean up the corrupt Ubuntu partition?

---

### Post by oldfred on 2013-12-17
If you use manual instal you can just overwrite it. If resizing, use Windows to shrink the NTFS partition, reboot Windows so it can run its chkdsk and make whatever repairs it likes to do on a new size. Do not create partitions with Windows.
Then use gparted to either create the partitions you want or delete the old partition and install into the unallocated space. I always prefer the Something Else or manual install, but if you have unallocated you should not have issues. Some in reinstalling or using LVM overwrite the entire drive, so that is why backups are so important. (not just copies to another partition on the same drive).

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

