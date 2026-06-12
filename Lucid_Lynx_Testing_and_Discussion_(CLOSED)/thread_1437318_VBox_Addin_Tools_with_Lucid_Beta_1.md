---
title: "VBox Addin Tools with Lucid Beta 1"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by samalex on 2010-03-23
Hi...  I installed Lucid Beta 1 on VirtualBox 3.1.4 running on Ubuntu 9.04 Desktop, and after Lucid Beta 1 is installed and after the VBox Add-in tools are ran as root then reboot, it says it's running in low graphics mode.  Nothing I do will get it past 800x600 or will enable the VBox addins for seamless use.

My concern is when installing the VBox addins it mentions needing to reboot so HAL can pick-up the changes, but HAL has been removed.  Does this mean the VBox addins will no longer work?

Thanks for any suggestions --

Sam

---

### Post by andrew.46 on 2010-03-23
Hi samalex,

I can certainly confirm this problem with an up to date Lucid installation as guest of Virtualbox 3.1.4_OSE. I have tried various fixes proposed on these forums and the virtualbox forums with no success...

Andrew

---

### Post by Ohrer on 2010-03-23
Hi I did install 10.04 on a virtual machine, using Vrtualbox this evening.

I had the same problem about the 'low graphic mode'. After installing the Guest addition **Devices->Install Guest Additions**& run ** /media/cdrom/VBoxLinuxAdditions.run **(look inside the folder for the right file) you have to edit **/etc/X11/xorg.conf**to look like this:

```

Section "Device"
   Identifier   "Configured Video Device"
   Driver	   "vboxvideo"
EndSection

Section "Screen"
   Identifier    "Default Screen"
   Device    "VirtualBox graphics card"
   Monitor   	"Generic Monitor"
   DefaultDepth   	24
   SubSection "Display"
     Depth    24
     Modes     	"1024x768"
   EndSubSection
EndSection

```

Sorry for my low level English.

---

### Post by andrew.46 on 2010-03-24
Hi,

Fix is on this thread:

[http://ubuntuforums.org/showthread.php?t=1435210](http://ubuntuforums.org/showthread.php?t=1435210)

Andrew

---

### Post by samalex on 2010-03-24
Andrew --

Awesome!  Thanks.  I'll try this out tonight when I get home.

Take care,

Sam

---

