---
title: "update 1/18/13 Unity broken"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by jbeiter on 2013-01-18
Unity fails but X runs. The app bar doesn't show up, no taskbar, and I just see the backdrop icons.

---

### Post by zvacet on 2013-01-18
Try type in terminal

```
unity
```

---

### Post by jbeiter on 2013-01-18
ran "unity"

Lots of pain surrounding glx. I won't paste the whole output, there is a ton of repeating errors but hopefully these might give a hint at what is broken:

Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Starting plugin: resize
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: wall
compiz (core) - Error: Failed to start plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: animation
compiz (core) - Error: Failed to start plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Loading plugin: fade
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't availableX
lib:  extension "GLX" missing on display ":0.0"

a ton of repetition. Anything I can smack with apt-get to bounce it back into shape?

virtualbox claims the d3 acceleration is broken too, the resolutions are screwed up on the display manager and the screen is truncated.

This was a real turd of an update. I'm really hoping for some tips before I'm reduced to reinstalling this **** from scratch.

---

### Post by lisanels47 on 2013-01-18
This is running in a virtualbox?  If so, you can disable 3d support in the settings for the virtual machine.

Also, unity can be reset like this:

unity -reset

But it looks like your issues are with the graphics, so if you can re-install the guest tools, that might also help.

Verify everything actually updated with:
apt-get -f install

---

### Post by carvis on 2013-01-19
I ran into very similar problems after applying these updates.
In my case, however, I was running fglrx beta (12.11) and not in a VM.

After dropping to shell I was able to uninstall fglrx and everything started working fine. 
I then went to ATI and found they'd released a new version (13.1) on Jan16.
Of note, this new version includes full support for Xserver 1.13 and Ubuntu 12.10. I downloaded and applied that version and Unity is working again.


I'd also add that the '-reset' parameter is deprecated for unity  in 12.10.
Not sure if --reset-icons is a direct replacement, but either way it didn't help in my case; it just made me rebuild my toolbar when I did get it working.

Again, not sure if this will help the OP, considering the technical differences, but hope it helps someone.

Good hunting!

---

