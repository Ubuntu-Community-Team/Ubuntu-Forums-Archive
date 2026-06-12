---
title: "HP Pavilion 15 - Ubuntu 14.04 - Driver Issues - Low Graphics Mode -"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by alistair3 on 2014-05-20
Hi, long time reader, first time poster. 

First, i've had Ubuntu 14.04 on this machine before working fine but i can't seem to do it again.  The machine originally came with Windows 8.1, but doing any type of development on a Windows system is just terrible, it's bad enough at work ! So i've decided to wipe the Windows system completely and run 14.04 LTS for the next few years.

Specs.
The machine is a HP Pavilion 15.  
AMD Fmaily 15h (Models 10h-1fh) Processor Root Complex.  
AMD/ATI Trinity [Radeon HD 7640G]

Problem in order....
1.  Machine fast-boot is off, UEFI is off,  legacy boot is enabled though.
2.  Format USB stick, copy iso 14.04LTS with unetbootin & boot.
3.  System Boot's up with GRUB, 2.02~beta2-9.  Gives 4 options.  Try Ubuntu, Install Ubuntu, OEM install, Check for Disk Defects.

4.  If i click on "Try Ubuntu without Installing" 
      1. Black screen for 5 seconds or so.
      2.  Ubuntu loading screen now shows up.
      3.  Pop-up saying "system running in low graphics mode"
      4.  Click "ok" getting given another screen saying "what would you like to do?", which gives four options, none of which work.
      5.  Note that i can still cntrl-alt-f1 and drop into a terminal.

5.  If i click on "Install Ubuntu"
      1.  Black screen for 5 seconds or so.
      2.  Ubuntu loading screen.
      3.  Get taken to graphical installer, works like a charm and the system installs successfully.  
      4.  Reboot and remove the USB stick.

6.  System Boots
      1.  Blank screen with purple border -- no boot loader ?
      2.  Get an Error "Radeon cannot find backlight controller" <-- or something like that, screen is very quick and can't see what is says exactly.
      3.  System pop-up "system running in low graphics mode"
      4.  Cant cntr-alt-f1 and get a terminal where i can log in and see the system has installed correctly.

Else:
I've basically tried everything i could find on the net about this, trawling through forums.  Including this article which i thought would help, but unfortuantely didn't. 
[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

I've also tried to read all of the HP bugs i could find, with still no luck. 
When the system boots, i don't get GRUB, i've got a sneaking suspicion i might have to drop to a terminal and use "boot-repair" but i'm not sure you can use that tool from the command line, since i cant get any GUI's working on 14.04.

I'm hoping someone out there can help.  Regardless if you can or not, thanks for taking the time to reading -- long post -- hope its set out alright.
Kind regards.
alistair.

---

### Post by mastablasta on 2014-05-21
> **alistair3 said:**
> 1. Blank screen with purple border -- no boot loader ?
yup, you need to hold shift key to get the boot menu. windows also never boots to boot menu by dafault.

> 
2. Get an Error "Radeon cannot find backlight controller" <-- or something like that, screen is very quick and can't see what is says exactly.
.

For 14.04 there is a kernel parameter that can be used with radeon drivers to get this working. check the ubuntu boot options section of the wiki [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
and radeon driver section.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
--

An easier option might be to install proprietary AMD drivers. Open additional drivers application, select AMD drivers and click install.


---

---

