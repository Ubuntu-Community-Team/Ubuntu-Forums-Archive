---
title: "Duel Booting W8 with Ubuntu 12.10 64bit problem"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by NanoSkill on 2013-03-16
[COLOR=#000000]Hello [/COLOR]

[COLOR=#000000]I recently upgraded my os from w7 to w8 after my old hdd died, which had ubuntu duel booting on it.Once i had updated my windows os i decided to get go for ubuntu and start to get into programming again. I booted a 64 bit version of ubuntu 12.10 with two usb's and countless disks but every time i do it brings me to two black screens. [/COLOR]

[COLOR=#000000]The first one was easily by passable with the f12 skip step and the nomonde set because i remembered doing that for windows 7 but when i choose either in install ubuntu or try it it goes into the menu with the 4 dots but then it goes into a command prompt and runs some scripts then nothing, all I get is a back lit black screen, no courser in the corner no splash text that is left over, just nothing[/COLOR]

[COLOR=#000000]I have searched over the internet for solutions but every thing i can find is uefi boot options for w8 but the laptop that I am installing it on was made in 2011 and i installed windows 8 myself it wasn't a pre install. I am not sure what it is i currently have a NIVIDIA GT 520 running on this machine which i suspect is the problem because i know nividia has problems with having linux installed but i have heard that having 2 cards can make it worse since there is also the Intel graphics card as well[/COLOR]

[COLOR=#000000]Here is a list of my system specs[/COLOR]



[COLOR=#000000]Operating System: Windows 8 Pro 64-bit (6.2, Build 9200) (9200.win8_gdr.130108-1504)[/COLOR]
[COLOR=#000000]Language: English (Regional Setting: English)[/COLOR]
[COLOR=#000000]System Manufacturer: Acer[/COLOR]
[COLOR=#000000]System Model: Aspire 5750G[/COLOR]
[COLOR=#000000]BIOS: InsydeH2O Version V1.05[/COLOR]
[COLOR=#000000]Processor: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz (4 CPUs), ~2.3GHz[/COLOR]
[COLOR=#000000]Memory: 16384MB RAM[/COLOR]
[COLOR=#000000]Available OS Memory: 16236MB RAM[/COLOR]
[COLOR=#000000]Page File: 2611MB used, 19256MB available[/COLOR]
[COLOR=#000000]Windows Dir: C:\WINDOWS[/COLOR]
[COLOR=#000000]DirectX Version: DirectX 11[/COLOR]
[COLOR=#000000]DX Setup Parameters: Not found[/COLOR]
[COLOR=#000000]User DPI Setting: Using System DPI[/COLOR]
[COLOR=#000000]System DPI Setting: 96 DPI (100 percent)[/COLOR]
[COLOR=#000000]DWM DPI Scaling: Disabled[/COLOR]
[COLOR=#000000]DxDiag Version: 6.02.9200.16384 64bit Unicode[/COLOR]

[COLOR=#000000]as well as Nividia GT 520M graphics card [/COLOR]
[COLOR=#000000]and Intel(R) HD Graphics 3000[/COLOR]

---

### Post by meteorrock on 2013-03-16
Your computers specs are good enough to use what we kids call a "hypervisor." I am checking over both "virtualbox" and "Vmware workstation 9.0.1" right at the moment using 64 bit Windows 7 as my host OS.  Using a hypervisor is a good workaround for having to set up drivers in linux. The switch to both OS is almost instantaneous on a hypervisor right now. Glad you have you looking into development again. Come hone your skills on our project over in the XDA nook color forums if you like. :)   Virtualbox is free for use, but takes a tad more work to set up. I show you how in my blog thread post below.  Check the last box I added in that thread for "virtualbox" setup. 

Just install your hypervisor on your Windows 7 or Windows 8 OS , it works good for me on both OS. Your native OS will be called your "host" OS and your ubuntu distro you are looking over will be your guest OS. Here is a blog of mine on how hypervisors work and the codes needed for a quick setup.  [http://forum.cyanogenmod.org/topic/50994-follow-along-with-me-trying-to-learn-how-to-code/page__st__40](http://forum.cyanogenmod.org/topic/50994-follow-along-with-me-trying-to-learn-how-to-code/page__st__40)

Using these "software" hypervisors as they call them makes it a LOT faster switching between OSes for the developer like yourself. Doing porting work between OSes this is the route you will want to go IMHO. You can even drag and drop files between those OSes.

~~~~~~~~~~~~~~~

 Your hypervisor will use a "passthrough" for all of your hardware drivers for your linux or ubuntu distro. It will piggyback the drivers already installed on your Windows OS to the virtualization to your ubuntu distro for more troubleshooting on your drivers. These hypervisors are near native in performace and run great with few bugs, and your computers specs should work well for virtualization. 

 After you have got your linux distro up and running in virtualization, and you decide you rather have dual boot on your computer for just that little extra performance on your linux distro, you can save that virtual disk that was created through these hypervisors and use that with the drivers up and running correctly in them. 

If these solution is not viable for you, let the forum know for additional help. :)

---

### Post by NanoSkill on 2013-03-16
Thanks ill have a look at your project to :D

---

### Post by oldfred on 2013-03-16
I only have nVidia and have to use nomodeset. But you have dual video and have issues.

 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

