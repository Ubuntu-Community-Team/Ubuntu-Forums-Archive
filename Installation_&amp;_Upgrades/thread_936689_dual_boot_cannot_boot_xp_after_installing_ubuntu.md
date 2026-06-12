---
title: "dual boot: cannot boot xp after installing ubuntu"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by Tuna_Can on 2008-10-03
I'm pretty sure my mistake was from not defragmenting before installing(no warning) and letting ubuntu partition for me.
Ubuntu boots and runs fine and I can even view files from the "windows side" of my hdd. The problem is when I restart and select windows xp from the menu it says "a disc read error occured, press ctrl alt del to restart"
I have my windows recovery disc but I REALLY hope there is a way to save all my stuff. :(
Please help! Thanks!

---

### Post by Herman on 2008-10-03
> I'm pretty sure my mistake was from not defragmenting before installing(no warning) and letting ubuntu partition for me. :D It doesn't make any difference at all whether or not you defrag your Windows drive before you resize it with GParted.

The partitioner Ubuntu uses is among the safest around, however, you should always make a backup before using any hard disk partitioner.

You could have run CHKDSK first though, that might help, and it is recommended in the GParted documenttion to run CHKDSK afterwards too.
Maybe you could give that a try, if you have your Windows 'Installation Disk' around. 
Boot it to a  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and run CHKDSk on the file system.
I prefer to run CHKDSK /R myself, but some people recommend CHKDSK /F, I think CHKDSK /F is quicker, but CHKDSK /R will do more.
That may or may not fix it, depending on whether or not that was the problem, but it won't hurt, except maybe it could be a waste of time.

A 'Recovery Disk' probably won't do you any good. Is that the kind that 'restores your computer to its factory shipped state?' (will erase everything - you don't want to do that!

Try to see if you can boot Windows XP in 'safe mode', by pressing F8 when it starts to boot too, and see if that gets you anywhere.

If you still have trouble, please post the output from 'sudo fdisk -lu', from a terminal in your Ubuntu Live CD.
```
sudo fdisk -lu
```

---

### Post by Tuna_Can on 2008-10-03
Thanks for reply!
Okay so I didn't have an xp boot disk so I went and downloaded the iso for one, burned it to cd, and after changing the bios to boot from cd, Windows loads fine. So I did a CHKDSK which was fine until it told me to do a /F. When i tried CHKDSK /F it said "CHKDSK cannot run because the volume is in use by another process"
Also when xp loads it keeps asking me to install new hardware (the volume). I figured that was the interfering process so installed, restarted comp, tried CHKDSK /F again but same error. I also tried it in safe mode with no luck.


output of sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x874a874a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   353156894   176578416    7  HPFS/NTFS
/dev/sda2       353156895   488392064    67617585    5  Extended
/dev/sda5       353156958   482785379    64814211   83  Linux
/dev/sda6       482785443   488392064     2803311   82  Linux swap / Solaris


Edit: I just saw the link to the recovery console thing in your post, ill do that now.
Edit: I get these errors when I try to install Recovery Console(from the i386 folder on my hdd, NOT the cd because I don't have it) using start/run/C:\WINDOWS\I386\WINNT32.EXE /cmdcons
[IMG]http://img236.imageshack.us/img236/5205/errordm4.jpg[/IMG]
[IMG]http://img294.imageshack.us/img294/5791/error2lp2.jpg[/IMG]

---

### Post by Tuna_Can on 2008-10-03
Is it possible to simply burn my I386 folder to a cd and use it as an "installation disk" to boot from it and get to the recovery console that way?

---

### Post by Herman on 2008-10-03
> Is it possible to simply burn my I386 folder to a cd and use it as an "installation disk" to boot from it and get to the recovery console that way?Yes, you can, but it's a little bit of work to do so.

Many computers come with 'recovery disks' instead of bona-fide Windows installation CDs.
Recovery disks are an unwelcome phenomenon because the  only thing they are good for is formatting your whole disk and returning the whole hard disk back to its factory-built state.
They don't provide the user with any of the tools needed for maintenance and repair work on the installed system like an 'Installation Disk' does.
Even worse, some computers don't come with any CDs at all, but a 'Recovery Partition', instead, so if your partition table gets clobbered you could be 'up the creek without a paddle'. (Unless you are good enough with Linux to be able to do without Windows XP from now on).
However, help is at hand, because if you're dual booting with Ubuntu, you can make your own Windows CD from the files already on your hard drive!

The tools and information described below here came mainly from '[Bart's way to create bootable CD-Roms (for Windows/Dos)]("http://www.nu2.nu/bootcd/")' - (by Bart Lagerweij).
Please refer to that site to read about the software and any legal details involved with it's use. [Legal information]("http://www.nu2.nu/legal/").
> You are allowed to reproduce, download, copy or translate information from this website, only under the following conditions:

[LIST=1]
[*]Use of such information includes our copyright notice.
[*]Use of such information includes a hyperlink to the Nu2.nu website/page.
[*]Use of such information includes the name of the author.
[/LIST]
 1. [I]Copyright (c) 2000-2008 by Nu2 Productions. All rights reserved.
2. [/I][Bart's way to create bootable CD-Roms (for Windows/Dos]("http://www.nu2.nu/bootcd/")
3. Herman -  [Send a Private Message to Herman]("http://ubuntuforums.org/private.php?do=newpm&u=31861").

**1. i386 folder**
First, boot Ubuntu and check to make sure you can find a folder in your C drive called i386.
...your C drive is mounted right?
If it isn't then mount it, look here: [            Mounting Windows FAT32 or NTFS filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop")
Find a folder in your C drive called i386, it could be right on the root of the C file system. 
If it isn't, you'll have to go looking for it and there might be more than one of them, look for it with the find files util or the like.
Just leave it there for now, but remember where it is. (Note the /path_to_file/filename).

**2. Drivers**
Second, go into drive C: and look for the drivers, as far as I know the drivers are mostly in C:\Windows\System and C:\Windows\System\system32\drivers.
Make a folder and call it drivers and copy all available drivers to your drivers folder.
And/or:
Open Firefox and go to the computer or motherboard manufacturer's website and download all the drivers you might need.
Copy all those drivers to your drivers folder too.

**3. Windows Product Key**
Find your Windows product key and save that somewhere handy for when you re-install.

**4. BCD Downloads**
Go to [http://www.nu2.nu/bootcd/#wxp](http://www.nu2.nu/bootcd/#wxp) and download [BCD full package v1.1.1]("http://www.nu2.nu/download.php?sFile=bcd111.zip") (523KB) 

Go to [http://www.nu2.nu/bootcd/#wxp](http://www.nu2.nu/bootcd/#wxp) and download [Windows XP package v1.0 (wxp10.zip)]("http://www.nu2.nu/download.php?sFile=wxp10.zip") (5KB)

Go to the [Free French Frog]("http://www.frogaspi.org/download.htm#frogaspi") site and get FrogAspi, already renamed as 'wnaspi32.dll'.

If those three files landed on your Desktop, move them into your /home/username directory.

**5. Combining the Files**
I repeat, those three files you just downloaded need to be located in your /home/username directory for the following commands to work.

**Extract** the contents of bcd111.zip and you will have a directory named bcd containing a directory named bin and five files: bcd.cmd  bcd.sam  bcdlog.txt  makelog.cmd  nu2lic.txt. ```
unzip bcd111.zip -d bcd
```**Extract**  wxp10.zip  into your bcd directory and you'll have a folder inside your bcd directory named: cds
```
unzip wxp10.zip -d bcd
```**Copy** the file wnaspi32.dll to your bcd/bin directory.
```
cp wnaspi32.dll bcd/bin/
```**Copy your i386 folder** to bcd/cds/wxphome/files... if you have [B]Windows XP Home Edition
[/B]```
cp -r i386 bcd/cds/wxphome/files/
```**or** if you are using **Windows XP Professional** it would be: bcd/cds/wxppro/files
 ```
cp -r i386 bcd/cds/wxppro/files/
```**Copy your drivers folder** to bcd/cds/winxphome/files... if you have [B]Windows XP Home Edition
[/B]```
cp -r drivers bcd/cds/wxphome/files/
```**or** if you are using **Windows XP Professional** it would be: bcd/cds/winxppro/files
```
cp -r drivers bcd/cds/wxppro/files/
```**6.** **Copy and paste the bcd directory to the root of drive C.**

**Service pack 2** can be slipstreamed, copy the 260mb sp2.exe file from the service pack2 CD to the root of C drive.
If you don't have a Service Pack2 CD, you can download SP2 from Microsoft. 
SP2 is a free download and can be downloaded using the following link: [http://www.microsoft.com/windowsxp/sp2/default.mspx](http://www.microsoft.com/windowsxp/sp2/default.mspx)

NOTE: These instructions were made for Windows with the FAT32 file system that has always been writable from Linux. 
Even if you have Windows with NTFS it is now writable from Linux too if you are running Ubuntu Gutsy Gibbon or later, or if special drivers are installed in Feisty Fawn.
Otherwise, you can copy the bcd directory and sp2.exe to a CD, or a USB flash drive and transfer the files that way, as long as they end up at the root of drive C somehow.

THAT'S ALL YOU CAN DO IN LINUX
===================================================
THE REST MUST BE DONE IN WINDOWS

Then boot WindowsXP
     'Start'-->'Run', and type in c: \sp2.exe -s:c:\bcd\ccds\wxphome\files\
if you have XP Home, or if you have XP Pro,
'Start'-->'Run', and type in c: \sp2.exe -s:c:\bcd\ccds\wxppro\files\
```
c:\sp2.exe -s:c:\bcd\ccds\wxphome\files\
```and click OK.
...you should see 'extracting files' and the Windows Service Pack 2 Setup Wizard progress bars.

After the Service Pack 2 integration process is done, navigate to your BCD folder and check and verify the presence of a file named /bcd/cds/wxphome/files/win51lic.sp2
If it isn't there you made a syntax error when typing the command, the only whitespace in it is between 'exe' and '-s:c:\\bcd\...'
Keep re-running the command until it works properly.
** This is very important** as this will prevent the CD asking "put the SPx CD into drive A:" during install."
Of course, this is a stupid error message, because drive A is the floppy disk drive, so you can't put a CD in it, so it's a show stopper.

**7. Burn the CD**.
Boot Windows and click 'Start'-->'Run', and type 'cmd'.

Place a blank CD in the drive.

cd up into the bcd folder,
```
cd \bcd
``` Take a quick look around with 'dir' to verify you are in the BCD folder, (you should see some files names you'll recognize).
```
dir
```if you have XP Home, type: bcd wxphome
if you have XP Pro,     type: bcd wxppro
```
bcd wxphome
```or
```
bcd wxppro
```From then on everything should be automatic and you'll end up with a burnt CD.

NOTE: The program makes and .iso file in C:\Documents and Settings\username\Local Settings\temp called 'bcd.iso', and it deletes the .iso as soon as the CD has been burned.
If there has been an error in cdrecord, you have a set number of seconds to copy the .iso file to a safe location before it gets deleted.
If you think you might need to do that, it will help to have that folder open beforehand, to save time. Then run the last command again. If you can save the .iso you can then reboot and burn it in Ubuntu.

**8.** **Test your new CD.**

---

### Post by Herman on 2008-10-03
> So I did a CHKDSK which was fine until it told me to do a /F. When i tried CHKDSK /F it said "CHKDSK cannot run because the volume is in use by another process"
Also when xp loads it keeps asking me to install new hardware (the volume). I figured that was the interfering process so installed, restarted comp, tried CHKDSK /F again but same error. I also tried it in safe mode with no luck.:D To answer your earlier question, as long as you can boot Windows in the first place, you can always just schedule CHKDSK to run next time you reboot Windows XP.
You can go 'My Computer',-->'Local Disk (C:), and right-click on 'Properties'.
Open the 'Tools' tab, and in the 'Error Checking' box, click the 'Check Now' button.
A 'Check Disk' window will open.

[LIST=1]
[*]Place a check mark in the square for 'automatically fix file system errors', and also a check mark in the square for 'Scan for and attempt recovery of bad sectors'.
[*]Click the 'Start' button
[*]A window will open advising you it can't do it right now but you can schedule a disk check for next time you boot up. Click Yes.
[*]Reboot your computer and choose Windows XP from your GRUB menu. Don't be alarmed when it blue-screens in the middle of starting Windows XP and runs your disk check.
[/LIST]
Just to make sure you understand, or in case I missed anything, here's a Symantec link about how to do that, [How to Run Microsoft CHKDSK from the command line]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004066687571562").

You can't get CHKDSK to run a check in your Windows file system while Windows is running in the file system it's trying to check, in case that's what you're trying to do. :D

---

