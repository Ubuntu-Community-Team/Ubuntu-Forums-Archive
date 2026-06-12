---
title: "Very frustrated with 7.04 installation."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by MarkSparks on 2007-08-17
My system specs :

 	 GIGABYTE GA-M55SLI-S4 Socket AM2 NVIDIA nForce4 SLI ATX AMD Motherboard - Retail
 	 G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop
        EVGA 320-P2-N811-AR GeForce 8800GTS 320MB 320-bit GDDR3 PCI Express x16 HDCP Ready


Well, I can get the live CD to work by hitting F4 and selecting a larger resolution. It can come up with video, and I can work around stuff, even do the install almost to completion. 

At the end of the installation when it asks to remove the installation media and hit <Enter>, I eject the DVD and....nothing. Non-responsive. I did a MD5 check of the installation media and it passed. 

So, I'll use the ACPI function of press and hold down the power switch for 5 seconds for an un-graceful power down. 

When it starts back up, I can get to the GRUB loader and select the boot options, but if I choose anything other than text mode command prompt (non graphical) it goes to a black screen and there's no HDD activity. I tried typing in the username and password, thinking that it was sitting at the login prompt, but it's honestly unresponsive in any way shape or form. 

I reconfigured xserver and forced it to use 1600x1200 or 1024x768 as the only resolutions, but nothing, still a blank screen. 

Any suggestions? I can get to the user prompt, so perhaps I was thinking of doing a command line install of a new video driver, but I'm out of options here. 

Please help!

Mark.

---

### Post by Pumalite on 2007-08-17
When you reconfigured the xserver, did you choose 'vesa' as your driver?

---

### Post by dabl on 2007-08-17
Maybe this will help a little: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by MarkSparks on 2007-08-17
On the first installation, I did use VESA as the driver. I then did a reconfig again and tried the nv driver, neither gave me a graphical interface. 

This has been a multiple week event. The things I tried based off video reconfigs :

VESA driver 
1600x1200       1024x768     800x600
1600x1200       1024x768
1600x1200 (only, I tried to force it to the higher resolution)

NV driver
1600x1200       1024x768     800x600
1600x1200       1024x768
1600x1200 (only, I tried to force it to the higher resolution)

---

### Post by Pumalite on 2007-08-17
It might help to go to your monitor manual to check horiz and vert refresh rates as well as frequency and apply them when reconfiguring your graphics.

---

### Post by dabl on 2007-08-17
> **MarkSparks said:**
>  if I choose anything other than text mode command prompt (non graphical) it goes to a black screen and there's no HDD activity. I tried typing in the username and password, thinking that it was sitting at the login prompt, but it's honestly unresponsive in any way shape or form. 

Try Alt-F1, and if that doesn't work, Ctrl-Alt-F1, and see if it switches to a console, where you can log in in text mode.

> 
Any suggestions? I can get to the user prompt, so perhaps I was thinking of doing a command line install of a new video driver, but I'm out of options here. 

That's not a bad idea.  When in text mode, have you tried ```
sudo apt-get install nvidia-glx-new
```?

If it appears to install the package, you can start the xserver with ```
startx
``` and see if you've got an Nvidia driver.  :)

---

