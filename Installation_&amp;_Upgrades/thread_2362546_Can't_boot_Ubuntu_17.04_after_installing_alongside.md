---
title: "Can't boot Ubuntu 17.04 after installing alongside Windows 10"
date: 2017-05-30
forum: Installation &amp; Upgrades
---

### Post by osakawilson2 on 2017-05-30
I'm on an Acer Aspire XC-730 running Windows 10 64-bit.

I shrunk my windows partition and made a bootable Ubuntu USB with Rufus. I installed it onto an empty partition (195GB) that is labeled "Healthy Primary", but has no letter indication. When I went to boot and called up the boot settings, it did not show up. Only the original Windows and the USB options show up. 

So I booted up the USB Ubuntu and took a look at it in gparted and it shows that 10GB are used in that partition, however when I checked again in Windows, it says the whole partition is available. 

Two things I did that may be stupid: In Windows Disk Management, I selected the partition and clicked 'make partition active' under actions in the menu. Also while in the boot menu, I made a supervisor password. Otherwise, I stuck to what I thought was basic dual boot setup. 

So, it boots straight to Windows and does not show up as an option in the boot order. Any ideas?

---

### Post by kc1di on 2017-05-30
Hello osakawilson2  and Welcome to Ubuntu,

You may want to try Boot-Repair found [here: ]("https://help.ubuntu.com/community/Boot-Repair")

other things you'll need to know , did you install ubuntu in uefi mode?  if not you will need to in order to dual boot with windows 10. 
Good Luck

---

### Post by osakawilson2 on 2017-05-30
I'll check out Boot-Repair. 

I have never heard of UEFI mode, I went to a page on how to adjust UEFI boot settings. It looks like Boot Settings and the description of how to get there looks just like getting to boot settings. I'll keep looking, but I seem to be missing something. I installed from the Ubuntu USB, so I don't think I was in UEFI mode.

---

### Post by osakawilson2 on 2017-05-30
I ran Boot-Repair in UbuntuLive following the directions on the page and nothing changed. 

Any ideas of how to get into UEFI mode? All the sources I find just tell me how to enter the BIOS settings.

---

### Post by RobGoss on 2017-05-30
Acer is a bit harder to install Ubuntu or any Linux Os for that matter. You'll have to access your BIOS and set Trust, in order to be able to install Ubuntu 

If you system is fairly new them most likely it's UEFI. This means if Windows is installed in UEFI them Ubuntu must also be installed in the same order

I recommend making a full backup of your data and files just incase something goes wrong

Most new user choose to dual boot their systems, you will need to do your homework first to fully understand what's involved with this process

---

### Post by yancek on 2017-05-30
> I installed it onto an empty partition (195GB) that is labeled "Healthy Primary", but has no letter indication.

That is default/expected behavior from a windows system.  It can't read or write to a Linux filesystem such as you are using with Ubuntu.  I don't believe it is possible to assign a drive letter to a Linux partition.  It 'may' be possible to install third party software to enable at least read ability of Linux filesystems from windows although I don't know why you would want to.

> So I booted up the USB Ubuntu and took a look at it in gparted and it  shows that 10GB are used in that partition, however when I checked again  in Windows, it says the whole partition is available. 


Also expected behavior for the same reason as posted above.  From windows with a default install that is all you will see of a Linux filesystem.

> Two things I did that may be stupid: In Windows Disk Management, I  selected the partition and clicked 'make partition active' under actions  in the menu.

I don't know of any Linux distribution that requires it's partition to be set as active although pretty much any windows needs it.  Do you have UEFI or MBR?  If it is windows, most probably UEFI which you can check by entering the BIOS.

Boot repair provides a link which you can post here that has details on your system which would help people to help you.  You forgot to post it.

---

### Post by osakawilson2 on 2017-05-30
Here's what I've done so far:

