---
title: "Compiz has stopped working"
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-02-02
After upgrading to 9.04 alpha 3, my compiz has stopped starting up on startup/working altogether. This is what I have done so far:

Running ```
compiz
``` using alt-F2. This makes my windows dissapear and my screen flicker, before my windows come back as normal.

Then I have tried to enable visual effects under Appearance. I click on either normal or extra, and I get a bar that says "Looking for drivers", before I get the same as I did after running compiz, and a message box saying that effects couldn't be enabled.

I have no idea what to do, and I know I have not given anywhere near enough information here. The trouble is I don't know what commands to output etc. Any help telling me what to output would be great.

David

---

### Post by Kevbert on 2009-02-02
What video adapter/driver are you using ?

---

### Post by Tomatz on 2009-02-02
Run the command:

```
compiz --replace
```

Then post the output here ;)

---

### Post by jfernyhough on 2009-02-02
* in a terminal, not just using ALT-F2

;)

---

### Post by jocko on 2009-02-02
I think I just had the same problem (I don't remember the exact error compiz gave when I tried to run it from a terminal).
From my Xorg.0.log:```
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
```So, I reinstalled the nvidia driver (which gave me the warning "/usr/lib/xorg/modules/extensions/libglx.so is not a symlink"), and now everything works again.
Apparently some recent update had overwritten the link to nvidia's libglx.so.

Davideotape: Do you have an nvidia gfx card? In that case, to check if you have the same problem as me, run this in a terminal:```

grep EE /var/log/Xorg.0.log
```If you see the same error as me, just use synaptic to completely remove the nvidia driver and then reinstall it again (or run nvidia's installer again if you installed it manually). Maybe this could affect ati's fglrx drivers as well?

---

### Post by davideotape on 2009-02-03
> **Tomatz said:**
> Run the command:

```
compiz --replace
```

Then post the output here ;)

Here we go -

```
david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Property _NET_WM_NAME on window 0x3a0001f contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a0001f contained invalid UTF-8
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x7e specified for 0x3a0001f (OpenOffice).
Window manager warning: Property _NET_WM_NAME on window 0x3a00058 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00058 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a005a8 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a005a8 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a006ef contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a006ef contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00077 contained invalid UTF-8




```

I'm guessing that's not good, but I don't know what to do now :S

Oh, and I don't have a GFX. I have a nvidia 7500 LE.

---

### Post by Tomatz on 2009-02-03
> **davideotape said:**
> Here we go -

```
david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Property _NET_WM_NAME on window 0x3a0001f contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a0001f contained invalid UTF-8
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x7e specified for 0x3a0001f (OpenOffice).
Window manager warning: Property _NET_WM_NAME on window 0x3a00058 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00058 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a005a8 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a005a8 contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a006ef contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a006ef contained invalid UTF-8
Window manager warning: Property _NET_WM_NAME on window 0x3a00077 contained invalid UTF-8
Window manager warning: Property _NET_WM_ICON_NAME on window 0x3a00077 contained invalid UTF-8




```

I'm guessing that's not good, but I don't know what to do now :S

Oh, and I don't have a GFX. I have a nvidia 7500 LE.


The driver you updated/upgraded to is not in compiz's "whitelist". Basically either downgrade your GPU driver (manually) to a version whitelisted in compiz. Or wait for a compiz update, compatible with your driver (which i would recommend as jaunty is alpha).

;)

There is a way to get round the whitelist but i wouldn't recommend it and i cant find a link ATM. Just wait a while and it will be fixed.

---

### Post by davideotape on 2009-02-03
Cool, thanks for that. I think I'll wait.... I don't suppose I'm missing bouncy windows that much :P

Is there a way to see which driver I've got, and a way to check when it will be white listed by compiz?

---

### Post by Tomatz on 2009-02-03
Run **glxinfo** in a terminal to see what driver you are using. As for the whitelisted drivers, i would ask on the compiz forums (or a compiz guru here ;)). You can try to run compiz with the following command to see how well it runs with your driver (this will bypass the whitelist):

```
SKIP_CHECKS=yes compiz
```


You will probably end up with no window decorations. If so, enable the window decoration plugin in CCSM.

---

### Post by jocko on 2009-02-03
> **Tomatz said:**
> The driver you updated/upgraded to is not in compiz's "whitelist". Basically either downgrade your GPU driver (manually) to a version whitelisted in compiz. Or wait for a compiz update, compatible with your driver (which i would recommend as jaunty is alpha).

;)

There is a way to get round the whitelist but i wouldn't recommend it and i cant find a link ATM. Just wait a while and it will be fixed.

Nope. That's the error I got when I had the same problem. Check your /var/log/Xorg.0.log if there are any errors complaining about missing the glx module, if that's the problem it was introduced by the update to xserver-xorg-core that came on saturday (Jan 31), which contained a libglx.so file that replaced the symlink to nvidia's (or ati's) libglx.so (at least if those drivers were manually installed so that apt/dpkg wasn't aware of them).
Just uninstall the nvidia (or ati) video driver and reinstall it, that will replace the libglx.so with the correct symlink.

---

### Post by Tomatz on 2009-02-03
> **jocko said:**
> Nope. That's the error I got when I had the same problem. Check your /var/log/Xorg.0.log if there are any errors complaining about missing the glx module, if that's the problem it was introduced by the update to xserver-xorg-core that came on saturday (Jan 31), which contained a libglx.so file that replaced the symlink to nvidia's (or ati's) libglx.so (at least if those drivers were manually installed so that apt/dpkg wasn't aware of them).
Just uninstall the nvidia (or ati) video driver and reinstall it, that will replace the libglx.so with the correct symlink.

Good point, this could be the problem BUT i had exactly the same problem davideotape is having when i installed intrepid alpha. Hopefully one of us is correct anyway ;)

