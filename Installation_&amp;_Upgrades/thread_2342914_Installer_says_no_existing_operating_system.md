---
title: "Installer says no existing operating system"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by tjsilver on 2016-11-11
Hello!

First, please accept my apology if this has already been covered - if it has, I couldn't find it! (Well, it may have been but I didn't understand how the chap resolved it)

My laptop is a Dell Inspiron 17.  Started life with Windows 8 pro, upgraded to 8.1 and then finally Windows 10.  Now that it is out of warranty I thought I'd 'have a go' with Ubuntu.

However, the Ubuntu installer doesn't/can't 'see' my existing OS so I'm not being offered the option to install along-side my existing OS.

What to do next please (in plain, simple, idiot speak).

Tim

---

### Post by yancek on 2016-11-11
Windows 8 and 10 use UEFI by default if it is pre-installed so you will need to install Ubuntu UEFI.  Read the official Ubuntu documentation below before beginning.  Trying to use the auto-install method "install Alongside" is going to be troublesome so you will need to use the manual method.  In Ubuntu, it is the "Something Else" option.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2016-11-11
Understand that Win10 uses the new default "hibernation" method which prevents Linux from mounting (and therefore, reading) the Windows partitions even when Win10 is not running.

This will prevent any Linux installer from "seeing" the Windows OS.

What you need to do in Win10 is disable something known as FastStartup: 

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by tjsilver on 2016-11-12
Thanks for replies.  Am about create EFI iso and thanks for instructions regarding disabling 'fast startup' - I'd read I should do it but didn't know how!

OK. So I created a EFI pendrive using Rufus (I chose the MBR option). Disabled 'Fast Startup', shut down and restarted in to Windows. Shut down, restarted (changing boot device to USB) - Ubuntu installer still doesn't see existing OS!

More help please.

---

### Post by oldfred on 2016-11-12
Post this from terminal in Ubuntu's live installer:
sudo parted -l

Do you have Intel SRT which creates or uses a small partition for start up, often a smaller SSD using the size of RAM as the hibernation location. If UEFI/BIOS setting still has that on or drive still has RAID meta-data it will cause issues. Intel SRT seen as RAID, even though not really RAID.
If you have the smaller SSD & it is at least 16GB you can install Ubuntu's / (root) just to that and use HDD for /home. That makes all of Ubuntu fast  where it only made Windows boot faster.
If Intel SRT make sure drive is also set to AHCI.
       Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[URL="http://ubuntuforums.org/showthread.php?t=2199382"]http://ubuntuforums.org/showthread.php?t=2199382
[/URL]
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121) 

[URL="http://ubuntuforums.org/showthread.php?t=2199382"]
[/URL]

---

### Post by tjsilver on 2016-11-13
Thanks for all the input but things are starting to get a bit too techie for an old fart like me. As I have Windows 10 Pro I've installed it as a VM which, on reflection, actually better suits my reason for wanting Ubuntu

---

