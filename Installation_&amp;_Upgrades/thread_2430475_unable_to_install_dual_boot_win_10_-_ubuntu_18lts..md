---
title: "unable to install dual boot win 10 - ubuntu 18lts. install crashes."
date: 2019-11-02
forum: Installation &amp; Upgrades
---

### Post by y7cats on 2019-11-02
trying to install ubuntu 18lts on a Lenovo ideapad 320 with win 10 as a dual boot install. from both verified cd or usb. 
all goes well till drive file allocation window opens. when I ok preselected choices I get a "unknown error report install failed" and the install fails.
  NOTE: I have a 1terabyt drive but the preselected files allocation sizes are about 16 for win and 10 for ubuntu, doesn't sound right to me. 
I should have saved a copy of the report but I will the next time I try so I can submit it to the forum for revue. 
thank you for any help on this. frank

---

### Post by yancek on 2019-11-02
> I have a 1terabyt drive but the preselected files allocation sizes are about 16 for win and 10 for ubuntu, 

16 and 10 what?  Terabytes?  When you are in the Installation Type window on the Ubuntu installer, are you able to see the windows partitions as well as the unallocated space on which you intend to install Ubuntu?  Is your windows 10 install a standard EFI install?  Ubuntu has a page detailing installing Ubuntu with windows 10, see the link below and read through it before trying again.  Post back if you have questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2019-11-03
Also understand that Win10 will be Hibernated -- by default!  That means the Linux installer is going to have problems seeing it, as it will not be able to mount the volumes properly.

Unless you have already disabled FastStartup in Win10, you need to do that BEFORE attempting a Linux install -- or you risk corrupting the Win10 filesystem.

Win10 has enabled a new hibernation process known as Fast Startup -- which is enabled BY DEFAULT.  
 
This is different from Fast Boot, which is a BIOS/UEFI option.  
 
Fast Startup is supposed to dramatically speed up the booting process, but in some PCs, it actually slows it down or causes it to hang.  It's also a new form of hibernation known as hybrid sleep -- and this causes battery drain to maintain the state of the PC while turned off.
 
Disabling Fast Startup might fix the booting problem.
 
There are two ways to disable FastStartup in Win10: (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

