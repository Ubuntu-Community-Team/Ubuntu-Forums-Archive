---
title: "Can't get any bootable USB progam to work"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by danbuter on 2016-05-01
Currently on Win7-64. Tried using all of the recommended USB bootable programs to make a USB drive work to install the latest Ubuntu-Mate 64 bit. 

The best result I've gotten is the option to load Ubuntu after selecting the USB drive on restart, but then I get a dead black screen. 

I've used multiple Linux distros on this computer in the past with no issues, but so far, I've had zero luck with 16.04.


------------------
System Information
------------------
Time of this report: 12/7/2015, 09:46:20
       Machine name: PC
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.151019-1254)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.
       System Model: Studio XPS 435MT
               BIOS: Default System BIOS
          Processor: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz (8 CPUs), ~2.7GHz
             Memory: 4096MB RAM
Available OS Memory: 4088MB RAM
          Page File: 1447MB used, 6724MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7601.17514 64bit Unicode

---

### Post by Bucky Ball on 2016-05-01
[Try this]("http://ubuntuforums.org/showthread.php?t=1613132") under the heading 'How to enable kernel options on the livecd (before install)'.

Use 'nomodset' and then 'Try Ubuntu' and see if you get to a desktop ok. If so, double-click the icon on the desktop to install.

---

### Post by danbuter on 2016-05-01
How do I use nomodset while on Win7?

---

### Post by Bucky Ball on 2016-05-01
You don't.

> The best result I've gotten is the option to load Ubuntu after selecting the USB drive on restart ...

If you can get that far, then boot from the Ubuntu install USB and follow the instructions on that thread. :)

---

### Post by danbuter on 2016-05-01
It goes black before I get any real options. Right after I select Ubuntu...

---

### Post by Bucky Ball on 2016-05-01
> **danbuter said:**
> Right after I select Ubuntu...

If you're getting the option to select Ubuntu then there would be a bunch of other options there, too, like 'Try Ubuntu' 'Check disk for defects', etc. Is there? If so, then unsure what you're missing about these instructions from that link which are performed before you get to those options:

> If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom:

Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see this menu:

If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key. You can close the menu with escape key and resume booting by selecting the option “try ubuntu without installing” (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).

If you need to add kernel options not provided by the F6 menu, you can just type them in at the end of the boot options line.

Important: if you select a kernel boot option from the F6 menu and proceed to boot and later install ubuntu, those boot options will NOT be applied to your installation. If you needed nomodeset to get the livecd to boot, you will almost certainly need it again once you reboot in to your fresh install. See below how to set those options on an installed ubuntu. And perhaps click the “affects me too” on this bug report where I request these settings be applied (semi) automatically.

---

### Post by danbuter on 2016-05-01
Actually, it doesn't give me any options like that.

Ah well, I'm not sure why the Linux devs have been making so many poor decisions the last few years. From basic stuff like this to the disasters that were Gnome 3 and KDE 4, it's very frustrating.

---

### Post by RobGoss on 2016-05-01
> **danbuter said:**
> Actually, it doesn't give me any options like that.

Ah well, I'm not sure why the Linux devs have been making so many poor decisions the last few years. From basic stuff like this to the disasters that were Gnome 3 and KDE 4, it's very frustrating. I'll try again in a year and a half when the next LTS is ready.

I'm pretty surprised that Ubuntu, Red Hat, or someone else hasn't made a fix for this so that a new person installing linux for the first time would actually have the distro work. It makes Ubuntu look very bad at their job if the initial install won't even work on a bog standard PC box.

I guess it depends on who's installing Ubuntu, I think Ubuntu has done a great job it's not the dev fault that some people are having a hard time installing it. I use and install Ubuntu all day long with out a hitch. The best thing for people to do is read what it takes to install and run Ubuntu distro's

>  It makes Ubuntu look very bad 

I don't think it does in fact Ubuntu look anything but bad, because let's not forget Linux in FREE so we can't really complain besides Ubuntu has so much more to offer then any other OS out there....

---

### Post by yancek on 2016-05-01
>  			 			It goes black before I get any real options. Right after I select Ubuntu... 		

The link below explains how to get and set options from the Ubuntu installation media. 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ubfan1 on 2016-05-01
Did you hashcheck the downloaded ISO?  The md5sum program is available for Windows, and eliminates the possibility of struggling with strange errors from a bad file.  What video hardware do you have?  That can suggest specific options to get the boot working.  I have found the 16.04 ISO to be pretty hard to get converted into an install media -- even using a 14.04 "Startup Disk Creator" produces a USB which wont boot.  I have used unetbootin in the past on Windows, but not in a few years. The raw block writers like dd seem to be the best bet.  I finally did produce a working 16.04 boot media by booting the ISO off the hard disk, and using that system to write the new media.

---

### Post by Bucky Ball on 2016-05-02
Ok, sounds like you don't need further support but would prefer to share your opinions about Ubuntu, devs, etc now ...

> **danbuter said:**
> I'll try again in a year and a half when the next LTS is ready.

So before this devolves further into a random discussion about the pros and cons of Ubuntu, please mark the thread as solved to help other potential helpers and save them some time. Thanks.

---

### Post by danbuter on 2016-05-03
Went out and bought some DVD-Rs. Using one of them, I got Ubuntu to install. Have no idea why it won't work using a USB.

---