1. Backed up Windows.
2. Made an UbuntuLive USB.
3. Shrunk the Windows partition.
4. Through the USB installed Ubuntu onto an open partition (Windows doesn't acknowldege that the install is there, but UbuntuLive does.)
5. Tried to boot with F12, but only the Windows boot and the UbuntuLive boot showed up.
6. Tried to change the BIOS settings to change boot order, but couldn't find it in the boot order. 
7. Tried Boot-Repair and nothing happened. 

Everywhere I look it says to change the trust within the UEFI, but I can't find where I go and what I do to change the trust for the Ubuntu boot. 

What I believe needs to be done:

1. Find UEFI settings (So far this has eluded me.)
2. Set trust on the Ubuntu bootloaders in shimx64.efi and grubx64.efi
3. Use EFI bootmgr to add Ubuntu to boot order (I imagine once I find the UEFI settings, I'll know where this is too.)

I haven't gotten past step one. I've looked on multiple pages, but can't find the UEFI settings. They all seem to guide me to BIOS settings, but as I mentioned, there is no trace of the Ubuntu boot in my BIOS settings. I am fully ready to do my homework, but just don't know where to look from here.

---

### Post by oldfred on 2017-05-30
Parted's boot flag or Windows set active have totally different meanings with BIOS & UEFI.
With UEFI the boot flag must only be on the ESP - efi system partition which is normally the first (or second) partition FAT32 formatted.

If Windows 10 you must have fast start up off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Windows will not see Linux partitions or not see the data in them. Linux can read the NTFS partitions, if not hibernated nor need chkdsk. Often better to have a separate NTFS data partition and set Windows system partition as read only. The Linux NTFS driver shows all the normally hidden files & folders and users accidentally can damage system. With my old XP system first thing I would do was unhide everything. I then often broke it, but also then learned how to fix it.

Linux does not use letters for "drives". And Windows confuses partitions with drives. A drive is a physical device and partitions are sub-divisions of that device.
In Windows a d: "drive" can be a second partition or a second physical drive.
Linux uses drive letters like sda, sdb sdc etc. and partitions are numbers after drive like sda1, sda2, sdb1 etc.

Acer has a unique requirement for UEFI boot. Its actually better than many that make it really difficult to boot Ubuntu.
You have to set a UEFI Supervisory password and then from inside UEFI set trust on the .efi boot files in the ESP - efi system partition.
Also make sure you have latest UEFI from Acer. Some had to downgrade UEFI, but newer threads users have said upgrade solves problem.

Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

Lots more info in link in my signature on UEFI, below.

---

### Post by osakawilson2 on 2017-05-30
So far I've turned off Fast Start Up, made a supervisor password in the BIOS. You said make it in the UEFI, but I haven't found the UEFI settings yet. I followed the directions from the first Trust Settings link, but they just lead me to the BIOS settings. The link said that some of the grey items would turn blue, particularly [COLOR=#000000]"Select an UEFI file as trusted for executing", however, I don't find anything like that. 

Another link said updating the BIOS should work. I downloaded that and ran the exe file, but nothing happened and it didn't fix it.

Ill take a look at the other links later and see if any of those work. [/COLOR]

---

### Post by oldfred on 2017-05-30
If you have updated UEFI/BIOS, you also have to go back and redo all UEFI settings. It reverts most to defaults.
With UEFI some settings are now saved in its NVRAM, with old BIOS no settings were ever saved.

UEFI is the new BIOS.
Vendors incorrect use BIOS since most users know that.

       UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by osakawilson2 on 2017-05-30
So, I didn't update my BIOS. I downloaded it from ACER and ran the  executable app in the WIN folder, but after showing me the menu, it just  closed. The Version in my BIOS now is still the old one. It said click  any key to continue, so I did that a few times, then it just disappeared  with no changes. It is definitely the one for my computer. 

Anyway, besides that, I went through each link and all of them say that once you set the supervisor password, the option to [COLOR=#000000]"Select an UEFI file as trusted for executing" will appear. This is not the case. 

The  only thing I haven't done is update the BIOS. Either I am doing  something wrong or the file from ACER is bad. In a video, the BIOS  update file is supposed to open a GUI. Mine didn't. [/COLOR]

---

### Post by oldfred on 2017-05-30
I  do not know Acer, but my UEFI updates have 3 ways and I never have run from inside Windows.
The usual file I download has an update file, not an executeable. And that file can be on a FAT32 partition or flash drive or they offer a full DOS bootable flash drive with the update file.
And when I just have file, I open it from within the UEFI.
Did the executeable extract a file for update?

This says the .exe when clicked just extracts the update file.
[https://www.youtube.com/watch?v=Oyy1uKIPB6s](https://www.youtube.com/watch?v=Oyy1uKIPB6s)

---

### Post by osakawilson2 on 2017-05-31
The update download came zipped in a folder that contained four folders: Appendix, EFI, ROM, and WIN.

Appendix contained: EFI Flash SOP_0717 (PDF file), and Windows Flash Utility SOP_0714(PDF file)
EFI contained: AfuEfix64.efi and FLASH.nsh
ROM contained: R01-A2.16M 
WIN contained: AFUWINx64 (Application), amifldrv64.sys (System file), and FLASH (Windows Batch File)

The contents of EFI Flash SOP_0714 were:
 EFI Flash SOP  
1. When you see the LOGO or hear one short beep, please press &#8220;Delete&#8221; to enter BIOS Setup Utility.  
2. Choose &#8220;Authentication&#8221; page and select &#8220;Secure Boot&#8221; to disabled.  
3. BIOS Setup Utility will disable &#8220;Secure Boot&#8221;  
4. Choose &#8220;Exit&#8221; page and select &#8220;Save & Exit Setup&#8221; and press &#8220;Enter&#8221;.  
5. Select &#8220;Yes&#8221; to restart.  
6. Press hot key F12 to enter Boot Menu, and select EFI USB thumbdrive.  
7. Under the EFI system, and choose the Removable BlockDevice group  ( the Removable BlockDevice location is dynamic.)  
8. Enter &#8220;\Service\EFI&#8221; folder.  
9. Type flash.nsh, and use it to flash the ROMs.  
10. After finish , Press the power button to shut down the system.  
11. Boot system. When you hear two short beeps, please press &#8220;Delete&#8221; to enter BIOS Setup Menu.  
12. Select &#8220;Load Default Setting&#8221; and press &#8220;Enter&#8221;. Select &#8220;Yes&#8221; to load default settings.  
13. Select &#8220;Save & Exit Setup&#8221; and press &#8220;Enter&#8221;.  
PS. System may reboot 2 or 3 times after flash BIOS. This is normal behavior. 

There contents of Windows Flash Utility SOP_0714 are:
 Windows Flash Utility SOP  
1. Please enter &#8220;Service\WIN&#8221; folder and select &#8220;Flash.bat&#8221;.  
2. Please double click &#8221;Flash.bat&#8221;.  
3. The system will prompt a command window and select &#8220;Yes&#8221; to continue process.  
4. Please wait BIOS update process. Please restart your system after updating BIOS completely. 5. When you see the LOGO or hear one short beep, please press &#8220;Delete&#8221; to enter BIOS Setup Menu.  
6. Change page to &#8220;Exit&#8221;.  
7. Select &#8220;Load Default Setting&#8221; and press &#8220;Enter&#8221;. Select &#8220;Yes&#8221; to load default settings.  
8. Select &#8220;Save & Exit Setup&#8221; and press &#8220;Enter&#8221;.  
9. Select &#8220;Yes&#8221; to restart. 
PS. System may reboot 2 or 3 times after flash BIOS. This is normal behavior. 

These appear to be directions for how to do something. Do I want to follow one or both of these directions?

---

### Post by oldfred on 2017-05-31
It looks like one is the update from a flash drive from within UEFI, and the other is directly from within Windows.

On update from flash drive does it say to make a flash drive, probably has to be FAT32 and copy files to flash drive?
Then in UEFI use those files to update UEFI?

---

