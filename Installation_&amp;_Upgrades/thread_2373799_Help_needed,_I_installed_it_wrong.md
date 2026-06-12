---
title: "Help needed, I installed it wrong"
date: 2017-10-09
forum: Installation &amp; Upgrades
---

### Post by krashkitty on 2017-10-09
I was trying to install Ubuntu alongside Windows 8.1. I backed up my system using the Macrion Reflect program. I made the USB stick, and did the thing where it shrinks the space for it, I set that at 100,000. Then I got to the blue screen, where I was supposed to choose "Use a device". I clicked that, and then I was supposed to click "boot from EFI device", but that wasn't an option. The 1st two options were Letters and possibly numbers. The 3rd option said something about Generic USB. I chose that one because I was using a USB stick. I don't know if that was the right one or not, but I got to the part where I clicked "try Ubuntu". Then I clicked on the install it icon on the Ubuntu desktop. Then I installed it alongside Windows. It said to restart to finish the installation. Upon restarting, there was a black screen with a lot of white text. I have no idea what it really meant, but I saw the word failed a lot. So I pushed the power button on my computer and then restarted it that way. It took me back to Windows, with no sign of Ubuntu. I panicked and did a system restore, back to earlier, just before I made the back up. Then I reinstalled the backup program. Then I checked to see if the change I made in the disk management part had reverted during the system restore. Unfortunately, it had not. So I tried again to install Ubuntu, but it said it's already installed. But I can't find it. I'm not sure where I went wrong, but I'd like to either get my computer back the way it was, or install it properly. I'd really appreciate any help. Thank you.

---

### Post by ajgreeny on 2017-10-10
It is not easy to follow what you tried to do as you have not given us the sort of detailed info we need to really help you.

However, to show us what is on your computer at present follow the instructions in **Boot-Repair** in my signature below to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by krashkitty on 2017-10-10
Thank you for responding. I have made the Boot repair USB drive, and have tried a few times to get the paste bin thing. But instead it keeps giving me a whole text file. From reading the info on the Boot repair pages, I suspect that my internet isn't connecting for some reason when the USB drive is in. I'm hardwired to the internet. I will keep trying to get it to work, and post here once I can get it.

---

