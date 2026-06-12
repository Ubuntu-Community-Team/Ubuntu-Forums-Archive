---
title: "how to install tablet"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by kiyoshi7 on 2011-10-13
hey i have a genius gpen 4500 and i wanna know how to install drivers and etc cause i want to reassign the buttons on the pen. i went to the terminal and wrote lsusb and it gave me this:

daniel@ubuntu:~$ lsusb
Bus 002 Device 004: ID 04e8:1f03 Samsung Electronics Co., Ltd 
Bus 002 Device 003: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 064e:2100 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

where can i get software for the tablet and how do i install it? sorry im still learning how to use the terminal so i dont know how to do this yet

---

### Post by Favux on 2011-10-14
Hi kiyoshi7,

You didn't say what release of Ubuntu you are using.  The UC-Logic tablets use the WizardPen driver.  You want to install DoctorMO's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)  Instructions for the tablet are on the WizardPen wiki:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by kiyoshi7 on 2011-10-14
ahh sorry im using ubuntu 11.04

---

### Post by Favux on 2011-10-14
Have you installed the driver from the PPA?

---

### Post by kiyoshi7 on 2011-10-16
i tried installing using the 2nd link u gave me and it keeps giving me this:

daniel@ubuntu:~$ sudo apt-get install xserver-xorg-input-wizardpen
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xserver-xorg-input-wizardpen


edit:

i tried skipping ahead and was able to get to the the part of downloading and installing the driver but  i get this:

daniel@ubuntu:~$ sudo apt-get install bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bzr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
daniel@ubuntu:~$ bzr branch lp:wizardpen
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 51 revision(s).        


i tied downloading the driver from the site [https://launchpad.net/wizardpen](https://launchpad.net/wizardpen) but i dont know what to do with it....

edit 2

ok i tired a lil more and was able to follow all the install steps with no problem but when i have to check the integrity it tells me the dir. doesnt exist here is the line im using:
ls /usr/lib/xorg/modules/input/wizardpen_drv.*

---

### Post by kiyoshi7 on 2011-10-16
never mind i figured it out

---

