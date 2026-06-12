---
title: "Ubuntu 11.10 only boots into Windows"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by jgiesler on 2011-10-17
I just installed Ubuntu 11.10 from disc and when i restarted it I dont get the option between Ubuntu and Windows.

Rather, it just boots into Windows.

Did Grub just not install or what?

Don't know what else to say.

Please help and will provide any additional info if needed.

---

### Post by JobTaker on 2011-10-17
Hello,

I am having the same problem, I have a Lenovo V570 ( Core i5-2310M 8GB of RAM and a SATA III (6Gb/s)) using a Crucial 64GB M4 SSD. Same problem. I have tried another SSD, same brand larger but got nothing also. The computers SATA controller is set to AHCI, but I have tried via IDE/Compatibility mode too. It seems as if the boot loader is not read or installed, I installed via a USB drive from a x64 version of 11.10 desktop.

---

### Post by oldfred on 2011-10-18
@jgiesler
Please post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or download and run this program which also runs boot script and may repair system.

Yanni has created a easy way to download boot repair:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

@JobTaker
You need to do same but it gets too confusing to have one thread with two different boot issues. Please start a new thread and post the boot script.

---

### Post by otoolerc on 2011-10-18
@oldfred
 
> **jgiesler said:**
> 
Rather, it just boots into Windows.
 
 
Don't know what else to say.

 
... Pretty sure that the Boot Info Script is irrelevant here, as terminals aren't available to those who cannot run Ubuntu...
 
... I may be wrong...?

---

### Post by otoolerc on 2011-10-18
And also to add, I am having the same problem as the thread starter.
 
As simple as it gets: Turn on computer, Windows 7 boot loader presents me with my options:
 
Windows 7
 
Enter, or Esc.
 
No Ubuntu option.

---

### Post by sfBlackfox on 2011-10-18
Did you used to used to login by Windows Boot loader ? 

If not, just insert the live cd and reinstall grub2?

---

### Post by oldfred on 2011-10-18
You can run script from Ubuntu liveCD or download this:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You should have a liveCD or repairCD for every system installed. You should make the Windows repairCD if you have not.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by JCoop on 2011-11-01
Not sure if you already figured this out, but I had the same problem and was able to fix it. 

First, I want to point out what doesnt work as this caused me a lot of headache. My system is Lenovo V570 with intel graphics 3000 and 64 bit Windows plus 64 bit Ubuntu. MBR partition, Windows, Ubuntu, swap area. I tried about 3 new installs(putting the Grub/MBR on every partition to no avail I might add) before I found the correct way listed below so enjoy.

1. For some reason the live cd does not let you see the boot options. It will also not let you select them if you try and guess where each option should be. I tried to make another cd, but that didnt work either. So, after selecting the first option, you boot into ubuntu live cd mode and install. Just do everything like you would normally do it. GRUB will not work but whatever, just do it.

2. After the initial disappointment of booting directly into Windows after restart, go ahead and make your way to this link:
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

It will allow you to make a SuperGrub 2 boot disk. THe reason for this is because I learned the hard way that any changes you make to Ubuntu using the live cd apparently dont actually change the main system. So all of the helpful advice about trying to install Grub from this point is pretty well useless. Anyways, burn it, restart, and select option 1 I believe, which should be boot into existing Linux OS, or something to that effect.

Again, for some reason trying to do the recovery mode or any other thing with the live disk and even some options with the Grub Disk, you will probably get an unreadable menu. That makes this pretty much the only way that works. If you dont believe me, please try it for yourself. If you follow my instructions though, you will save about 12 frustrated hours. 

What to do:

When Ubuntu boots up you will be tempted to just use the Grub Disk for the rest of your life instead of messing with anything ever again. God knows I was. The good news is you are only a few steps away. 

Go to the software center and download Boot-Repair. Once you have it installed, open it and select the advanced options tab on the left hand side. You are looking for the option that says something like purge and re-install Grub. Do this. Unfortunately, I am writing this from Windows like an idiot so there may be another option I am forgetting.I will edit this post if that is the case though. That should be it though. You will then be taken through a list of options as it purges Grub and re-installs it.

***This is Critical**** Boot-Repair tells you which answers to select from the options. Make sure you select those options. Also, make sure you select the default partition to install Grub. Whichever partition it has listed first, go with that. After you do all of this, if you were having anything like the time I was, you will probably be thinking that your system is just going to boot back into Windows... but guess what? It should work perfectly now!

One thing I wasnt able to solve was how to repair the menu options for the live cd or for Grub recovery mode. Neither worked  with either of the cd's I tried (both were 64-bit. I had heard that the 32-bit cd's menus do work). Also, if you have the same model computer as me (or just an intel centrino wireless N card), you can get your wireless working by following this link:
 [http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/)

Be sure to restart afterwords for the wireless adapter to be recognized.

This is actually my first post to a forum... like ever, so I'm sorry if I miss any of the typical conventions or what have you. I just spent a ridiculous amount of time working on this before I figured it out and wanted to try and help others. If you think this method translates to other computers, please feel free to reproduce these instructions somewhere else where they may be more useful, as I am not really sure how to do that. Thanks!

---

