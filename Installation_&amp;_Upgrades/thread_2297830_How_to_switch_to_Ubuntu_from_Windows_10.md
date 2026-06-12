---
title: "How to switch to Ubuntu from Windows 10?"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by noise2 on 2015-10-06
Hey there. I want to start using Ubuntu, but I'm not entirely sure how to install it with Windows 10 and all. Would it be any different from Windows 8, or?
Totally new to this, if it isn't obvious.

---

### Post by yancek on 2015-10-06
You can download Ubuntu and burn it as an image to a DVD or use software such as unetbootin, pendrivelinux and others to create a bootable flash drive of Ubuntu.  That would give the opportunity to run it to test it before installing.  One possible complication with windows 8 and 10 is that they generally use GPT/UEFI to boot so if you install Ubuntu, you would need to install it using UEFI.

---

### Post by oldfred on 2015-10-07
Windows 10 install should be identical to Windows 8.
If vendor provided or update from Windows 8 then it is UEFI with gpt partitioning.
If you installed yourself or upgraded from Windows 7 it may be BIOS with MBR partitioning.

Either way you have to make sure Windows fast startup is off if you want to dual boot.
Best to shrink Windows NTFS only with Windows own tools to make room for Ubuntu and reboot immediately as Windows has to run chkdsk after any size change.

Make good backups of Windows, and all your data. 
Make a Windows repairCD or flash drive, if you do not have the Windows install media. You may have to make Windows repairs.
Both of above required, even if not installing Ubuntu as hard drives fail and Windows may need repairs.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html

[/URL] Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]
[/URL]

---

### Post by noise2 on 2015-10-07
Okay, cool. Got a new (Windows 8) computer a few months ago, right before the launch of 10, so when that came out I decided to test it in hopes that I'd actually like it... I didn't... Waited more than a month to try and revert back, sorta screwed myself over in that regard. 
Anyway, I was worried it would be drastically different and I couldn't install Ubuntu without major complications.
Both of you were super helpful, thanks!

---

