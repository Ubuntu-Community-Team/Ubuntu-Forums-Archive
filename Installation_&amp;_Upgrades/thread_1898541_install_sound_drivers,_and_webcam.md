---
title: "install sound drivers, and webcam"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by EVILOX on 2011-12-21
Hi
I am new to linux, and especially Ubuntu, and I need help.

I have installed Ubuntu on my office Desktop (HP D530), and it installed pretty easily.  The problem is, I am trying to install sound drivers, and webcam, as well as other software, but when I click on the application icons, nothing happens.  What am I doing wrong?

Thanks

---

### Post by oldos2er on 2011-12-21
Are you clicking these things from within the Software Center, or ? Usually appropriate drivers are installed along with the OS.

Can you give us your hardware specs?

---

### Post by EVILOX on 2011-12-22
I have tried installing via the software centre, but don't see the option.  The drivers and software I want to install is on a disk and a usb.  I have a HP D530 system on which I want to install this software.  I would appreciate maybe a walkthrough or guideline on how to install my sound drivers, webcam, and other software.
Thanks

---

### Post by emmomalick on 2011-12-22
What type of software are you trying to install? 

BTW sound drivers and other hardware drivers are automatically installed in Ubuntu, you have no need to install them manually. Most of the drivers are built into UBUNTU.

Can you go up to the sound icon and make sure that nothing is muted.

I think there's might be a problem of codec. When you try to play a file  a new window appear click on SEARCH button and install all required CODEC from there. OR go to Synaptic Package Manager under SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER install VLC player or search on Ubuntu Software Center for VLC.

END OF PROBLEM.

---

### Post by EVILOX on 2011-12-22
I have no sound at all.  VLC is installed, and the sound settings are fine.  I have tried multiple media types, and still no sound.  I also have to install google chrome, google earth, and my webcam, but it is giving me a message saying that the application is not recognized.

---

### Post by emmomalick on 2011-12-22
Fine. Please let me clear that are you trying to install google chrome, google earth etc from Ubuntu Software Center or trying to run a ".exe" file on Ubuntu.

---

### Post by EVILOX on 2011-12-22
I have tried installing the software using the .exe file, and it says cannot read from source disk.  I then tried using the software centre, but cannot find the installer for the webcam and sound drivers.

I have found that chrome and google earth is available in the software centre, so that issue is solved.  The main thing is to install the drivers.

---

### Post by emmomalick on 2011-12-22
.exe files are not capable to run in Ubuntu. Because they are not designed for Linux.

Exe files do contain object code, but it is still dependent on the  operating system to do certain things when loading the program into  memory.  First off Windows uses the "PE" format for object code  (ironically the P stands for portable).  Linux now uses the Elf format,  it used to use one called Coff.

Ubuntu has its own formats to run the programs e.g .deb , .rpm etc. All softwares like Google Chrome, Photo Editor etc are available in Software Center, You can install them from there. 

Another way to run .exe files in Ubuntu is through WINE. But i don't think so that it works fine like it is in Windows. You can see here for more

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

For your Webcam, i suggest you to install CHEESE from Ubuntu Software Center, it might automatically install the drivers. If not then post here the results.

And also take a look at the Hardware Drivers under System > Administration > Hardware Drivers, it allows you to enable your graphic card drivers for 3d acceleration. Activate the (CURRENT RECOMMENDED) drivers from there if available.

---

