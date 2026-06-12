---
title: "[SOLVED] Graohic Driver problem..."
date: 2008-07-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2008-07-31
I have a problem with my graphic card or something like that, I can't get compiz to run, but when try to rum compiz from terminal it is something with Xgl see the output:

ubuntu@ubuntu-desktop:~$ compiz --replace
_***Checking for Xgl: not present. ***_----(something there, am I right?)
 Detected PCI ID for VGA: 
Checking for texture_from_pixmap: 
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
***_Checking for Xgl: not present. _***----(something there, am I right?)
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

 anyone know how to fix this?

---

### Post by ibuclaw on 2008-07-31
[Give Compiz-Check a try.]("http://forlong.blogage.de/article/pages/Compiz-Check")
It will tell you
A) if your graphics card is supported.
B) if you are missing anything required to run compiz.

Regards
Iain

---

### Post by gjoellee on 2008-07-31
here is the output:
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   Unknown
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 476: [: 5308: binary operator expected
           [ OK ]

by the way...it worked fine in Hardy but hardy crashed, so I wen't over to Intrepid Ibex alpha3 which for me is actually more stable then Hardy as well as faster, and this is the only problem I have had

---

### Post by ibuclaw on 2008-07-31
> **gjoellee said:**
>  Checking for hardware/setup problems..../compiz-check: line 476: [: 5308: binary operator expected
           [ OK ]

hmm I see a null pointer :)

One minute, I'll just check out the script to see what you are missing...

[EDIT]
I've just had a look, and that line says 
> [ ! -z $METACITY_PID ]

What does this command output?
```
ps -o pid= -C metacity
```

Regards
Iain

---

### Post by ibuclaw on 2008-07-31
Anyhow, this is how I got nvidia to work on my intrepid box:
```
sudo apt-get install build-essential linux-kernel-headers nvidia-settings nvidia-177-kernel-source
```

Now drop down to run-level 1
```
sudo shutdown now
```
And choose "root terminal/console" in the menu.

Then type in
```
nvidia-xconfig
```
so NVIDIA configures itself for your hardware.

Then run:
```
nano /etc/X11/xorg.conf
```
and find the section:
```

Section "Files" 
    RgbPath        "/usr/X11R6/lib/X11/rgb"
EndSection

```
And comment it out, so it looks like this
```

#Section "Files" 
#    RgbPath        "/usr/X11R6/lib/X11/rgb"
#EndSection

```
Save and Quit.

Then type in **exit** to return to the menu and choose "continue with normal boot".

Regards
Iain

---

### Post by gjoellee on 2008-07-31
i'll try that now

---

### Post by overdrank on 2008-07-31
Moved :)

---

### Post by gjoellee on 2008-07-31
solved! Thanks a lot!

---

