---
title: "Trouble installing Ubuntu 13.10 on my HP Pavilion g6-1d85nr Laptop PC"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by dorlancrazyrocker on 2013-12-01
[FONT=microsoft sans serif]Hey guys, I'm pretty new on the Ubuntu thing and I'm very curious about it's OS. I have been trying to install Ubuntu a few months ago and it's just not working on my PC! I burn a DVD with the Ubuntu 13.04 [64-bits] a couple months ago, and recently the 13.10 [32-bit] version... none of them works. I don't understand well how Ubuntu functions but I do know how to install OS (I installed Windows 8/8.1 Preview and 8.1 Pro) directly from BIOS with no problems. When I run the Ubuntu DVD from the BIOS, it shows the Welcome Screen saying "Ubuntu" and a graphical design under it (like a normal loading). The problem is, at some point the installation crashes and doesn't respond at all, not even "ESC" button works, so the only way to quit it's by force shutdown. I tried several times and the same issue goes on, sometimes crashes after appearing a cursor on the menu and sometimes it doesn't even appear. The strange thing is when at some point on installation the screen goes black, like it disappears the Welcome screen and then reappears. I don't know it has to do with my graphics card but it's a pretty generic one so I don't know. My PC specs are:
- CPU: AMD A4-3305M APU with Radeon(tm) HD Graphics [64-bit compatible] (has dual core processor with 1.9GHz clock)
- GPU: AMD Radeon(tm) HD 6480G (512MB of memory)
- HDD: TOSHIBA MQ01ABD050 ATA Device [500 GB]
- OS: Windows 8.1 Pro and a second partition with Windows 8.1 Preview. (Before it was only Windows 8 Pro, came with preinstalled Windows 7 Home Edition)
* I doesn't have UEFI just BIOS boot.
* All drivers are already updated, for AMD CPU/GPU I'm using Catalyst driver.

I hope you have enough info for helping me resolve the issue, as I said I'm pretty new on Ubuntu (and the forums too) so don't expect me high knowledge on the OS, only I understand mostly Windows.
Thanks in advance and sorry this is so long!!! ;) 
[/FONT]

---

### Post by fantab on 2013-12-01
Have you disabled [FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8?

The kind of error you describe sounds like a Graphic Card related. You can Try [**NOMODESET**]("http://ubuntuforums.org/showthread.php?t=1613132") option at Ubuntu DVD boot.
If the DVD boots then "Try Ubuntu Without installing", open Terminal [ctrl + alt + t], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by dorlancrazyrocker on 2013-12-01
I have disabled the FastStartup feature on both Windows 8.1 I have installed... as for the NOMODEST thing I will do that right now! I will reply later with the results!!! :)

EDIT: I did the NOMODEST thing and the install were successful... thanks a lot for your help! Already enjoying the Ubuntu experience. ^^

---

