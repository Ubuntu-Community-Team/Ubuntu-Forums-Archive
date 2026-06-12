---
title: "HOWTO FIx: VirtualBox OSE problem &amp; Inaccessible OS"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2008-01-16
I installed VirtualBox OSE (command line below) and tryed to added XP to my sharing folder and no go.  So, I restarted VirtualBox and i got this error.

**Error Box from VirtualBox when started Up
> Could not load the settings file '/home/MyUsername/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/MyUsername/.VirtualBox/VirtualBox.xml', line 40, column 159.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

What Should I do to fix this?



**Terminal Line from installing VirtualBox OSE
> MyUsername@MyUsername:~/Trash$ sudo mkdir VirtualBoxShare
[sudo] password for MyUsername:
MyUsername@MyUsername:~/Trash$ vboxmanage sharedfolder add "XP" -name "share" -hostpath /home/MyUsername/Trash/VirtualBoxShare/
The program 'vboxmanage' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: vboxmanage: command not found
MyUsername@MyUsername:~/Trash$ sudo apt-get install virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-ose-modules-2.6.22-14-generic
Recommended packages:
  virtualbox-ose-source
The following packages will be REMOVED:
  virtualbox
The following NEW packages will be installed:
  virtualbox-ose virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 2 newly installed, 1 to remove and 48 not upgraded.
Need to get 6012kB of archives.
After unpacking 17.6MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe virtualbox-ose-modules-2.6.22-14-generic 6 [317kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe virtualbox-ose 1.5.0-dfsg2-1ubuntu3 [5695kB]
Fetched 6012kB in 23s (259kB/s)                                                
(Reading database ... 103357 files and directories currently installed.)
Removing virtualbox ...
 * Stopping VirtualBox kernel module vboxdrv                                    
 * Cannot unload module vboxdrv.
Shutting down VirtualBox host networking...done.
Selecting previously deselected package virtualbox-ose-modules-2.6.22-14-generic.
(Reading database ... 102743 files and directories currently installed.)
Unpacking virtualbox-ose-modules-2.6.22-14-generic (from .../virtualbox-ose-modules-2.6.22-14-generic_6_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.0-dfsg2-1ubuntu3_i386.deb) ...
Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
Installing new version of config file /etc/init.d/vboxdrv ...
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...

MyUsername@MyUsername:~/Trash$ vboxmanage sharedfolder add "XP" -name "share" -hostpath /home/MyUsername/Trash/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] Failed to create the VirtualBox object!
[!] Primary RC  = 0x80004005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80004005
[!] Text        = Could not load the settings file '/home/MyUsername/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/MyUsername/.VirtualBox/VirtualBox.xml', line 40, column 159
[!] Component   = VirtualBox, Interface: IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
[!] Callee      = <NULL>, {00000000-0000-0000-0000-000000000000}
MyUsername@MyUsername:~/Trash$ 
MyUsername@MyUsername:~/Trash$ vboxmanage sharedfolder add "XP" -name "share" -/home/MyUsername/Trash/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] Failed to create the VirtualBox object!
[!] Primary RC  = 0x80004005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80004005
[!] Text        = Could not load the settings file '/home/MyUsername/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/MyUsername/.VirtualBox/VirtualBox.xml', line 40, column 159
[!] Component   = VirtualBox, Interface: IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
[!] Callee      = <NULL>, {00000000-0000-0000-0000-000000000000}
MyUsername@MyUsername:~/Trash$ vboxmanage sharedfolder add "XP" -name "share" -/home/MyUsername/Trash/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] Failed to create the VirtualBox object!
[!] Primary RC  = 0x80004005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80004005
[!] Text        = Could not load the settings file '/home/MyUsername/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/MyUsername/.VirtualBox/VirtualBox.xml', line 40, column 159
[!] Component   = VirtualBox, Interface: IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
[!] Callee      = <NULL>, {00000000-0000-0000-0000-000000000000}
MyUsername@MyUsername:~/Trash$ 


Next Error
I went to /home/USER_NAME/.VirtualBox/VirtualBox.xml
and
I removed this line (LogHistoryCount="3") from the file, but now every OS is inaccessible.

