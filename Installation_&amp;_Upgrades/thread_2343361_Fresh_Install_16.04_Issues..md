---
title: "Fresh Install 16.04 Issues."
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by Disposition96 on 2016-11-15
I am trying to install a fresh version of Ubuntu 16.04 and get rid of my windows 7.  Unfortunately, I've ran in to an issue I can't seem to overpass...

The first time I loaded up the disk, I verified the disk and everything verified.
The second time I loaded up the disk I booted it in to testing without installing.
I then went to install and everything froze.
I restarted and now I can't boot to the desktop mode or try and install, if I install it just goes in a loop.
I get PCI : Failed to adjust inkctl speed no matter what I try and do.

How do I get around this?

[B]Computer type Laptop 
[B]System Manufacturer/Model Number Samsung 700Z5C 
[B]OS 7 Ultimate x64 
[B]CPU i7-3635QM 
[B]Motherboard Samsung NP700Z5C-S04CA 
[B]Memory 8GB 
[B]Graphics Card HD4000 & GT 640M 
[/B][/B][/B][/B][/B][/B][/B]

---

### Post by Disposition96 on 2016-11-15
[COLOR=#000000]I am trying to install a fresh version of Ubuntu 16.04 and get rid of my windows 7. Unfortunately, I've ran in to an issue I can't seem to overpass...[/COLOR]

[COLOR=#000000]The first time I loaded up the disk, I verified the disk and everything verified.[/COLOR]
[COLOR=#000000]The second time I loaded up the disk I booted it in to testing without installing.[/COLOR]
[COLOR=#000000]I then went to install and everything froze.[/COLOR]
[COLOR=#000000]I restarted and now I can't boot to the desktop mode or try and install, if I install it just goes in a loop.[/COLOR]
[COLOR=#000000]I get PCI : Failed to adjust inkctl speed no matter what I try and do.[/COLOR]

[COLOR=#000000]How do I get around this?[/COLOR]

[B]Computer type Laptop 
[B]System Manufacturer/Model Number Samsung 700Z5C 
[B]OS 7 Ultimate x64 
[B]CPU i7-3635QM 
[B]Motherboard Samsung NP700Z5C-S04CA 
[B]Memory 8GB 
**Graphics Card HD4000 & GT 640M **[/B][/B][/B][/B][/B][/B]

---

### Post by oldfred on 2016-11-15
Did you install in BIOS or UEFI boot mode?

Are you using nomodeset which almost always is needed until you install the nVidia proprietary driver from the repository.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If now only Ubuntu installed, you may need to press Escape key while starting to boot. Maybe more than once to catch the time after UEFI but before grub loads.
If BIOS you hold shift key until grub menu appears.

---

### Post by Disposition96 on 2016-11-15
Sorry I don't quite understand what you mean by which mode, I haven't actually been able to install it at all yet.  So I don't know how to run the BootInfo summary report.

------ This is my complete detailed guide as to what I"m doing at the moment.

When I load from CD at the start of PC boot.

GNU GRUB Version 2.02

*Try Ubuntu without installing.
*Install Ubuntu.
*Oem Install (For Manufaturer)
*Check disk for defects.

If 1. Try Ubuntu without installing.  Then goes to load but flashes :

Nouveau 0000:01:00.0:pci : failed to adjust inklctl speed

Then loads the Ubuntu logo and looks like it is trying to load with the white and red dots going across.

Then loads a prompt that says login : 
However before I can do anything it resets to a completely blank screen

-------

If 2 Install Ubuntu then goes to load but flases :

Nouveau 0000:01:00.0:pci : failed to adjust inklctl speed

and does the same thing.

As a side note, the first time I threw in the CD in and loaded without installing it took me to the actual home screen then it started freezing up.

---

### Post by Geoffrey_Arndt on 2016-11-15
I don't have a dual video system (Intel & Nvidia) - - but I've read those systems are more of a challenge to install any Linux on.   Recommend you research about  "bumblebee" and "nvidia-prime" to overcome that issue.    Perhaps someone on this forum with personal experience will also provide more detail - - but this thread is a start in the right direction.

[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)

---

### Post by QIII on 2016-11-15
Threads merged.

Please do not create duplicate threads.  It waters down the community's efforts to help by doing just what happened.  Different people help in different spots and duplicate effort.

---

### Post by Disposition96 on 2016-11-16
> **Geoffrey_Arndt said:**
> I don't have a dual video system (Intel & Nvidia) - - but I've read those systems are more of a challenge to install any Linux on. Recommend you research about "bumblebee" and "nvidia-prime" to overcome that issue. Perhaps someone on this forum with personal experience will also provide more detail - - but this thread is a start in the right direction.

[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)


So to do this, how do I get it to the point where I can do the first step in terminal?

---

### Post by oldfred on 2016-11-16
Some systems need more than just the nomodeset boot parameter.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

I believe bumblebee is now mostly obsolete. The newest nVidia drivers do switching.
      
 Bumblebee may not be required with nVidia Optimus which is installed automatically with newest nVidia driver.
Bumblebee has been depreciated in favor of nvidia-prime

---

### Post by Disposition96 on 2016-11-17
So I've tried to use that link and managed to get nomodeset checked off but to no avail... it has booted different however...  plus I got it to show me everything once and took pictures.

[http://i.imgur.com/dk3Q9UJ.jpg](http://i.imgur.com/dk3Q9UJ.jpg)
[http://i.imgur.com/5sYYNKF.jpg](http://i.imgur.com/5sYYNKF.jpg)
[http://i.imgur.com/IhjuQln.jpg](http://i.imgur.com/IhjuQln.jpg)
[http://i.imgur.com/sJ0EFV6.jpg](http://i.imgur.com/sJ0EFV6.jpg)

The time I got all of this to come up it booted and then it said internal error, froze and I couldn't click more options. 


Hopefully this can help someone help me.


Edit #1 - 

Played around with the rest of the boot options, I seem to have been able to get it to load and am talking to you now off the CD with nomodeset & edd=on enabled.  

It's running super smooth (for off a cd)

Is there anything extra I can test prior to trying an install with the same features?

Edit #2 -

I've tested it twice now and each time I can load in to ubuntu off the cd with those two things enabled, should be safe to try an install or should  test something else first?

---

### Post by oldfred on 2016-11-17
CD is often good as once loaded you are really running from RAM, just a bit slow in loading first time.

Issues often are common by brand, so even though different models, these may have some solutions to issues.

 Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by Disposition96 on 2016-11-17
I love how series 7 laptops have issues.  Mine is older and only had  windows 7 on it but I've definitely hit a few bumps.  I don't want to  run it off the CD every time, I do actually want to run it off an  install.  If I don't care about dual booting anymore then should I be  safe to just install it and use the two perimeters that I've enabled to  get to the desktop the last two times?   Someone told me that the new  drivers are better than bumble bee now and I just have to use the noboot  first until I install the proprietary drivers?

---

### Post by oldfred on 2016-11-17
I always suggest dual booting or at least making full backup of Windows.
Many users jump into the deep end of the pool and find they cannot swim. They want to play a game that only works in Windows or run some proprietary application. It took me several years to wean myself from Quicken in XP, but decided that Kmymoney was good enough, even if not as good.

And with Ubuntu/Linux it works well the more standard the hardware is. And then you may need boot parameters or live with some minor issues. Depending on what your needs are those minor issues may be major. Some expect perfection, but Windows is far from perfect also.

       Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
The ultimate guide to Linux for Windows users 
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) 
   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by Disposition96 on 2016-11-17
Too late, I just slammed ubuntu on this beast.  I actually looked up games I play on here, the only thing I play is CS:GO anymore and HoN and both have Linux clients.   Aside from that I edit a lot of documents and pdfs which LibreOffice Impress/Calc/Writer seem to do just fine and I believe if they don't I can just download open office.

The only thing I need to figre out how to do now is edit my boot config permenently, presently I have to hold shift at startup and remove nomodeset then ctrl + X and everythign works fine, otherwise I get a login screen loop which I can't get past.

---

### Post by oldfred on 2016-11-17
What video was it?
Or did you have Boot-Repair add nomodeset to grub's config file?

The recovery mode has nomodeset by default but standard boot should normally just have quiet splash.

 sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

After any edits:
sudo update-grub

---

### Post by Disposition96 on 2016-11-17
That fixed it, 

GRUB_CMD_LINUX



[LIST]
[*]Entries on this  are added to the end of the 'linux'  command  (GRUB legacy's "kernel" ) for both normal and recovery modes.  It is used to pass options to the kernel.
[/LIST]

On this line, there was nomodeset, I think it was there because I had to load with it using the disk so it passively put it there during the install as I installed via the disk.

Aside from a few other threads I have going now, the OS itself is running flawlessly, I thank you for your help sir. :-)

---

