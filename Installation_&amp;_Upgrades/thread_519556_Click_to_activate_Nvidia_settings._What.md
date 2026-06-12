---
title: "Click to activate Nvidia settings. What?"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by lancest on 2007-08-07
My new AMD 64 dual has and Nvidia 7300 video card. I put special adjustment settings in it that don't activate until I run the Nvidia utility after booting. Maybe the driver isn't loading although xorg shows 
'nvidia'?  My Philips CRT monitor is a year or two old it seems to wheeze once in a while. Probably the fault of the monitor right?

---

### Post by dabl on 2007-08-07
> **lancest said:**
> 
 I put special adjustment settings in it that don't activate until I run the Nvidia utility after booting.

Not sure I understand "special settings", but is this the way you want it to run?  If you want it to default to a certain resolution and refresh settings (and assuming you actually have the Nvidia driver installed) you can simply run ```
sudo nvidia-settings
``` from a console window, click "detect display", then set your resolution and refresh rates, then click the "Save to X Configuration File" button, and "save" in the little window that pops up.  Then restart the x server with Ctrl-Alt-Backspace and you should be good to to.

>  Maybe the driver isn't loading although xorg shows 
'nvidia'? 

Well, this brings up the other question -- are you really running the Nvidia driver. Right before you see the login screen, do you see a full-screen green and black Nvidia logo/splash?  If not, then you don't have the binary Nvidia driver installed, or at least not correctly.  If you think that is the problem, I would suggest that you download the Envy script installer from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the file "envy_0.9.7-0ubuntu6_all.deb" that is about halfway down the page.  Once it is installed, you will open your "System" menu and click "Envy" to install the Nvidia driver, or else in the console simply enter ```
sudo envy -t
```

HTH :)

---

