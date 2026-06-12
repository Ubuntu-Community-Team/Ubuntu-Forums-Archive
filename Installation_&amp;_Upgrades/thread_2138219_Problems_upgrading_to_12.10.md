---
title: "Problems upgrading to 12.10"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by MHC on 2013-04-23
I have a 64 bit dual-boot system. I tried upgrading from 12.04 to 12.10 using the update manager. During the upgrade I got 2 error messages>

1. [I]Errors were encountered while processing initramfs-tools

Could not install 'initramfs-tools'. The upgrade will continue but the 'initramfs-tools' package may not be in a working state. Please consider submitting a bug report about it. 

subprocess installed post-installation script returned error exit status 1[/I]

2. [I]Error during commit
A problem occurred during the cleanup. installArchive() failed


[/I]The installation continued, then asked for a re-start. I did this, but soon got the message:
[I]The system is running in low-graphics mode.
Your screen, graphics card ([/I]ATI Radeon HD 4800 Series) *and input device settings could not be detected correctly. You will need to configure these yourself.*

I clicked OK then immediately got the screen:

[I]What would you like to do?
[LIST]
[*]Run in low-graphics mode 
[*]Reconfigure 
[*]Troubleshoot 
[*]Exit 
[/LIST]

[/I]This screen seemed to be dead. I could not move around it or accept the default with any keys or the mouse. I tried re-booting several times, always with the same result. 
How can I fix this and actually get into ubuntu?

---

### Post by grahammechanical on 2013-04-23
Do you get a Grub Menu? If so, select Advanced Options for Ubuntu and at the next screen select Recovery Mode. At the Recovery Mode screen select Resume. That may get you to a desktop where you can go to System Settings>Software Sources>Additional Drivers tab and experiment with the video drivers available. If the proprietary drivers are activated you could try the Nouveau open source driver. You may need to reboot.

If you get to a desktop without Unity, then right click the wallpaper and select Change Wallpaper. That will open System Settings and you can proceed from there.

Regards.

---

### Post by MHC on 2013-04-23
Thanks for your suggestions grahammechanical. Unfortunately I had previously tried going through Recovery Mode, with the same result. I even tried it again after your suggestion, except choosing "failsafe mode" instead of Resume. But I still got exactly the same thing. I am at my wits end, with ubuntu and all my work there now inaccessible.

---

### Post by MHC on 2013-04-24
What are my options? Can I reinstall Ubuntu from Windows?

---

