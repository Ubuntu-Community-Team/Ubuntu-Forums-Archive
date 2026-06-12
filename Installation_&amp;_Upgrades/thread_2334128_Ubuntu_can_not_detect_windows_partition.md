---
title: "Ubuntu can not detect windows partition"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by deudingdude on 2016-08-16
Hello i know there has been a thread like this already but no matter where i searched i could not find a solution to my problem
Soooo...
i am running windows 10 and i would like to dual boot xubuntu 16.04 .
BUUT it can not detect that i have windows installed, and even if it does it does not in the installation , example:
os-prober has no results 
WINOSDATA=true os-prober  tells me that it detects a windows partition
so then i type
WINOSDATA=true ubiquity <--- or something like that i don't quite remember
if any of you guys can help me please do, i also had an idea:
what if i installed xubuntu on a seperate partition and then added a grub entry for windows?

---

### Post by ubfan1 on 2016-08-16
From the Windows disk manager, do the partitions have a type "dynamic" or "basic".  Dynamic partitions are not seen by Ubuntu.  Search around for "dynamic partition conversion to basic", it's pretty involved I think.

---

### Post by yancek on 2016-08-16
If your windows 10 was pre-installed, it is almost certainly using UEFI so you need to install Xubuntu UEFI.  Instructions on that at the site below:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> what if i installed xubuntu on a seperate partition and then added a grub entry for windows? 		

Installing on a separate partition is necessary.  If you install xubuntu on the same partition as windows you will overwrite windows.

---

### Post by deudingdude on 2016-08-17
They are all basic

i didn't come preinstalled, but i think it is uefi still

it detects the windows partition but it doesn't detect that i have windows installed on it , soo that means that when i install it it will probably not appear in grub, which would be a problem for me since i do want to dual boot

---

### Post by yancek on 2016-08-17
> it detects the windows partition but it doesn't detect that i have windows installed on it

Yu'll need to explain what you mean by that.  How far do you get in the attempt to install?

You should be able to enter the BIOS and check the settings to determine if UEFI is on/enabled.  If it is, then install Xubuntu UEFI.

---

### Post by Mark Phelps on 2016-08-17
A Win10 PC will come with FastStartup enabled by default.  This is a new form of hibernation in which the Windows filesystem volumes remain mounted even when Windows is not running.  That will prevent the Linux installer from mounting them.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

