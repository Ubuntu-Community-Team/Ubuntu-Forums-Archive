---
title: "Karmic Koala 9.10 - X / GDM fails with nVidia driver - Black Flicker then CLI"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eznet on 2009-10-25
So, I have been wrestling with this issue since upgrading to Karmic.  Install nVidia driver, reboot PC and no longer being able to start X / GDM  - CLI only.  The screen would flicker a dozen times or so, then would drop to the CLI.

After a dist-upgrade, and failing to get X to start, I decided to go with a fresh install of Karmic beta.  Unfortunately, this resulted in the same issue - no X session with nVidia drivers (which worked fine in 9.04).  The only way I could get back to the GUI was to uninstall the nVidia driver and remove the xorg.conf.

Each time I would install nVidia drivers and reboot, I would fail to get a GUI and would see this in my Xorg.0.log:

```

(II) Primary Device is: 
(EE) No devices detected.

Fatal server error:
no screens found

```

Now, I am up and running nVidia 64 Bit v190.42 drivers without issue.  What was the key? Adding 
```
Busid        "PCI:#:#:#"
``` 

to the DEVICE section of my xorg.conf.  Just had to run:

```

sudo lspci | grep VGA

```

to get the Busid - note: this will return something along the lines of 1:0.0, which would be 1:0:0

Yup.  That was it for me... I don't know why this wasn't added by default, as I have NEVER had to do this manually in the past, but it is needed for me now for some odd reason.  Note:  I have tried all repo drivers as well as all 180+ nVidia provided packages and this never works out of the box for me in Karmic - I must add this line or I will be greeted with a flickering screen as X tries to start, before being dumped to the CLI.

Props to this thread for tipping me off: [http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start](http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start)

Summary:

```

>sudo apt-get install nvidia-glx-185 (or whatever you want)

>sudo lspci | grep VGA
*Above will give you your Busid*

>sudo nano /etc/X11/xorg.conf
*Add your Busid to the Device section of your xorg.conf*

>sudo reboot now

```

I hope this helps someone else.

If anyone has any ideas on why the PCI line isn't making it to xorg.conf, please toss me a bone!

-Matt

---

### Post by shulegaa on 2009-10-26
I've struggled for hours with this very same problem with the Ubuntu 9.04 to 9.10 (distribution) upgrade.  Post upgrade, the X server will not start.  It flickers some text on the screen and then drops back to the Linux command line.  Talk about trashing your desktop!   Thank goodness Karmic Koala is still only a release candidate!

 If anyone thinks it might be relevant, I happen to have a custom built desktop rig using the ASUS P5Q PRO motherboard (w/Intel Q9950 quad core) and dual STI Radeon HD 4850 (RV770) video cards (in SLI cfg).   

For me as well, everything worked great under Ubuntu 9.04.  After the 9.10 upgrade, and as the original poster suggests, I too had to add the following line to my /etc/X11/xorg.conf file ... via a command line invocation of old-school, 'character' mode emacs!:

   ```
Busid      "PCI:01:00:00"
```As suggested by the main post, this must appear in the xorg.conf "Device" section:

```

Section "Device"
           Identifier       "Configured Video Device" 
           Busid                  "PCI:01:00:00"
 EndSection

```Of course, my results from "sudo lspci | grep VGA" looked something like this:

```
01:00.0 VGA compatible controller:  ATI Technologies, Inc. RV770 [Radeon HD 4850]
02:00.0 VGA compatible controller:  ATI Technologies, Inc. RV770 [Radeon HD 4850]
```I have no idea if both video cards are getting exercised via SLI ... or if Linux is exercising just one video card ... but when I'm running Linux it doesn't much matter for me. ;-)

---