What should be my next step?


> Could not load the settings file '/home/MyUsername/.VirtualBox/Machines/OpenSUSE 10.3/OpenSUSE 10.3.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Unknown element 'PXEDebug'
Location: '/home/MyUsername/.VirtualBox/Machines/OpenSUSE 10.3/OpenSUSE 10.3.xml', line 33, column 36.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


**The FIX. Do the following....**
I just ended up removing VirtualBox and then reinstalling VirtualBox.  When my VirtualBox started up, there were all my OSs are ready in VirtualBox with no errors at all.


Troubleshooting:
Still get an inaccessible OS after reinstalling VirtualBox.  Most likely it's because you were messing around with .xml files for VirtualBox.
IE:
> I went to /home/USER_NAME/.VirtualBox/VirtualBox.xml
and
I removed this line (LogHistoryCount="3") from the file, but now every OS is inaccessible.

 - You probably were editing the 'VirtualBox.xml' or one of the OS's .xml file (mine is 'OpenSUSE 10.3.xml'). 
 - To fix this problem. Hopefully, you made a back up of the 'VirtualBox.xml' and Name_of_Your_OS.xml (MIne is 'OpenSUSE.xml'  'whatever OS you used in VirtualBox). 
 - Just replace the VirtualBox.xml and 'Name_of_Your_OS.xml' (mine is 'OpenSUSE 10.3.xml) with the files that you backed up before.
 - Replace them
 - And bam! Everything is fixed

Side Note:
VirtualBox.xml can be founded in /home/USER_Name/.VirtualBox/
Name_of_Your_OS.xml can be founded in /home/USER_Name/.VirtualBox/Machines/Name_of_Your_OS/Name_of_Your_OS.mxl
Mine was
/home/MyUsername/.VirtualBox/VirtualBox.xml
and
/home/MyUsername/.VirtualBox/Machines/OpenSUSE 10.3/OpenSUSE 10.3.xml

and of couse, my 'USER_Name' is 'MyUsername' just replace 'USER_Name' with your user name.

I hope this helped anyone.

Sugi

---

### Post by Sugi on 2008-01-17
I went to /home/USER_NAME/.VirtualBox/VirtualBox.xml
and
I removed this line (LogHistoryCount="3") from the file, but now every OS is inaccessible.

What should be my next step?


> Could not load the settings file '/home/LongPENIS/.VirtualBox/Machines/OpenSUSE 10.3/OpenSUSE 10.3.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Unknown element 'PXEDebug'
Location: '/home/LongPENIS/.VirtualBox/Machines/OpenSUSE 10.3/OpenSUSE 10.3.xml', line 33, column 36.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

---

### Post by Sugi on 2008-01-17
Side Note to my Problem:  I have tried installing another OS in the mean time and when I try to start that one up.  It shuts down and won't load up again. :-/


Anyone knows how to recovery my OSs?  Can't I at least save the information about each OS and reinstall everything like a recovery or something?

Thanks,
Sugi

---

### Post by Sugi on 2008-01-17
still broken :(

---

### Post by Sugi on 2008-01-17
This is my problem.

---

### Post by Sugi on 2008-01-19
anyone out there with the power to change my Thread title to
"[COLOR="Navy"]HOWTO FIx: VirtualBox OSE problem & Inaccessible OS[/COLOR]"

---

### Post by Vadi on 2008-02-04
I had the same error msg, but that was when I uninstalled non-oss virtualbox and got the oss one. Revertered back, and it worked just fine.

---

### Post by ma65p on 2008-06-19
Well, it has been a year but I found the solution.

1. Uninstall all virtualbox packages (synaptic, search for "virtualbox")
2. After the uninstallation, delete folder named ".VirtualBox" by open nautilus, View-> show hidden files, then delete the folder.
3. Reinstall VirtualBox through Synaptic again. You should be fine.

---

### Post by Victormd on 2008-06-19
Why not install the PUEL (Personal Use and Evaluation License) version? It's free plus you get USB support, currently not available under the OSE version. You can download it [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

