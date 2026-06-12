---
title: "Inspiron 1100 low graphics res 11.04"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by AllanKu on 2011-05-25
Dell Inspiron 1100 Intel 845 gpu
Running 10.10 very well, 1024 x 768 video

11.04 Live CD has 1024 x 768 grahpics
11.04 install has 640 x 480

I noticed the following in Xlog which seems to be related to video

From live CD log
39.817] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.817] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    39.817] (II) FBDEV(0): checking modes against framebuffer device...
[    39.817] (II) FBDEV(0): checking modes against monitor...
[    39.817] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    39.817] (**) FBDEV(0):  Built-in mode "current"
[    39.817] (==) FBDEV(0): DPI set to (96, 96)

From installed log
 (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.113] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    22.113] (II) FBDEV(0): checking modes against framebuffer device...
[    22.113] (II) FBDEV(0): checking modes against monitor...
[    22.113] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    22.113] (**) FBDEV(0):  Built-in mode "current"

Other than the references to video memory and virtual size, the logs seem to be identical.

Is this video memory sensed wrong in the installed version?
Is this the reason for the wrong monitor resolution?
Should I create a custom xorg.conf file to fix the resolution problem or is there another way?

The current 10.10 xorg log is the same as the one for the live CD.

I have two drives and am switching them out to test install things on this old laptop

Allan

---

### Post by betterhands on 2011-06-15
i had an Inspiron 1100 lying around that i just installed 11.04 on last night.  same resolution problem.  Monitor is listed as 'unknown'.  haven't had time to tinker with it much after installing last night, but if i find a resolution that works for me i'll post it here.  

saw this old post...haven't had a chance to try any of the advice, and not sure if it's just as valid for 11.04.  [http://ubuntuforums.org/showthread.php?t=190022](http://ubuntuforums.org/showthread.php?t=190022)

---

### Post by SirWeazel on 2011-07-05
Open up Ubuntu Software Center, search for the "startup-manager" and install this application.  Find the application after it is installed and run it. I think it will be system-administration-startupmanager, but don't quote me.

Run the app, change display resolution to 1024x768, color depth 24 bits. Close with the "x" and restart.  Everything should be good to go. (It is a little difficult doing this in the small square of a display you will have, but it will work)

An alternative i think would be to edit grub i think, but i'm not sure off hand. This is the graphical way i know.

Note: I don't think "suspend" works correctly with the display. It shuts off the display and doesn't turn it on upon resume. So i removed the option to suspend. (gksudo gedit  /usr/share/polkit-1/actions/org.freedesktop.upower.policy) and change <allow_active>yes</allow_active> to <allow_active>no</allow_active> under the suspend to remove this feature, or under the hibernate feature if you want to remove that also)  basically change "yes" to "no". The hibernate feature works for me. 

Hope this helps.

---

### Post by DebuRoba on 2011-08-06
> **SirWeazel said:**
> Open up Ubuntu Software Center, search for the "startup-manager" and install this application.  Find the application after it is installed and run it. I think it will be system-administration-startupmanager, but don't quote me.

Run the app, change display resolution to 1024x768, color depth 24 bits. Close with the "x" and restart.  Everything should be good to go. (It is a little difficult doing this in the small square of a display you will have, but it will work)

An alternative i think would be to edit grub i think, but i'm not sure off hand. This is the graphical way i know.

Note: I don't think "suspend" works correctly with the display. It shuts off the display and doesn't turn it on upon resume. So i removed the option to suspend. (gksudo gedit  /usr/share/polkit-1/actions/org.freedesktop.upower.policy) and change <allow_active>yes</allow_active> to <allow_active>no</allow_active> under the suspend to remove this feature, or under the hibernate feature if you want to remove that also)  basically change "yes" to "no". The hibernate feature works for me. 

Hope this helps.

Thank you SirWeazel, that worked perfectly.

---

### Post by SirWeazel on 2011-08-07
Glad i could help.  I also forgot to mention that you should go into the power settings and make sure you don't have suspend selected. The turn off monitor feature works correctly though.

On another topic, but i figured i would let you know, i run unity 2d (the daily build) on this laptop with out a problem.  Everything has been working good.

---

### Post by candtalan on 2011-12-24
> **SirWeazel said:**
> Open up Ubuntu Software Center, search for the "startup-manager" and install this application.  Find the application after it is installed and run it. I think it will be system-administration-startupmanager, but don't quote me.

Run the app, change display resolution to 1024x768, color depth 24 bits. Close with the "x" and restart.  Everything should be good to go. (It is a little difficult doing this in the small square of a display you will have, but it will work)

An alternative i think would be to edit grub i think, but i'm not sure off hand. This is the graphical way i know.

Note: I don't think "suspend" works correctly with the display. It shuts off the display and doesn't turn it on upon resume. So i removed the option to suspend. (gksudo gedit  /usr/share/polkit-1/actions/org.freedesktop.upower.policy) and change <allow_active>yes</allow_active> to <allow_active>no</allow_active> under the suspend to remove this feature, or under the hibernate feature if you want to remove that also)  basically change "yes" to "no". The hibernate feature works for me. 
Hope this helps.

Thanks for this, works well! (Using Lubuntu 11.10)

edit:
forgot to mention I am having to use a modified boot script to include
i915.modeset=1
 before I see any display 
similar:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[http://ubuntuforums.org/showthread.php?t=1531644](http://ubuntuforums.org/showthread.php?t=1531644)

edit2:
I noticed that after using update manager to set resolution to 1024x768 then the boot script included the parameter
vga=792

---

### Post by SirWeazel on 2011-12-24
Glad it help, and i think your information will probably help me. I haven't put 11.10 on it yet, but was going to. I'll post back here how my 11.10 install goes.

---

