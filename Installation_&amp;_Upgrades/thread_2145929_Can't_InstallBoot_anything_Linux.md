---
title: "Can't Install/Boot anything Linux?"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by Evilhugbear on 2013-05-16
Hey guys,

I currently have Win8 and Win7 in a dual boot, and wanted to try out Elementary OS. So, I downloaded it, burned it, and tried to install it. I got a udevd timeout error. I thought "maybe it's a bad burn or download." So, I redownloaded, burned, and attempted to install. Same error. I tried a bootable USB drive. Same error.

So, I tried Linux Mint. I did similar things with Mint, and got a udevd timeout error every time.

So, I tried Ubuntu. Same thing.

So, I tried to start gParted to wipe the hard drive to see if that would affect anything. That wouldn't even boot.

So, I have no idea what's wrong, and was hoping you guys could shed some light. I've searched and searched, and all the other threads are all unsolved.

I could get some pictures of the errors tomorrow, if that could help.

Thanks :D

BTW: Forgot to mention this is with a UEFI motherboard, and all OS's were 64-bit

---

### Post by Evilhugbear on 2013-05-17
Does anyone have some insight into this?

---

### Post by oldfred on 2013-05-17
Are Windows in UEFI or BIOS mode? Or really MBR(msdos) or gpt partitioning.
Are both copies of Windows in primary partitions.
Did you create partitions in Windows and it converted to dynamic partitions that do not work with Linux and maybe not all Windows repair tools?

Since UEFI did you boot Ubuntu installer in the same mode as you have installed Windows, either UEFI mode or BIOS/CSM/Legacy mode. How you boot installer is how it installs. But both Windows and Ubuntu have to boot in the same boot mode.

Post this from terminal in live Installer:
  sudo parted /dev/sda unit s print

---

### Post by Evilhugbear on 2013-05-17
> Are Windows in UEFI or BIOS mode? Or really MBR(msdos) or gpt partitioning.
I'm not sure. How can I check this?
> Are both copies of Windows in primary partitions.
Yes, they are.
> Did you create partitions in Windows and it converted to dynamic partitions that do not work with Linux and maybe not all Windows repair tools?
I'm not sure. Disk Management in Windows 7 doesn't mention dynamic partitions, so I guess not.
> Since UEFI did you boot Ubuntu installer in the same mode as you have installed Windows, either UEFI mode or BIOS/CSM/Legacy mode. How you boot installer is how it installs. But both Windows and Ubuntu have to boot in the same boot mode.
I didn't boot them any specific way, I just put the DVDs in and tried to install. (Same with Windows and Linux)
However, I did try Auto, disable Legacy, and disable UEFI in my motherboard's UEFI. I'll try those again just in case.
> Post this from terminal in live Installer:
  sudo parted /dev/sda unit s print

I can't even get into the live installer :(. The menu comes up to select what you want to do, and I select install, and then it times out.

[Here's]("http://i.imgur.com/dmHsZlI.png") a picture of Disk Management. C: is Windows 7, my main OS, and F: is Windows 8, which I installed second and plan to overwrite with Linux.

---

### Post by Evilhugbear on 2013-05-17
I just tried booting after disabling Legacy boot, and it didn't detect anything to boot. So I guess they are in Legacy mode.

---

### Post by oldfred on 2013-05-17
You have the standard 100MB boot/repair partition that is part of BIOS/MBR installs. You may have your Windows 8 boot files in the boot partition if you installed that last. Make sure you make a Windows repair CD or flash in case you have to fix Windows after uninstalling 8.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Of course backups are always a good idea.
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Your partitions say basic so dynamic is not the issue. Were drives ever RAID? Or was drive ever gpt? Both of those leave meta-data that causes issues as Linux sees that extra data and is not sure if it should be used or not.

---

### Post by Evilhugbear on 2013-05-17
I did try RAID once before, but it caused problems so I got rid of it. They aren't currently in RAID. How do I delete the meta-data?

---

### Post by Evilhugbear on 2013-05-17
I just tried installing Ubuntu 13.04 64-bit via DVD again, and this time it got to the live ubuntu desktop! However, soon a window popped up and said program problem detected, and I clicked report. Then, it cut to a command line screen, and kept giving errors. I mentioned nouveau over and over, and from what I can tell it has to do with nVidia drivers?

So Elementary and Mint have udevd timeout errors, and Ubuntu has nouvea errors? I have a Gigabyte GTX 670, are there known problems with it?

EDIT: [Here]("http://imgur.com/7JV9UaT") is a pic of the screen I forgot to link :P

---

### Post by oldfred on 2013-05-17
I have an older nVidia card and have to use nomodeset. But as soon I as boot my install, I install the proprietary nVidia drivers.
I have installed from system settings, some versions have just an icon for Addl drivers. The newest have drivers as a tab under Software and Updates.
And I have installed from command line.

If you can boot install the nVidia drivers. If not try recovery mode which may work or give an option to go to command line which you can use to install the proprietary drivers.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

There are several versions you can install.

 #To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

---

