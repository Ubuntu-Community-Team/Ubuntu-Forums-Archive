---
title: "New install hangs on &quot;Install third-party software for graphics and WiFi hardware...&quot;"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by jub2 on 2016-06-02
Well, hang may not be the correct term, since the Quit button is active (highlights when I bring the spinning cursor over it). But it's taking forever. I've done installs where this was a pretty quick step. 

Is it an issue with the server that these drivers and software are being downloaded from?

---

### Post by grahammechanical on 2016-06-02
The third party software will include Microsoft's core fonts and we need to accept the Microsoft End User License Agreement (EULA) for the process to continue. Somewhere there should be a dialog box. It may be hidden behind the installer window. Move the installer window to one side and you may see the dialog containing the Microsoft EULA. click to accept or reject.

Regards.

---

### Post by Bucky Ball on 2016-06-02
Best to leave 'install third-party' and 'install updates during installation' unticked. Just install the OS, deal with that stuff later when you have a desktop and a better chance of fixing it. Installing third-party drivers during install can add a lot of guff you don't and won't need. 

Updates are easy to do once installed and better to select which third-party drivers you actually need once you have the machine up and running and you can see what's working and doesn't. 

(There is an app called 'Additional Drivers' in Ubuntu that should identify anything you need and offer the drivers required once you have the OS installed.)

---

### Post by jub2 on 2016-06-04
> **Bucky Ball said:**
> Best to leave 'install third-party' and 'install updates during installation' unticked. Just install the OS, deal with that stuff later when you have a desktop and a better chance of fixing it. Installing third-party drivers during install can add a lot of guff you don't and won't need. 

Updates are easy to do once installed and better to select which third-party drivers you actually need once you have the machine up and running and you can see what's working and doesn't. 

(There is an app called 'Additional Drivers' in Ubuntu that should identify anything you need and offer the drivers required once you have the OS installed.)
Thanks, good call.

---

### Post by gangadjinn on 2016-07-27
> **jub2 said:**
> Well, hang may not be the correct term, since the Quit button is active (highlights when I bring the spinning cursor over it). But it's taking forever. I've done installs where this was a pretty quick step. 

Is it an issue with the server that these drivers and software are being downloaded from?

I have this excact problem. BUT it happens whether or not I choose to install third party and updates... Just starts to load, and then nothing for hours. 

What have I tried:

1. Turning my BIOS/UEFI upside down to see if there is something wrong there... Can't find anything. No fastboot option, boot mode set to legacy support.

2. tried just ticking updates, or just ticking 3.rd party, or none of them... No difference...

---

### Post by howefield on 2016-07-27
> **jub2 said:**
> Is it an issue with the server that these drivers and software are being downloaded from?

Opening System Monitor will tell you if you have traffic coming through, ie the downloaded updates ect.

> **gangadjinn said:**
> I have this excact problem. BUT it happens whether or not I choose to install third party and updates... Just starts to load, and then nothing for hours. 

Could be nothing to do with the 3rd party stuff, could be having an issue getting to the partitioning stage, anything "unusual" about your disks ?

---

