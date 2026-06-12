---
title: "Ubuntu 10.04 - Virtualbox - Full Screen"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by HarvMan on 2010-05-03
Hi, I have successfully used the latest version of Virtualbox on Windows XP (SP3) for a number of weeks to run Ubuntu 9.10 and Vista Ultimate SP2. Today I upgraded Ubuntu to 10.04 LTS. The problem is that I can no longer get a full screen to display (Rt Ctrl-F). I have reinstalled the Guest Additions, but still no improvement.
 
My Dell 9150 computer uses ATI Radeon X300/X550/X1050 display adapter. But all has been functioning properly prior to the upgrade today. The VM for Vista Ulimate runs fine.
 
Any ideas?

---

### Post by tobey1 on 2010-05-03
I have the same issue.  All is fine until I install the VBAdditions.:confused:

---

### Post by HarvMan on 2010-05-10
Hi, after further research I found this post #4: [http://ubuntuforums.org/showthread.php?t=1153853](http://ubuntuforums.org/showthread.php?t=1153853)

Essentially, I ran the following to install Guest Additions and the full  screen option is now functional.
I have never done this before ... previously only used VirtualBox  Devices > Install Guest Additions...
(the media was already mounted for VBOXADDITIONS_3.1.7_59409)

user@ubuntu:~$ sudo /media/cdrom0/VBoxLinuxAdditions-x86.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 3.1.7 Guest Additions for Linux.........
VirtualBox Guest Additions installer
Removing installed version of VirtualBox Guest Additions...
tar: Record size = 8 blocks
Building the VirtualBox Guest Additions kernel modules
Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
Starting the VirtualBox Guest Additions ...done.
Installing the Window System drivers
Installing experimental X.Org Server 1.7 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just  restart
the guest system) to enable the Guest Additions.
Installing graphics libraries and desktop services components ...done.

---

