---
title: "Multi-booting Vista/Gutsy on Sony Vaio TZ, VGN-TZ130N"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Kache on 2008-01-08
Note: This guide hasn't been completed yet.

I've been meddling with my new laptop a whole ton- installing, reformatting, reinstalling over and over, trying to get it just right- and I think I got it.

My goal was to set up a multi-boot system with Vista and Ubuntu. Therefore, the first step was to get a clean install of Vista without missing out on the "good" included software (a task in itself!). Then, we'll look into how to get as much compatibility with Ubuntu as possible.

This has been a huge learning process for myself, and after having getting help from so many sources online, and I just thought it'd be extremely helpful to consolidate all the information I've come across and to share what I did.

Sites:
[Sony Vaio TZ Series: Quest for 100% Compatibility]("http://ubuntuforums.org/showthread.php?t=514292")

Well alright, to get a multi-boot system going with Vista, we all know Windows has to be babied, so we let it go first. =P
[INDENT]
[SIZE="3"]**Getting a Clean install of Windows Vista**[/SIZE][/INDENT]

I found a few sites telling how to get this done, like:
[LIST]
[*][http://forum.notebookreview.com/showthread.php?t=146033](http://forum.notebookreview.com/showthread.php?t=146033)
[*][http://www.davidlouisedelman.com/technology/vaio-bloatware/](http://www.davidlouisedelman.com/technology/vaio-bloatware/)
[/LIST]
They weren't good enough for me. I wanted a truly clean install while not losing *any* of the functionality. Besides, none of them tell you how to get *completely* rid of the pesky restore partition. I even tried doing that by installing drivers/software on top of a retail Vista, but then I lost out on some Vaio functionality. It turns out it'll take a ton of patience and an instance of Gparted. You'll see what I'm talking about.

[INDENT]**_Backup your recovery partition to media_**[/INDENT]
Honestly, I've forgotten the how I did this exactly. Check the folders in c:\Program Files\Sony for a launcher.exe that runs the Sony Recovery tools to create the two DVDs.
[INDENT]**_Reinstall Windows (recommended, but may be optional)_**[/INDENT]
For some reason, installing clean retail windows and then using the recovery disks to install software/drivers doesn't give you everything! Some important software I could only install by using the recovery disk installation.
-Boot up with the recovery disks and run the Sony Recovery tools. Do a restore complete system from the disks.
-It doesn't matter if you decide to include the Vaio recovery partition. We're going to remove it later anyway.
-Select the default c: size, which uses your whole hard disk.
-Reinstall option: You can save a lot of time installing and cut out a lot of bloat by not ever installing the Sony modules from the second disk, since they're mostly bloatware. The cost is that you will need to manually install a few items using the recovery disks afterwards, and some of the shortcuts to some applications won't be in the start menu. (Note: That is, after the computer has rebooted once. Once you confirm "Complete Recovery," it asks for both disks, reboots, and asks for both disks again to install Sony modules. Just hit 'cancel' when prompted for the 2nd disk. There will be two more reboots in quick succession after that one.)
[INDENT]**_Hunting down bloatware and finishing windows installation_**[/INDENT]
_The Uninstallation Window_
Below is a partial list the programs you would find in the control panel's uninstall. Items in bold are essential for functionality. Italicized is useful software most people would use. Anything not on this list is either nonessential, trialware, or software you personally may decide to keep. If you find something on this list not in your uninstall window, we'll be installing them afterward.
[INDENT][I]Adobe Flash Player 9 ActiveX
Adobe Reader 8[/I]
[B]Alps Pointing-device for VAIO
Battery Care function
HDAUDIO SoftV92 Data Fax Modem with SmartCP
Instant Mode
Indel(R) Graphics Media Accelerator Driver[/B]
*Java(TM) SE Runtime Environment 6*
**LAN Setting Utility**
**Microsoft .NET Framework 1.1**
**MSXML 4.0 SP2**
[B]Peripheral Device & Storage Media Restriction Setting Utility
Protector Suite QL 5.6
Realtek High Definition Audio Driver
Setting Utility Series[/B]
**Sony Utilities DLL**
**VAIO AV Mode Launcher**
VAIO Azure Float Wallpaper (see note below)
**VAIO Central**
**VAIO Event Service**
VAIO Floral Dusk Wallpaper (see note)
[B]VAIO HDD Protection
VAIO Help And Support[/B]
VAIO Photo 2007 (see note)
**VAIO Power Management**
[B]VAIO Service Utility
VAIO Status Monitor[/B]
VAIO Teal Whisper Wallpaper (see note)
**VAIO Update 3**
[/INDENT]
Note: Photos and wallpapers are found in C:\Windows\Web and C:\Users\Public\Pictures\Sample Pictures\Vaio Sample Photos. Back them up them manually if you'd like before uninstalling them.

_Picking up the Pieces_
Now we need to install a few of the missing programs if you did the 2nd disk skip earlier. Load up VAIO Recovery Center using your backup VAIO Recovery Disks you made earlier and run the Reinstall Programs or Drivers tool. Checkbox and install anything you may be missing from the above list. In addition, the following items aren't listed in the uninstallation menu, so install them too.
[INDENT]
Battery Checker
VAIO Documentation
Fingerprint Protector Suite
Instant On
Powersetting Update
Bluetooth Utility
Wireless Switch Setting Utility[/INDENT]
If there's stuff in the 2nd disk I missed, please let me know.
[INDENT]**_Removing the Windows Restore Environment (EISA-Configuration) partition_**[/INDENT]
-In windows, go to Control Panel>Administrative Tools>Computer management>Storage>Disk Management. Shrink your C: partition as much as you can.
-Boot up with your first recovery disk. Select your shrunk partition and hit next. Start a Command Line from the list of recovery tools.
-In the command line, run "diskpart" from the Windows\System32 directory.
-Now, run the following commands: "list disk", "select disk 0", "list partition", "select partition 1", "delete partition override". For more detailed information, see [here]("http://mharbauer.spaces.live.com/blog/cns!2171BCF268FDF9DB!190.entry").
-Type "exit" to exit diskpart. Run "exit" again to leave the command line. Restart your computer with the Ubuntu LiveCD.
-Use the Ubuntu LiveCD and run gparted (System>Administration>Partition Editor) and move the windows partition all the way to the left (takes a *really* long time).
-Reboot with the Recovery Disk so that Windows can repair the partition we just messed with. Restart, and Vista will CHKDSK itself on next bootup.
-Use Vista's Disk Management to extend the windows partition however big you want before installing Ubuntu. Keep in mind for Ubuntu swap space.
(There are several ways to do all of this, and I've tried many of them. This one gives the best results, in my opinion in terms of time, reliability, and outcome.)

[INDENT][SIZE="3"]**Ah, Ubuntu.**[/SIZE][/INDENT]
Finally. We've got a clean install of Vista booting up as the first and only partition on the drive. Now to leave Vista in its own little world and install Ubuntu.
[INDENT]**_Install Ubuntu_**[/INDENT]
[INDENT]**_Sound_**[/INDENT]
[INDENT]**_Touchpad_**[/INDENT]
[INDENT]**_Hibernate_**[/INDENT]

Notes for myself:

DO NOT SET LAPTOP MODE!!!

vim-full
gconf
xorg.conf
uswsusp
laptop mode
synaptics

Using the Ubuntu liveCD, I deleted the 1.5gb partition and moved my NTFS partition to the front of my hard drive. (It took a *really* long time.) This confuses Vista somehow, and your Vista won't boot anymore. Boot up with the Recovery disks and use the included tools to fix the problem. (Perhaps the only thing that was wrong was the MBR, which would've been overwritten by GRUB later anyway, so perhaps Ubuntu *can* be installed immediately. Let me know if if this is so.)


==Not done==

---

### Post by K.Mandla on 2008-01-09
Moved to Installation and Upgrades.

---

### Post by Kache on 2008-01-10
Reserved Post (I duno if this forum has a post limit per message, so just in case)

My Vista Tweaks
-annoying Fn button beep
-battery care function
-sidebar

---

