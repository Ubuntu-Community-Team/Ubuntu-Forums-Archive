---
title: "Fresh install 10.4 and screen locks up after Gnome log in - only failsafe works"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by rj)pete on 2010-11-06
I'm hoping someone can point me in the right direction or at least confirm my suspicions.    

I picked up an older AMD Athlon machine to use as a CNC box to control a CNC machine I am in the process of building.  


I went through the LinuxCNC.org site and downloaded their bundled Ubuntu 10.4/EMC software and have installed it (many times over the last week actually).  After the last install, I did a software update in GRUB recovery mode as well.    


No matter what I try, it locks up within about 5-10 seconds after a regular Gnome session login with only the desktop background image displayed (although I notice the hard drive light is flashing sporadically).    


I can login in with a Gnome failsafe session (and xterm too) although I can't get my wireless network card (no Network Manager in top right) to work and I get default 800x600(60Hz refresh) video.    


I can also start the machine in recovery mode (hold down shift on bootup gets me to GRUB menu, select recovery mode and then failsafe graphics from a later menu) and then login with a regular Gnome session.  This allows my wireless network card to work (which allowed me to run the software update) and Network Manager is there but my video is still limited to 800x600.    


My current suspicion is that xserver/x.org (sorry, I'm not super familiar with the concepts in ubuntu/linux yet) is gagging on my video card.  I can't find anything in the log files to tell me anything useful although I'm not sure what I'm looking for so I could have missed it.    


If I do an lspci or an lshw command, it identifies the video card correctly and the machine seems to be using the MGA driver but in either failsafe or recovery mode it is limited to 800x600.    



I have tried adding nomodeset in the /etc/default/grub file (with a sudo update-grub after) to no avail.  I also tried adding an xorg.conf file (it didn't exist which I understand is now normal for 10.04) but that didn't help.    


I also tried downloading the Matrox drivers from their website but when I try to install (boy, are their supplied instructions cryptic!) it tells me my version of xserver is not supported.    



Here's the hardware details in case that helps:    

Asus A7V8x-x motherboard with an AMD Athlon XP2500+ processor running at 1.83Ghz with 1GB memory installed    

Video Card is a Matrox Millenium G550 AGP  hooked to a beater IBM/Lenovo Think Vision Monitor (max 1280x1024/75Hz).     


Probably irrelevant but just in case, the HD is a Maxtor 40GB IDE, the wireless card is a TP-Link TL-WN350GD and the optical drive is a TSST Corp CD/DVD RW SH-222A     


BTW, I have also tried installing Ubuntu directly from the Ubuntu website 10.4.1 download with the same result (as far as I can tell, I haven't tried all modes) and I even tried to install kubuntu which seemed to work but still 800x600 video and no wireless.  The KDE interface seemed to be just different enough from Gnome to be confusing me in trying to troubleshoot so I bailed on that and reinstalled Ubuntu.     


I have been googling the net and searching this forum and I can't seem to find anything definitive.  The MGA driver is supposed to support the Matrox G550 as far as I can tell but ????  Sorry for being so verbose but I'm really hoping someone can enlighten me on what to look for to nail down this problem.   


 BTW, I used to work in IT many years ago (and have dealt with various Unix systems) but these days I'm a Mac user and really rusty at the nuts and bolts of computer hardware so be gentle with your advice. ;-)    
Thanks, Ray

---

### Post by rj)pete on 2010-11-06
So I've made some progress.  After posting my thread, I went back into the forums to double check my post went up ok (it was my first thread and I was having problems getting the carriage returns recogized as preview kept displaying my nicely formatted post as one big block of text).

Anyways I found this new thread:
[http://ubuntuforums.org/showthread.php?t=1615178](http://ubuntuforums.org/showthread.php?t=1615178)

Which led me to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520)

I did a google search on "xorg.conf server flags section aiglx" and found this: 
[http://www.gentoo-wiki.info/AIGLX](http://www.gentoo-wiki.info/AIGLX)

It seems that my Matrox g550 is not supported by AIGLX so I added to my /etc/X11/xorg.conf file the following (from the replies in the bug report):

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

I can now login with a normal Gnome session although I am still restricted to 800x600.  I would prefer to have the higher resolution that my monitor and video card should be capable of so if anybody has any ideas on that I'd be greatful.

Thanks,
Ray

---

### Post by rj)pete on 2010-11-08
Ok, so I fixed my resolution problem.  I'm going to document what I did here as much for myself as for it's usefulness to others.

I'm fairly new to linux and ubuntu so it's been a bit of a struggle to know where to look for error messages, commands, etc. but eventually I noticed that there was an xorg log in the log viewer.  In there I found a number of messages suggesting things like 'hsync out of range'.

I also took a closer look at the example xorg.conf file example I had found in another thread (for a similar video card and problem) and realized that it was specifying different resolution options than what I actually needed.  

Basically, it seemed that the mga driver included in xorg/xserver was not able to get the correct specifications from the video card even though the system was correctly able to identify the actual card type.

So now I just needed to figure out how to set the correct options in the xorg.conf file to override the mga drivers bad defaults and see what happens.

Luckily in my googling about this problem I stumbled across the 'gtf' program that is part of xorg/xserver.  This program can take a resolution and refresh rate specification and spit out the appropriate Modeline parameters for the xorg.conf file.

I went into a terminal window and executed:

   gtf 1280 1024 75 -x

and I got the the appropriate Modeline piece (including a comment with details on the hsync rate and pclk rate) I needed and cut and pasted it into the xorg.config file built from the previous sample.

I rebooted and voila!  Now my default resolution is 1284 x 1024 with the correct 75hz refresh rate (the max my old lcd monitor can deal with).

Here's what my /etc/X11/xorg.conf file finally ended up looking like:

Section "ServerFlags"
   Option "AIGLX" "off"
EndSection

Section "Device"
  Identifier "Device0"
  Driver "mga"
  BusID "PCI:1:0:0"
  Option "OldDmaInit" "True"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "Unknown"
  ModelName "Unknown"
  HorizSync 30.0 - 110.0
  VertRefresh 50.0 - 150.0
  Option "DPMS"
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1280x1024_75.00" "1024x768" "800x600" "640x480"
  EndSubSection
EndSection


Note that at one point, I had two different samples of the xorg.conf file to work from and one of them had some extra options after the 'Option "OldDmaInit" "True" ' line in the device section.  these turned out to be invalid (maybe old?) and it initially caused the system to lock up with a blank screen on a boot up.  I ended up starting  in grub recovery mode(holding down the shift key on booting to get to the grub menu) and then selecting the failsafe graphics mode on a subsequent screen.  When I checked the xorg log file in the file viewer it highlighted the offending options so I deleted them and then everything was good.

Now that I have fixed my problem I have since googled setting up an xorg.conf and found the appropriate man page on the xorg site.

[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)

This might be useful for fine tuning the file for those who need to.

Whew!  So now I'm happy that my machine is working without having to use Gnome failsafe mode and at correct resolution.  Hopefully this is useful for others as well.

Ray

---

