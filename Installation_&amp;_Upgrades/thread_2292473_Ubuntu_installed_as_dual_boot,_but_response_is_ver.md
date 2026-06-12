---
title: "Ubuntu installed as dual boot, but response is very slow; other system works fine"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by Old_Printer on 2015-08-28
I installed Ubuntu on my Internet computer, installing it as a dual boot system when the installation failed for Ubuntu to be the only system on the machine. This way I can still get on the Internet, which I'm doing right now on XP.

As a dual boot, Ubuntu 14.04 finally took hold and it's loaded. No errors or critical warnings. When it rebooted after the install, and reaches the desktop, it crawls very slowly. I opened a window just to see the response. It opened slowly, and when I clicked on the window header to move it, it moved in jerks -- similar to what I've seen over the years when a video driver isn't installed.

The computer is a NetVista, which originally came with XP. Do I need to adjust anything in the BIOS video settings for Ubuntu to be able to run smoothly on this system?

As a note, this particular computer is fussy. I can't get an aftermarket video card to work on it, so I'm stuck with the on-board graphics -- for now, until I can solve the issue. I have others like this, and they're super machines. This computer is an exception.

Any help would be greatly appreciated.

Old_Printer

---

### Post by yancek on 2015-08-28
You do know that xp hasn't been supported for some time and is risky to use on the internet.  That being said, if the computer came with xp installed, the first thing you need to do is to compare the hardware you are using with the minimum hardware requirements for Ubuntu.  If your hardware doesn't meet the minimums or exceed, you may be better off trying a lighter distribution such as Xubuntu or Lubuntu or googling light distributions of Linux.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by CantankRus on 2015-08-28
You can install inxi (sysinfo script) to show some system details.
```
sudo apt-get install inxi
```

Then post the output of the terminal command...
```
inxi -b
```

---

### Post by Old_Printer on 2015-08-28
@yancek Yes, I know that XP is no longer supported, but it gets me online. I have a half dozen ghost copies to restore the drive in minutes if something happens. O:)

@CantankRus Okay, I tried to install inxi, but here's what was returned:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package inxi


I don't know anymore than that. Maybe this machine just won't do it.

Old_Printer

---

### Post by CantankRus on 2015-08-28
May have to enable the universe repo.
In terminal...
```
software-properties-gtk
```
[ATTACH=CONFIG]264089[/ATTACH]

After the change, when closing it will prompt to reload...do so.
Then try to install again.

---

### Post by Old_Printer on 2015-08-28
Here's what I ended up with, CantankRus. Can you tell by this if the computer is compatible with this version of Ubuntu?

> System:    Host: *****-***** Kernel: 3.16.0-30-generic i686 (32 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty

Machine:   System: IBM product: 830521U
           Mobo: IBM model: IBM Bios: IBM version: 24KT55AUS date: 05/10/2005


CPU:       Single core Intel Pentium 4 CPU (-UP-) clocked at 1993.713 MHz 


Graphics:  Card: Intel 82845G/GL[Brookdale-G]/GE Integrated Graphics Device 
           X.Org: 1.16.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@59.9hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.5, 128 bits) GLX Version: 3.0 Mesa 10.3.2


Network:   Card-1: Intel 82801DB PRO/100 VE (LOM) Ethernet Controller driver: e100 
           Card-2: Belkin F6D4050 N150 Enhanced Wireless Network Adapter v2000 [Ralink 
RT3070] driver: rt2800usb 


Drives:    HDD Total Size: 40.1GB (8.4% used)


Info:      Processes: 155 Uptime: 2 min Memory: 355.9/2018.1MB Client: Shell (bash) inxi: 1.9.17 

Old_Printer

---

### Post by Old_Printer on 2015-08-28
I just remembered something else about this NetVista. If I try to watch a YouTube video, it's jerky and won't play smoothly. It does this regardless of what browser I use. Other than that, everything works great on it, I just can't get Ubuntu to move faster than a snail and I can't watch YouTube videos -- or any videos, for that matter.

Old_Printer

---

### Post by oldfred on 2015-08-28
My Toshiba laptop Core2 Duo with 1.5GB RAM and Intel video was one of the last XP machines before Vista. But then vendors went back and allowed Vista machines to be changed to XP.

But if I install full Ubuntu, it is so slow as to be unusable. But since I wanted same version as Desktop I still installed Ubuntu but then changed Desktop/Gui to fallback or gnome-panel. That was the old gnome2 look with top and bottom panels. But is much lighter weight than Unity. 
Or you can try Lubuntu or Xubuntu.

You can test with this,
       sudo apt-get install gnome-panel

Reboot or restart gui by logging in & out and on login screen use icon in upper right to choose which desktop you want to use.
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

 Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)
How to choose Display manager sessions -  by kanasnoob 
[URL="http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682"]http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[/URL]

---

### Post by Old_Printer on 2015-08-28
@oldfred -- Thanks! I'm now using Metacity and everything is working smoothly.

So, what is it about Ubuntu's 14.04 GUI that won't work on a powerful IBM like this one? This computer has always been as solid as a rock. I have had Windows 7 on it in the past and it handles that without any problems, but I've always been stuck using the integrated video.

I'm going to check out the links that you posted. At least I can be on here with Ubuntu. It's kind of weird showing up here with Windows.

@CantankRus -- Thanks for your help as well.

Old_Printer

---

### Post by oldfred on 2015-08-28
Full Ubuntu with all the bells & whistles needs a modern system or 2GB or more of RAM and decent video card/chip in last 5 years or so. Or very high end if older.

The lighter weight flavors/versions then are for older systems or those who just do not want Unity. Lots of choices.

Look at the posts by kansasnoob on various settings with fallback. I implemented most of them as it made it better.

Full Ubuntu with Unity now really needs 64 bit system also. And I have wondered why they still offered 32 bit install with Unity as  not many systems exist that could use it. Then I saw a recent post where with 16.04 they may effectively discontinue 32 bit. It will still be available, but not fully tested nor as fully maintained. And you will have to search to find it.
But users needing 32 bit should be using Lubuntu or Xubuntu anyway.

---

### Post by Old_Printer on 2015-08-28
I'm downloading Xubuntu right now. I'll give that a try. Thanks for the links. I'll mark this thread as being solved.

Old_Printer

---

