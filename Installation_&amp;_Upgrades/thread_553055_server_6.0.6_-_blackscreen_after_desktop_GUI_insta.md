---
title: "server 6.0.6 - blackscreen after desktop GUI install-HELP"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by rdelgar on 2007-09-17
I have installed the LAMP server 6.0.6 and get a command line login- all was well.
Then I loaded the desktop GUI, on reboot I got a black screen with a bit of burnt orange at the far right of the screen and NO GUI.  Looks like a video driver issue?????

Here is a more detailed version of the GUI install:
Ubuntu ver 6.0.6 LTS  server install  on web server    
Configured RAID 10 on a 3ware 9550SX contoller card attached to 4 SATAII 150gb hard drives in a SuperMIcro computer.
Booted from cd- Ubuntu ver 6.0.6 LTS  server and answered promted questions, english, america, user & password etc.
System booted to command line, entered user & password.
Wanted GUI desktop so I entered; sudo aptitude install ubuntu-desktop  to install the GUI desktop.
After lengthy download, Post fix dos window appeared, I selected “Internet mail”  and entered the domainname.com.
BSOD+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
then on reboot-  black screen with a bit of burnt orange on far right.

Help 
bobbyd
[email]robert@delgarbino.com[/email]

---

### Post by dixonp on 2007-09-17
Edit /etc/X11/xorg.conf, search for a section corresponding to your video card, example:

```

   Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6200?]"
        Driver          "nvidia"
        BusID           "PCI:7:0:0"
   EndSection
```

Replace the driver ("nvidia" in the above example) with "vesa". This is a generic video driver that pretty much always works (graphics performance won't be good, but I don't think it matters to you because this is a server). Then reboot, your GUI should work.

Give us more information about your graphics card and monitor (vga, dvi ?). And send us /var/log/Xorg.0.log.old right after you reboot (this log file will be deleted the 2nd time you reboot).

---