---

### Post by davideotape on 2009-02-09
> **jocko said:**
> Nope. That's the error I got when I had the same problem. Check your /var/log/Xorg.0.log if there are any errors complaining about missing the glx module,

I've attached my /var/log/Xorg.0.log, I don't have a clue what it is on about though :S.

---

### Post by jocko on 2009-02-09
> **davideotape said:**
> I've attached my /var/log/Xorg.0.log, I don't have a clue what it is on about though :S.
According to the log, you are using the open source (nv) driver. It does not support 3d acceleration, which is why you can't run compiz. Install the proprietary nvidia driver if you want to have 3d support.

---

### Post by caryb on 2009-02-09
I wonder if there is any common thread between compiz & kwin not working? I'm using the Nvidia 180.27 driver & it was working the 1st couple of days of the install.


Cary

---

### Post by davideotape on 2009-02-10
> **jocko said:**
> According to the log, you are using the open source (nv) driver. It does not support 3d acceleration, which is why you can't run compiz. Install the proprietary nvidia driver if you want to have 3d support.

Sorry to bother you, but how would I go about doing this?

---

### Post by Nixie Pixel on 2009-02-10
> **davideotape said:**
> Sorry to bother you, but how would I go about doing this?
First check System -> Administration -> Hardware Drivers
If it is available there, you can check enable and it should install itself for you.

---

### Post by Kevbert on 2009-02-10
Same problem here. It's strange but compiz works fine in Jaunty Ubuntu with driver 180.27, but in Kubuntu (with the same driver) it doesn't work. Compiz-check says it's OK, but if I run compiz in (Kubuntu) terminal I get the following output:
```
$ compiz
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

---

### Post by minisori on 2009-02-10
try compiz --replace

---

### Post by maciu on 2009-02-11
Kevbert, i had the same problem - get the newest driver from here ```
ftp://download.nvidia.com/XFree86/
``` dist-upgrade to newest kernel and start compilz with compiz --replace (for me emerald -- replace didnt work somehow)

---

### Post by maciu on 2009-02-11
> **davideotape said:**
> Sorry to bother you, but how would I go about doing this?

Try what Nixie Pixel suggested if that doesn't work try envyng - nice python script to install video drivers. As a last resort uninstall everything what apt-get installed for you and download the newest drivers from nvidias site, it will compile a nice new kernel module for you and the latest version -  180.29 is supposed to be stable driver ;)

Ps. or it may be as simple as changing the driver from "nv" to "nvidia" in Device section in your xorg.conf

---

### Post by Kevbert on 2009-02-11
Thanks for the suggestions.
```
compiz --replace
```
gives me virtually the same problems as
```
compiz
```
I'm using the latest kernel in Kubuntu. It seems very strange that I can run compiz without any problems in the latest Ubuntu Jauny kernel but not Kubuntu. Both are using the 180.27 driver.
If I change the xorg.conf driver to "nv", it was "nvidia", I get the screen offset suggesting I need the restricted driver to correct this.
Where do I run
```
sudo sh NVIDIA-Linux-x86_64-180.29-pkg2.run
```
from? I can't run it from Konsole or from the Recovery Mode prompt.

---

### Post by Nullack on 2009-02-11
How about sudo apt-get remove --purge compiz* and turf it from the install all together :) Compiz wont ever work right until a proper video architecture is written for it.

---

### Post by davideotape on 2009-02-11
I have good news and bad news.

First of all, compiz runs :D

However, running it produces this code:

```
david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Plugin 'core' has ABI version '20090207', expected ABI version '20080828'.

/usr/bin/compiz.real (ccp) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


```

and gets rid of the top bar of windows.

Anyone know whats going on?

---

### Post by Kevbert on 2009-02-11
It looks like a whole load of upgraded compiz files are due to come out any day now along with the nvidia 180.29 driver.

---

### Post by philinux on 2009-02-11
Just got the updates now, all fixed.

---

### Post by Kevbert on 2009-02-11
All the updates and compiz now works fine in Kubuntu.

---

### Post by n3had on 2009-02-12
I had the same issue reinstalled the official drivers 180.29 and compiz is running fine!!!

Thank you everyone for all the support! I am LOVING it in here!!

nehad

---

### Post by gwenn on 2009-02-12
I also had some problems running compiz, but now everything seems fixed.Compiz runs fine but when I loggin I must run it manually sudo compiz.What can I do to fix this issue? 
Thanks!

---

### Post by jocko on 2009-02-12
> **gwenn said:**
> I also had some problems running compiz, but now everything seems fixed.Compiz runs fine but when I loggin I must run it manually [COLOR=Red]sudo[/COLOR] compiz.What can I do to fix this issue? 
Thanks!
You could add it to your session (system-->settings-->sessions).
Use the command "compiz --replace" (and *don't use sudo*, you don't need root permissions to run compiz. Using sudo for things that don't require it is not very safe).

---

### Post by gwenn on 2009-02-12
instaled Compiz-fusion icon.Fixed!

---

### Post by gwenn on 2009-02-12
only compiz didn't work and even compiz --replace in session manager...Maybe because of the compiz settings.However thanks it works now.

---

