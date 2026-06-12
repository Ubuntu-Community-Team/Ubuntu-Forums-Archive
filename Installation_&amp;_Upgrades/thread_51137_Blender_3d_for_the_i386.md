---
title: "Blender 3d for the i386?"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by OneSeventeen on 2005-07-22
I just downloaded and installed Hoary 5.04 and I finally got openGL to work on my ATI graphics card, so now I'm up for some 3d rendering.

When browsing the package manager, I can't find blender3d anywhere, yet on my amd64 ubuntu machine, blender3d was listed under "graphics".

Any ideas as to why I can't see this?  should I be using a command line tool to install it?  (apt-get install blender3d doesn't seem to work)

---

### Post by mcmuffy on 2005-07-24
I installed blender and it did indeed put an icon in the graphics menu.
If you have no menu entry though the program can be run by typing 'blender' into the run program option. Your other option is to use smeg to add a menu entry manually.

Hope this helps

EDIT : I actually ready your post this time, the file to search for in apt is blender not blender3d.

---

### Post by Irony on 2005-07-24
system > admin > synaptic > settings > repositories > add > tick everything and update > search (blender) > right click blender for install > apply

Then it should pop in the graphics section. It is however the 2.36 version. Note it is blender not blender3D.

---

### Post by OneSeventeen on 2005-07-25
Thank you both for the feedback!  This is a big help.  I unfortunately had to format the computer I was using because my replacement for said machine just came in.

I'll let you know how it goes, but I'm not holding my breath as I'm an unlucky owner of the ATI 200M mobile graphics chip, which so far has gotten me up to 300FPS in glxgears.  (But that's another thread... one that can be found [here](http://ubuntuforums.org/showthread.php?t=50459) in fact)

But, then again, I've heard hardware rendering only helps the design portion, not the rendering itself.

---

