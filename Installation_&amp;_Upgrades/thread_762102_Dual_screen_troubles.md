---
title: "Dual screen troubles"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by nachte on 2008-04-21
Hi all,

I've just installed the beta for 8.04, to once more see the problems that drove me away from 7.04 & 7.10. I can't get dual screen working on it. The machine is an amd x64, using a radeon 1950 pro.

After the upgrade i got the popup stating the message about the proprietary driver, which i enabled.. reboot, do some searching to find the catalyst tool.. and discover that once again.. it doesn't work properly.

My question: is there a guide somewhere that explains how to set up a dual screen machine, for ATI, on amd x64, whith both screens in their native resolutions?

thanks in advance,
kristof

---

### Post by Pumalite on 2008-04-21
This might help:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by nachte on 2008-04-22
Did not help.. it seems that on the login screen my first monitor is using the correct resolution, but once logged in.. back to the lower resolution.

i've added some information below, maybe someone can see whats wrong by looking at this??

driver seems to be ok?
kristof@Arakis:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7412 Release


The bits i think are needed from xorg.conf 
Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "DesktopSetup" "horizontal"
        Option      "Capabilities" "0x00000800"
        Option      "PairModes" "1680x1050+1280x1024"
        Option      "EnableMonitor" "tmds1,tmds2i"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
EndSection

any ideas anyone?

---

### Post by sterpstra on 2008-04-23
I've got the [seemingly] same issue.  I have a Radeon 3650 with HDMI and DVI outputs.  I can see both screens when I have them plugged in but I can't get anything but clone mode to work.  That's basically a useless function.  

My DVI is currently plugged into my Dell 2408 and it works fine with the larger resolution (with the exception of what appears to be aliasing effects within Google Earth)...  Anyway, plug the HDMI back in and I'm back to the same issue.  Only the clone option exists.

Is it just me or does ATI just not seem to support Linux very well?

---

### Post by moon2js on 2008-04-25
I have the same nothing-but-cloning problem with an older Radeon that has a DVI and VGA port (each with a monitor). Never have gotten this working in Ubuntu, and I was hoping Hardy would have resolved this.

---

### Post by RobbanC on 2008-04-25
Same here. :( 
I just installed 8.04 and only one of my monitors is recognized. I tried to manually edit xorg.conf for two screens (according to this: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) ) but that just ended up in a fail-safe, lo-res startup with still just one recognized monitor.

I have a ATI Radeon X1300 with one VGA- and one analogue-DVI monitor plugged in.

It would be great if someone could help us ATI.ers out! [-o<

---

### Post by moon2js on 2008-04-25
If you're editing xorg.conf according to the directions in that wiki, be very careful about syntax. I had the low-res problem, but I had a lot of little syntax things wrong.

To my "Screen" Section, I added:

```
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         3840 1200
        EndSubSection

```

Notice how the Virtual size has a different syntax (no 'x' between the dimensions) than elsewhere.

So, I got the dual screen spanning, and I can mouse across screens. It shows the bird background spanned across the two desktops, too (not a complete copy on each screen).

But it won't let me have a nonactive window actually visible in both screens (which defeats the purpose of everything). If  Iclick on Firefox on screen1 and that makes the Firefox window active, but all the now inactive windows in screen2 disappear. In fact, the only way I can reactivate the inactive windows in the seemingly empty screen2 is to use the workspace switcher (which seems to be mapped wrong, as left/right desktops are opposite of the left/right screens).

I will keep troubleshooting, but advice/ideas are welcome. I think the screen switcher is interfering, acting as if I only have one screen, which explains why it hides nonactive desktops, but since I have two screens, I want both desktops to be active.

---

