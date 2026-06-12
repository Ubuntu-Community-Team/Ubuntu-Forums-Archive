---
title: "Compiz in Karmic - How To?"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-07-15
Hey!

I'm curious how to get compiz to stop overcompositing. It's been a standard bug for me since Intrepid and I'd like to stamp it out in Karmic. Does anyone know how to get compiz working with the window titles, etc. working? If anyone doesn't know what I mean, just ask. I doubt it's a problem with my graphics card since it works in Hardy.

Thank you!

---

### Post by jocko on 2009-07-15
> **iaskedalice09 said:**
> Hey!

I'm curious how to get compiz to stop overcompositing. It's been a standard bug for me since Intrepid and I'd like to stamp it out in Karmic. Does anyone know how to get compiz working with the window titles, etc. working? If anyone doesn't know what I mean, just ask. I doubt it's a problem with my graphics card since it works in Hardy.

Thank you!
You would probably get help if you could describe your problem. compiz works fine here...

---

### Post by durand on 2009-07-15
And here. Maybe post a screenshot?

---

### Post by iaskedalice09 on 2009-07-16
Sure. Here's a screencap when I try and run compiz (by typing compiz --replace in ALT + F2). It crashed firefox-3.5

Here is info about my graphics card:
```

direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

I've also attached the output of glxinfo

---

### Post by iaskedalice09 on 2009-07-16
Also when I try and turn effects on via gnome-appearance-properties, it says Desktop effects could not be enabled.

---

### Post by taavikko on 2009-07-16
> **iaskedalice09 said:**
> Also when I try and turn effects on via gnome-appearance-properties, it says Desktop effects could not be enabled.

What's the pciid of the VGA
```
lspci -nn | grep VGA
```

It might be blacklisted...

---

### Post by iaskedalice09 on 2009-07-16
It doesn't look like it's blacklisted.

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

```

without code
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

---

### Post by taavikko on 2009-07-16
Yep, seems to be removed from the blacklist,
What does compiz complains about when started via terminal?
```
compiz --replace &
```

(If failing to fallback to metacity, use "metacity --replace &" (eg. window titles fail to show up)

---

### Post by iaskedalice09 on 2009-07-16
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:62: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:63: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:282: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

```

non-code
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:62: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:63: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/tom/.themes/Human Skin/gtk-2.0/gtkrc:282: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

---

### Post by psyke83 on 2009-07-16
> **iaskedalice09 said:**
> Hey!

I'm curious how to get compiz to stop overcompositing. It's been a standard bug for me since Intrepid and I'd like to stamp it out in Karmic. Does anyone know how to get compiz working with the window titles, etc. working? If anyone doesn't know what I mean, just ask. I doubt it's a problem with my graphics card since it works in Hardy.

Thank you!

If you can't see the window decorations with compiz, try:
```
$ gtk-window-decorator --replace &
```

Also try to revert to the default theme (with no customizations).

---

### Post by iaskedalice09 on 2009-07-16
compiz --replace with $ gtk-window-decorator --replace & works wonderfully. How do I make it default (i.e., if compiz runs, so does gtk-window-decorator)?

---

### Post by iaskedalice09 on 2009-07-16
I stand corrected. window decorations are still not on terminal but on everything else.

---

### Post by psyke83 on 2009-07-16
> **iaskedalice09 said:**
> I stand corrected. window decorations are still not on terminal but on everything else.

You're getting confused due to a slight bug when the window manager switches - the decoration of the gnome-terminal window is hidden under the top panel.

Hold the alt key and left-click anywhere in the terminal, and drag the window down. It happens to everyone.

---

### Post by psyke83 on 2009-07-16
> **iaskedalice09 said:**
> compiz --replace with $ gtk-window-decorator --replace & works wonderfully. How do I make it default (i.e., if compiz runs, so does gtk-window-decorator)?

It shouldn't be necessary to do this. I suspect that your user configuration is corrupt - try to create a new user and see if the problem happens there.

---

