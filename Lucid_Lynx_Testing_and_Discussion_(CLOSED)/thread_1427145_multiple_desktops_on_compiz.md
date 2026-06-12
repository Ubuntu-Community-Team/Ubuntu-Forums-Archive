---
title: "multiple desktops on compiz"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arjmage on 2010-03-11
Having a weird problem with the multiple desktops on compiz. I can't get the horizontal size (in the general options in the compiz manager) to stick at 4, or at any value for that matter. It always jumps back to 2. 

So that leaves me with only 2 desktops in my 'cube'.

I *can* increase the vertical size to 2, giving me 4 desktops -- but that doesn't behave the same way as in rotating a cube. I have to manually click the desktop in the chooser on the bottom right.

Any reasons why I can't increase the desktop size?

Here's the output from compiz-check:
> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [GeForce Go 7400] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Here's the output from compiz:
> compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


Any ideas on how to browbeat the slider to move away from 2!?

Bonus points for also telling me why this is happening -- since I moved to Lucid Lynx.

---

### Post by overdrank on 2010-03-11
Hi and I had to use preference on the workspaces on the panel to change to 4 desktop. 

Moved to Lucid Lynx Testing and Discussion

---

### Post by arjmage on 2010-03-13
A-ha! that's the trick. Increase it separately in the preferences of the panel in the corner of the screen.

The numbers there form the upper bound for the values Compiz can take. I'd have thought that it would be allowed to override system parameters as such, but oh well, that's another program design.

Thanks!

---