### Post by krashkitty on 2017-10-10
Please disregard the last post. I just tried again, & it came right up. It is [http://paste.ubuntu.com/25714032/](http://paste.ubuntu.com/25714032/)  
Also, I don't know if it matters, but my computer is 4 hours ahead since I began trying all this yesterday. And the little pictures next to my bookmarks in Google Chrome are all wrong. I really messed something up big time it seems.

---

### Post by oldfred on 2017-10-10
You have newer UEFI hardware (within last 5 years) and Windows installed in UEFI boot mode.
But you installed Ubuntu in BIOS boot mode.
You have grub installed to gpt's protective MBR for BIOS boot and bios_grub partition.

I normally add both ESP - efi system partition & bios_grub to all drives but only use one or the other.
And that grub is in MBR, will not matter as long as you do not boot in BIOS mode. It just will not ever used.

You can use Boot-Repair's advanced mode and uninstall grub-pc(BIOS boot) and install grub-efi-amd64 (UEFI boot) to convert your install. Be sure to boot Ubuntu live installer in UEFI mode and then add Boot-Repair using ppa.

If you had UEFI boot on in UEFI/BIOS and perhaps a setting to "allow" USB boot, you should have had two boot options for flash drive. Typically UEFI:flash and flash (which is then BIOS boot) where flash is name or label of flash drive. How you boot installer is then how it installs, so you booted in BIOS mode.

---

### Post by krashkitty on 2017-10-10
Oh wow. I really, really appreciate the help. Unfortunately, I don't understand what any of that means. I was just trying to install Ubuntu on my computer as a backup, in case Windows ever broke. I'm not even remotely tech savvy, and so just followed step by step instructions from a website I found, but messed it up somehow. Is there any way I can get simple instructions to fix it, or undo it?

---

### Post by oldfred on 2017-10-10
All you have to do is use Boot-Repair.
But be sure to boot in UEFI mode and reinstall Boot-Repair to you Ubuntu live installer in live mode.
Boot-Repair in advanced mode will walk you thru the process.

Advanced mode screens are here, if you want to see what it will show you, you want the reinstall grub and purge old grub options:
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by krashkitty on 2017-10-10
Ok, thank you. I will try that now. I just hope I don't break it any worse.

---

### Post by krashkitty on 2017-10-10
Ok. I ran the repair. I think it worked. It gave me a new paste thing. [http://paste.ubuntu.com/25715533](http://paste.ubuntu.com/25715533) . Then I rebooted, and it had a dark purple screen with a list of options, like Ubuntu, Advanced Ubuntu. And a  few other things, some were about Windows. I tried doing the 1st one, that just said Ubuntu, and it took me into the Ubuntu screen, where I was able to use Firefox to go online. So I think maybe that part is ok. It also had an icon on the side for Windows, and I was able to navigate through to my pictures and documents. Then I rebooted, to try to get back into Windows, but I wasn't sure which Windows option to choose, so I guessed. The first try asked me some questions about what country I'm in and language, and then said proceed to Windows 8.1. I hit enter, but instead it took me back to the purple menu screen. Then I tried another Windows option, and I'm back in Windows now from that one. I'm not sure if this is really fixed or not though.

---

### Post by krashkitty on 2017-10-10
I just rebooted again so I could note what all the options were. It is a dark purple screen. And it lists the following:
Ubuntu
Advanced Options for Ubuntu
Windows UEFI bootmgfw.efi
Windows Boot UEFI Loader
EFI/ubuntu/mmx64.efi
EFI/Lenovo/Boot/bootmgfw.efi
Windows Boot Manager (on/dev/sda2)
System Setup

If I don't choose anything, it goes into Ubuntu. I got back in Windows by choosing the Windows Boot Manager (on/dev/sda2) option.
Is this how it should look? Both systems seem to work, but I don't know if this is how it should be to go in between the 2 systems.

---

### Post by oldfred on 2017-10-10
Not sure where you are at.

You now have multiple boot managers (menus).
UEFI is a boot manager and is the first one, often it just uses the default, but you can bring up its menu using one time boot key like f10 or f12, check your manual.
Grub2 is a boot manager & boot loader for Linux systems. It will show Ubuntu first in menu & typically Windows near the bottom of menu. Grub only boots working Windows.
Windows only has its BCD which is only for those with multiple Windows installs or sometimes UEFI or third party settings to boot something.

Grub will not boot Windows that needs chkdsk, nor Windows that is hibernated/fast start up on. And Windows with updates may turn fast start up back on. Then grub will not boot it, but you can directly boot Windows from UEFI menu and turn fast start up off again.

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html
[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472) 

You must make a Windows repair/recovery flash drive whether dual booting or not. And you must make a full backup of Windows if any of your data is at all valuable. Systems do fail. Links for Windows 10, but should be similar for 8.
       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
        Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by krashkitty on 2017-10-10
Ok. So I'm still confused. Am I understanding correctly, that Ubuntu is properly installed now, but just Windows needs to be fixed? I followed the instructions to set the Fast Startup., but it was already set up that way, so I didn't change any settings there. I did make a recovery thing yesterday before attempting to install Ubuntu. I used an external hard rive and a USB stick and a free program called Macrium Reflect. Should I erase all that backup and make a new one now, or should I try to fix the Windows menu/menus first? Also, there are Windows updates waiting to be install. I'm holding off on that in case it makes things worse, or should I go ahead and install them.

---

### Post by krashkitty on 2017-10-10
I'm sorry if I'm making this more confusing than it needs to be. I went back and reread your last post and changed the Fast Startup to off. Then I shut down, without installing Windows updates. Then Upon restart, I got the same purple menu:
Ubuntu
Advanced Options for Ubuntu
Windows UEFI bootmgfw.efi
Windows Boot UEFI Loader
EFI/ubuntu/mmx64.efi
EFI/Lenovo/Boot/bootmgfw.efi
Windows Boot Manager (on/dev/sda2)
System Setup

---

### Post by oldfred on 2017-10-10
I do also use Macrium Reflect for my one Windows install. I do not like Windows as it is not particularly easy to install nor do incremental backups. It wants to do its own internal backup, but if hard drive fails, then that backup is not really anything.

You are seeing standard grub menu. 
Does not any of Windows entries work?
Can you boot Windows directly from UEFI menu?

---

### Post by krashkitty on 2017-10-10
If I click on "Windows Boot Manager (on/dev/sda2)" that brings me back into Windows. I've gone back and forth between Ubuntu and Windows a few times now, & I think it seems to be ok. The only issue I notice is that when I enter Windows after being in Ubuntu, my clock is set ahead by 4 hours. A google search indicates that that may be solved by setting the Ubuntu clock to local. I hesitate to do that though before asking if that should be ok. I would like to install the windows updates, set that clock if appropriate, and run Ccleaner on Windows before making another backup with Macrium Reflect. Do you think it would be ok to take those steps now? I'm really nervous about making any more mistakes. If I make the backup, is it ok to delete the previous backup? I'm out of USB drives. But I don't know if I should keep yesterdays backup or not.

---

### Post by oldfred on 2017-10-10
That looks like a standard grub menu.
Not sure why several Windows options, but sometimes Boot-Repair adds duplicates.
The system setup should take you directly to UEFI in case that is needed.

Advanced options is if Ubuntu has trouble booting and should have a recover option and an older kernel, if newer one is the issue.

I think mmx is an advanced option for managing UEFI Secure Boot keys. Do not use it. (I do not.)

The Lenovo boot may be to start the recovery process or whatever Lenovo has as its own reinstall/reset process. If that is the Windows recovery, many systems just reset Windows to as installed from factory, all settings & data lost. Another reason for good backups. 
But some are just an update to Windows files,not sure what Lenovo does.

One my one Windows system which is for watching video that cannot be played in Linux, I have UEFI set to boot Windows. And to boot Ubuntu I press f12 as that is key for my Dell to boot into Ubuntu, I then get grub menu also.

---

### Post by krashkitty on 2017-10-10
You've been super helpful, and I've learned a lot I think. I guess I'll just leave the menu this way for now, as it's working, and any more changes might cause more trouble than they're worth. So, do you think it's safe now to do those Windows updates? And set the Ubuntu clock? I think it's working ok, but I'm still really nervous about doing anything else until I'm sure it's safe. I definitely don't want to mess up anything else.

---

### Post by krashkitty on 2017-10-10
I went ahead and did the updates, as well as the Ubuntu updates. Everything seems to still be in working order.  Thank you so much for all your help. One last question, if anything does go wrong, can the backup I made yesterday undo all the changes, even the part where I shrunk something to make room for Linux? I'm thinking of keeping that backup and ordering a new USB stick to make a second backup, so that there will be one that can undo everything if necessary.

---

### Post by oldfred on 2017-10-10
The old way of backups was grandfather, son, & child or three copies in rotation.
Now with more space available and drives lower in cost users often do more in the way of backups.

With Linux you need to backup /home. I have a very few settings in /etc where I have manually edited something like a grub configuration file, so I just copy those few files into /home so they are backed up. I also export a list of installed applications, so I can reinstall everything almost automatically. I then can re-install Ubuntu, restore /home & update applications. I have reinstalled and in effect restored multiple times, so know process which makes it easier.

With image type backup, it is obsolete as soon as you use system. But you can still backup your data which usually is the most important part. Now sure of details of Windows anymore.

---

### Post by krashkitty on 2017-10-10
Ok great. I'll back up everything & do some research on the Windows aspect of it. Again, thank you. I really appreciate all your help.

---

### Post by oldfred on 2017-10-11
If it is working ok, you can change to solved.
And if new issues start a new thread with that issue in title.

---

