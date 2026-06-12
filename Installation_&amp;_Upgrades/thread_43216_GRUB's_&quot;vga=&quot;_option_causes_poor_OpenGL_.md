---
title: "GRUB's &quot;vga=&quot; option causes poor OpenGL performance"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by NeoChaosX on 2005-06-21
Okay, I dunno where to go with this, so I'll just try to explain as best I can.

I'm sure quite a few users have found [this thread](http://www.ubuntuforums.org/showthread.php?t=41709) that adds boot splashes to Ubuntu. However, one of the steps I have to doto use the program gives me a problem I do not know how to fix.

When I edit my GRUB menu.lst and add the "vga=792" option to my default boot, I noticed when I'm booted into Linux, OpenGL performance is dragged *way* down. Before I added the option to GRUB, I had a glxgears score of about 960~ fps. When I have the "vga=" option enabled, it averages about 200fps. I've got a Mobility Radeon 7500 with 32 MB of video memory, and am running DRI drivers for the device. I've tried removing the splashy program, reverting to older drivers, and even installing the fglrx drivers. THe only thing that fixed the problem was removing the "vga=" option from GRUB. When I brought this up in the thread, the few people who commented said they suffered no reduction in performance. I find it strange this bug is only happening to me.
 
So, does anyone know why the "vga=" option is such a drag on performance? Is it just me, or are there other people who also have the same problems with it enabled?

---

