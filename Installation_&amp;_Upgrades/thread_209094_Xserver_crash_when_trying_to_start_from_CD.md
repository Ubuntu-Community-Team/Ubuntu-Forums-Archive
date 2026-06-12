---
title: "Xserver crash when trying to start from CD"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by AdamBlack on 2006-07-04
This is my first attempt with linux and have run into a problem

When I choose the Start or install option after booting the disk it goes through all the loading but then the xserver crashes. These are the messages I get after the Orage Ubuntu loading screen:

Failed to start the X serve (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
I pick Yes

X Window System Version 7.0.0
Release Date December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build operating system: Linux ubuntu 2.6.15-23-amd64-generic #1 SMP
PREEMPT Tue May 23 12:45:47 UTC 2006 x86_64

Build Date: 16 March 2006
Before reporting problems ........ yadd yadda

Module Loader present
Markers: yadda yadda
(==) Log File: "/var/log/Xorg.0.log", 
(==) Using Config File: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal Server Error:
No screens found                                                 f"

I pick view detailed and looked for warnings and errors and at the bottom there is
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach 64 in slot 1:0:1 could not be detected!
(EE) No Devices Detected.
Fatal Server Error:
no screens found


So I assume that it has to do with my video card. I do have a PCI TV capture card in the computer that I don't really use, could that cause this?
Any suggestions?

System Specs:
Amd Athlon 64 3500+
1gb ram
Asus A8N-E motherboard
320 GB SATA Hard Drive
120 GB IDE Hard Drive
dvd burn
cd burn
ATI RADEON x800GT PCI-E video card

---

### Post by AdamBlack on 2006-07-04
nevermind I got it after searching through the forums for a while.

---

### Post by foots2015 on 2006-07-04
Hey i have the same problem how did you fix it?

---

### Post by Bunkai on 2006-07-05
[QUOTE=AdamBlack]nevermind I got it after searching through the forums for a while.[/QUOTE]

Where? I'm still searching for this answer.

---

### Post by /thomas on 2006-07-05
[QUOTE=Bunkai]Where? I'm still searching for this answer.[/QUOTE]

if you happen to have an ATI graphic card, chances are you'll find the solution by putting the model name as the search word, ie "x800". there is a thread about how to install ATI graphic cards.

---

### Post by foots2015 on 2006-07-05
*bump*

---

